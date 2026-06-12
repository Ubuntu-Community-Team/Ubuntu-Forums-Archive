---
title: "man pages, HOWTOs, and HTML docs"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by anroy on 2009-09-19
Sometimes man pages refer to "HOWTO" documents and/or to HTML docs.  For example, I've quoted below a snippet from git's man page.

My question is: Are these HOWTOs and HTML docs also part of the package's installation on my hard drive, the way that man pages are?  If so, is there a standard way (command, etc.) by which to access them?

My question is not specifically about git, but about documentation of Linux/Unix packages in general.

Thanks.

> 
SEE ALSO
       gittutorial(7), gittutorial-2(7), Everyday Git[1], gitcvs-migration(7), gitglossary(7), gitcore-tutorial(7), gitcli(7), The Git User´s Manual[2]


GIT
       Part of the git(1) suite


NOTES
        1. Everyday Git
           everyday.html

        2. Git User’s Manual
           user-manual.html

        3. git concepts chapter of the user-manual
           user-manual.html#git-concepts

        4. howto
           howto-index.html

        5. GIT API documentation
           technical/api-index.html


---

### Post by Bachstelze on 2009-09-19
In this particular case (git), documentation is in a separate package (git-doc). After you install it, you will find the documentation in /usr/share/doc/git-doc. Since  it's HTML documentation, you can view it in your favourite web browser.

---

