---
title: "SVN from command line"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by malfist on 2007-04-30
I've done it once I just don't remember how. I work with a remote SVN repository with several programmers for a small gameing website. How can I connect to the repository through the command line? I mean with just going to the dir and typing svn commit or svn checkout without the url and username/password. Any ideas, I've done it with one repository but I don't remember how to do it with the others.

---

### Post by jlsheehan on 2007-04-30
> **malfist said:**
> I've done it once I just don't remember how. I work with a remote SVN repository with several programmers for a small gameing website. How can I connect to the repository through the command line? I mean with just going to the dir and typing svn commit or svn checkout without the url and username/password. Any ideas, I've done it with one repository but I don't remember how to do it with the others.

Hi,

"svn update" will fetch remote changes locally

"svn commit" will publish your changes

"svn help" will give you more information.

Jeff

---

### Post by malfist on 2007-04-30
when I do svn update, it tells me Skipped ',' and svn commit says '.' is not a working copy

---

### Post by jlsheehan on 2007-04-30
Hi again,

Maybe I jumped too far ahead...the above commands must be performed from a local subversion "working copy".

To get a local working copy you have to "check it out" from the remote repository.

Depending on what access methods are available to you will determine the URL to your remote repository.  For example I commonly use something like this:

svn checkout svn+ssh://svn.example.com/home/svn/projectrepo/trunk localdir

Once checked out, you can use the commands given previously from inside the localdir directory.

Jeff

---

