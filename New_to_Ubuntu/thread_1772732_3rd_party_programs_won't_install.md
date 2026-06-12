---
title: "3rd party programs won't install"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by tillich on 2011-06-01
So I'm totally new to Ubuntu, been using 11.04 for the last five days or so... liking it, but I keep having this problem where whenever I try to install something I downloaded (not found in the software centre) such as Opera or Gunity, I click the "Install" button but nothing happens. It looks like it's starting to install, but then it stops and it says "Install" on the button all over again, as though I never clicked it.

Programs that can be found in the software centre work fine... but others don't seem to work at all. What's going on here?

---

### Post by jtarin on 2011-06-01
Applications are packaged for Ubuntu with the .deb extension. If your packages do not have this extension they will not install. You cans use the Synaptic package manager to search for and install software. Pay attention to the package extension names.

---

### Post by wolfen69 on 2011-06-01
What types of files are these? .Debs?

---

### Post by mastablasta on 2011-06-01
what is the file name of programme you want to install?
 
it should be something like Opera.deb
 
 
.exe is a windows executable.
 
it can also be instal.sh i think. in this case you need to make it executable and allow it to be excecuted.

---

### Post by tillich on 2011-06-02
Okay, that was the problem I think. Instead of .deb, they were all .trz or something like that, I deleted the file and don't remember the exact extension. Thanks for all your help!

---

### Post by Chronon on 2011-06-02
It was probably .tgz, which could contain binaries and an install script.  There should be a README that tells you how to install.

Searching for "Opera deb" gave me this page:
[http://deb.opera.com/](http://deb.opera.com/)

If you want to install software from sources other than Ubuntu repositories this is what you should look for: A signed repository with instructions on how to add their public key to your keychain.  Now the package manager can authenticate the source of the packages when you install and these packages should show up in Synaptic or Ubuntu Software Center.

You can also install directly from .tgz like the one you downloaded.  This is simply a less preferred method than adding a repository since the latter method gives a way for the vendor to push security updates (and the signing helps ensure that no malicious 3rd party has tampered with the files).

---

### Post by Ghost|BTFH on 2011-06-02
In case you haven't caught on yet - installing from outside the repositories is a high risk situation.

When doing so, you are in effect granting root permissions to a piece of software which may or may not be what it claims.  Getting programs from the repositories is the way to go for safe, secure computing.

A solid idea is to ask in here if there's something you want to install and are unclear on where it might be found.  There are a lot of additional repositories that we long-time users know, trust and can suggest that will allow you to get pretty much anything you might need.

Be safe, not sorry.

Cheers,
Ghost|BTFH

---

