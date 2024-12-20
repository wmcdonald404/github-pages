---
title: "Create a simple GitHub Pages blog post"
tags:
- github
- github-pages
---
## Overview
This post summarises a simple workflow to add new posts to an existing Github pages-based Jekyll formatted blog. See [Further Reading](#further-reading) for more on the initial setup of Github Pages and Jekyll.

## Background
[Github pages](https://pages.github.com/) can provide a simple, relatively cheap way to host some simple web content. Frequently this content is auto-generated from underlying [markdown](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax) in from a Git repository using [Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll).

## How-to
1. Set some common variables to reuse in subsequent steps.

    Set the current date & time, and the subject of the blog post:
    ```shell
    $ export BLOGDATE=$(date -I)
    $ export BLOGTITLE='Simple Github pages blog post'
    ```

2. Add the contents including any requisite [FrontMatter](https://jekyllrb.com/docs/front-matter/)

    Create the post file with an appropriately time-stamped name. Assuming our repository is checked out at `~/repos/github-pages/`, construct the FrontMatter from the environment variables:    
    ```shell
    $ cat >> ~/repos/github-pages/_posts/${BLOGDATE}-simple-pages-blog-post.md <<EOF
    ---
    title: "${BLOGTITLE}"
    ---
    EOF
    ```

    Edit the file and add the rest of the content:
    
    ```shell
    $ vim ~/repos/github-pages/_posts/${BLOGDATE}-simple-pages-blog-post.md
    ```

    Add the rest of the blog post after the FrontMatter using standard [Github markdown](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax). For example, [this blog post's markdown can be viewed here](https://github.com/wmcdonald404/github-pages/blob/main/_posts/2024-01-02-github-pages-simple-blog.md?plain=1) or [here in raw format](https://raw.githubusercontent.com/wmcdonald404/github-pages/refs/heads/main/_posts/2024-01-02-github-pages-simple-blog.md).

    

3. Verify `git status`, `git add` the new content, `git commit` the new post and `git push` to the remote repository.
    
    Check the current Git source control state:
    ```shell
    wmcdonald@fedora:~/repos/github-pages$ git status
    On branch main
    Your branch is up to date with 'origin/main'.

    Untracked files:
      (use "git add <file>..." to include in what will be committed)
            _posts/2024-01-02-simple-pages-blog-post.md

    no changes added to commit (use "git add" and/or "git commit -a")
    ```
    Add the new content in order to stage the new changes:
    ```shell
    wmcdonald@fedora:~/repos/github-pages$ git add _posts/
    ```
    Validate the new Git state:
    ```shell
    wmcdonald@fedora:~/repos/github-pages$ git status
    On branch main
    Your branch is up to date with 'origin/main'.

    Changes to be committed:
      (use "git restore --staged <file>..." to unstage)
            new file:   _posts/2024-01-02-simple-pages-blog-post.md
    ```
    Commit the new content:
    ```shell
    wmcdonald@fedora:~/repos/github-pages$ git commit -m '- Add new blog post describing simple workflow to add new post.'
    [main 0126586] - Add new blog post describing simple workflow to add new post.
    1 file changed, 64 insertions(+)
    create mode 100644 _posts/2024-01-02-simple-pages-blog-post.md
    ```
    Push to the remote to trigger a workflow:
    ```shell
    wmcdonald@fedora:~/repos/github-pages$ git status
    On branch main
    Your branch is ahead of 'origin/main' by 2 commits.
      (use "git push" to publish your local commits)

    nothing to commit, working tree clean

    wmcdonald@fedora:~/repos/github-pages$ git push
    Enumerating objects: 10, done.
    Counting objects: 100% (10/10), done.
    Delta compression using up to 8 threads
    Compressing objects: 100% (8/8), done.
    Writing objects: 100% (8/8), 1.79 KiB | 1.79 MiB/s, done.
    Total 8 (delta 3), reused 0 (delta 0), pack-reused 0
    remote: Resolving deltas: 100% (3/3), completed with 1 local object.
    To https://github.com/wmcdonald404/github-pages.git
      7609736..5dd04aa  main -> main
    ```

4. Check that the new post has been generated
    Verify that the new post is visible as a **Post** on your [Github page](https://wmcdonald404.github.io/github-pages/).

    You can have a look at the [Github Actions](https://github.com/wmcdonald404/github-pages/actions) pipeline run which, if the build ran successfully, will have auto-generated your new page update.

    Navigate to [your new post](https://wmcdonald404.github.io/github-pages/2024/01/02/simple-pages-blog-post.html) to verify its publication.

## Further reading
- [Github Pages skills template course (start here)](https://github.com/skills/github-pages)
- [Chad Baldwin's blog, a user-perspective on setting up Github pages with Jekyll](https://chadbaldwin.net/2021/03/14/how-to-build-a-sql-blog.html)
- [Tom Campbell's Everything Github Pages](https://tomcam.github.io/least-github-pages/)
