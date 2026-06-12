---
title: "GEDIT install"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by viodelin on 2009-06-19
Hello,
I'm just starting to use Linux. I am trying to install GEDIT but the configuration doesn't complete and gives me the error:

C compiler cannot create executables

This is after I put in sudo -i and my password. I am the only user, so there is nobody to not give me permission.

Can anybody help?

thanks
Maria

---

### Post by Paqman on 2009-06-19
What distro are you using? Gedit should come as default with anything using the Gnome desktop (eg: regular Ubuntu)

You can install it on a system using a different desktop (eg: KDE on Kubuntu) using your package manager, but it'll probably want to install a ton of Gnome dependencies.

---

### Post by viodelin on 2009-06-19
Thanks for your quick reply.
I have Hardy heron ubuntu and it doesn't seem to have Gedit. I downloaded gedit from [http://ftp.acc.umu.se/pub/GNOME/sources/gedit/2.24/](http://ftp.acc.umu.se/pub/GNOME/sources/gedit/2.24/) ( I read somewhere that this was the latest stable version)

---

### Post by kostkon on 2009-06-19
> **viodelin said:**
> Thanks for your quick reply.
I have Hardy heron ubuntu and it doesn't seem to have Gedit. I downloaded gedit from [http://ftp.acc.umu.se/pub/GNOME/sources/gedit/2.24/](http://ftp.acc.umu.se/pub/GNOME/sources/gedit/2.24/) ( I read somewhere that this was the latest stable version)
Actually it comes with Gedit by default. You can access it from *Applications &#8594; Accessories &#8594; Text Editor*.

Also, I would like to recommend you [this nice guide on how to install software in Ubuntu]("http://www.psychocats.net/ubuntu/installingsoftware").

Hope that helps.

---

### Post by viodelin on 2009-06-19
Well, I never! I thought the text editor was a notepad - which maybe it is. I'll try it out.
thanks also for the link, I really needed that anyway.
Cheers,
Maria

---

### Post by drkameleon on 2009-06-19
How about typing...

```
gedit
```

...in the terminal? (CAREFUL with lowercase, *nix is case-sensitive)

GEDIT IS part of any default installation, indeed. ;)

---

### Post by Rubicon_82 on 2009-06-19
It seems that you are trying to build gedit from source.  Is there any reason why you are doing this, instead of installing the binary package through your package manager?

There are a few things you can check to help determine the source of your compiler error:

What version of the geidt source are you trying to compile?
Have you read the README and/or INSTALL files that came with the source?  Do you understand them?
Do you have write access to the place you're trying to build the source, and is there enough free space on the drive?
Did that version come with a 'configure' script, and did it successfully complete?  If not, try installing the development packages ./configure cannot find (e.g. *package_name-dev*).
Did 'make' successfully complete?
Does a makefile target exist for 'check'?  If so, does 'make check' successfully complete?

Note that if you've obtained the source code with 'apt-get source <package-name>', running 'apt-get build-dep <package-name>' will take care of the build dependencies for that package.

---

### Post by viodelin on 2009-06-19
Thanks, Rubicon, for your reply. 
I'll just close this thread by saying that I'd been reading the readme files for gedit in gedit without realising it, silly old me.:)

---

### Post by nothingspecial on 2009-06-19
> **viodelin said:**
> Thanks, Rubicon, for your reply. 
I'll just close this thread by saying that I'd been reading the readme files for gedit in gedit without realising it, silly old me.:)

If that`s the silliest thing you do with your new linux installation then you`ll have done well.

---

