---
title: "programs not showing up in synaptic"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by aharown07 on 2009-08-18
Can't figure out what I'm doing wrong. Brand new to Ubuntu/Linux. 
Several programs I've installed have not installed properly, mostly due to not doing it "right" through the package manager(s)...  but I've been doing that because the programs are not showing up in the package managers.
For example, Opera... why doesn't that show up?
(I have verified that "universe" is a source in Synaptic)

Another was Filezilla... had to install via command line. (At least that one went well and works fine... Opera I had to purge... something very wrong there... very, very slow)

So what can I check to get all the programs showing up in the package managers?

---

### Post by super kim on 2009-08-18
hi aharown07,

what version of ubuntu are you using? for example hardy, itrepid, jaunty?
if your not sure click on the "System" then "Administration" then look for "System Monitor" the first tab is called "System" that will have the release.

---

### Post by zephyrcat on 2009-08-18
In Ubuntu there are multiple ways to install software. I would recommend you read this guide:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

As to your question, software will only show up in Synaptic if it was installed via Add/Remove Programs (in the Applications menu), Synaptic, or a .deb package. If you executed some commands in a terminal (command line), the program will not show up in Synaptic.

As far as the Opera problem, how did you attempt to install Opera? You should be able to install Opera by downloading a .deb file from this page:

[http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)

Then just double click on the file, click Install, and enter your password.

---

### Post by super kim on 2009-08-18
for jaunty (9.04) look at this [here]("http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04-p4")
or [here]("http://yaplc.blogspot.com/2009/01/how-to-install-opera-on-ubuntu-810.html") for intrepid (8.10)
and for dapper or hardy look at [this]("http://ubuntu-tutorials.com/2007/02/03/installing-opera-on-ubuntu/")

why opera anyway? firefox is free, opera is not. the epiphany browser is also very good inho.

---

### Post by rsiddharth on 2009-08-19
I think this link may help you in installing Opera successfully - [https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

This link will give a Introduction to Software Repositories  : [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by aharown07 on 2009-08-19
To answer some questions... 
Using Jaunty
Why Opera? Because I do web development and I have to see how it looks in all the major browsers... and also Opera is free... at least, they've never asked me to pay for it. (FF is my main browser)

I installed by downloading a .deb file and then running it. I may actually be a problem w/the flash plugin. Will need to install again and test some more.
I've done some reading on repositories but looks like there are some links here to stuff I haven't seen so I'll check them out. Thanks.

About terminal vs. Synap... ins't Synap. just a GUI to what's happening when you install from terminal? Thought I read that somewhere.

---

### Post by bapoumba on 2009-08-19
> **aharown07 said:**
> To answer some questions... 


About terminal vs. Synap... ins't Synap. just a GUI to what's happening when you install from terminal? Thought I read that somewhere.

Synaptic is a graphical application for apt. It does the same thing as apt-get does from the command line. They share the history file, so you can use either one.

---

### Post by mcduck on 2009-08-19
> **zephyrcat said:**
> 
As to your question, software will only show up in Synaptic if it was installed via Add/Remove Programs (in the Applications menu), Synaptic, or a .deb package. If you executed some commands in a terminal (command line), the program will not show up in Synaptic 

Not exactly true. Synaptic, Add/remove, and the Update Manager, and Gdebi are all frontends to apt-get , the very same tool ypu'd usually use from command-line. And apt-get handles installing packages with dpkg, the very same tool you'd use to install individual .deb packages.

As long as what you install comes in .deb package, it will be registered by the package management and will show in all these tools. It makes no difference if you use GUI tools or terminal commands to install the package.

(Well, not in the Add/Remove, since it's made to display only a small selection of most popular graphical apps).

Now, if you use any other means than apt-get/dpkg (or the GUI tools based on these), the program of course will not show in package management.

---

### Post by 3rdalbum on 2009-08-19
> **aharown07 said:**
> To answer some questions... 
Using Jaunty
Why Opera? Because I do web development and I have to see how it looks in all the major browsers... and also Opera is free... at least, they've never asked me to pay for it. (FF is my main browser)

I respect that (I use Opera too, actually).

What the other poster meant was "Opera is not Free".

If software is "free software" it means that you don't have to pay for it. If software is "Free Software", then you don't have to pay for it AND you get access to the source code AND your modifications to the source code also automatically become Free Software.

> I installed by downloading a .deb file and then running it. I may actually be a problem w/the flash plugin. Will need to install again and test some more.
I've done some reading on repositories but looks like there are some links here to stuff I haven't seen so I'll check them out. Thanks.

About terminal vs. Synap... ins't Synap. just a GUI to what's happening when you install from terminal? Thought I read that somewhere.

Pretty much - Synaptic is a GUI to the "dpkg" and "apt-get" commands. If you installed something from a .deb package, it will show up in Synaptic.

So yes, Opera is there in Synaptic if you have installed a .deb package of it.

---

### Post by super kim on 2009-08-19
> **3rdalbum said:**
>  "free software" it means that you don't have to pay for it. If software is "Free Software", then you don't have to pay for it AND ...

sorry i hardly ever use the **** key

to the op i hope you got opera installed in the end :)

---

### Post by aharown07 on 2009-08-19
Yeah, I'm still a little confused about installing via package mgr vs. downloading a .deb file. Had some trouble getting VirtualBox installed initially when I downloaded their .deb that said it was for Ubuntu.
Later, did it again via the package manager and it ran fine. When I posted about it, someone said it's not a good idea to download .deb files... and I seem to recall reading that at Ubuntu.com somewhere also. 
Perhaps it's more a matter of getting the right "version" of the package?

Anyway, right now I have Opera running in Wine, but will make another attempt at a real Linux install soon. It doesn't look very good in Wine (and... to jab at Opera lovers, the only reason to use Opera is that it's so pretty)

Oh, about "free" and "Free"... I get it now. Slowly adapting to the Open Source culture--or should I say "open source" or "opensource" or...  :)

---

### Post by rsiddharth on 2009-08-19
> 
Later, did it again via the package manager and it ran fine. When I posted about it, someone said it's not a good idea to download .deb files... and I seem to recall reading that at Ubuntu.com somewhere also. 
Perhaps it's more a matter of getting the right "version" of the package?

Why some recommend not to install software through .deb file is because of  ' dependencies ' issues that may come in the way . For instance an Alarm Clock application may depend on libraries/code(s) which may not be included in the .deb file ( you got to install the library/libraries before being able to install the software itself ) . In nutshell a particular application may depend on one or more libraries to install and run successfully . 

The beauty of the APT system is that it takes care of the these dependencies , installation , un-installation , management of the application (  updating , etc ) . 

To get a clear idea of  " Software Management  " in Linux and in ubuntu in particular , read the chapter 6 of a book named " ubuntu pocket guide " written by Keir Thomas . 

Here is the link from where you can  download the book : [http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

Here is link from which you can read the book from your Browser itself ( If your choosing this pathway ,head directly to the 6th chapter titled " Software Management " ) : [http://books.google.co.in/books?id=kHLlJzI6L20C&pg=PP17&dq=ubuntu+pocket+guide&client=firefox-a#v=onepage&q=&f=false](http://books.google.co.in/books?id=kHLlJzI6L20C&pg=PP17&dq=ubuntu+pocket+guide&client=firefox-a#v=onepage&q=&f=false)

---

### Post by mcduck on 2009-08-19
Installing things from .deb is absolutely OK, as long as you trust the source where you got the .deb package.

It's just that installing through apt-get/Synaptic is easier and safer, it's able to handle all dependencies automatically, and all programs are tested to be compatible with your system.

(apt-get will uninstall, update etc. all packages you installed from separately downloaded .deb packages. They are no different from .deb packages downloaded through apt-get itself. It's just that it's only able to provide updates if the same package is available through the repositories. And if it's available, then why download it manually anyway?)

---

