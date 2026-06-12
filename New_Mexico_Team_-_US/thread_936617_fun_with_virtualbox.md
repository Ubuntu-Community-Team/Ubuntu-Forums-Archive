---
title: "fun with virtualbox"
date: 2008-10-03
forum: New Mexico Team - US
---

### Post by randancing on 2008-10-03
I have been playing around with virtualbox and have run on to some thing I don't understand---

[

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

    ]


I have no idea how to 'execute' something. I thought it was a command, but it appears that Bash doesn't like it and I am too slow to figure out what it is telling me to do.

I did apt-get and install on the modules, but I can't seem to get around the       /etc/init.d/vboxdrv start

I know it is a path but I don't know how to set the path and the vbox together.

I have just completed my first week as a Linux user. Happy anniversary to me.

---

### Post by mindoms on 2008-10-03
Congratulations to your anniversary :)

run this, to make sure all packages are installed:
```

sudo apt-get install virtualbox-ose virtualbox-ose-modules-`uname -r` 

```

add your user to the vboxusers group. This is a permission thing. so you are allowed to use virtualbox
```

sudo adduser $USER vboxusers 

```

re-login. this will close all apps and restart the x-server, so make sure all work is saved.
control+alt+backspace

here comes the thing you actually asked about:
open a terminal and run:
```

sudo /etc/init.d/vboxdrv restart 

```

so you only missed the sudo (super user do) thing. This is essential, because normal users dont have the permission to start/stop services.

now you should be able to run virtualbox

hth, stefan

---

### Post by randancing on 2008-10-04
This has been a frustrating journey. I have tried everything that has been given here as well as things I have found on at least twelve other forums, and I still couldn't get the thing to install.
I finally did the right thing and decided to un-install the ose version and get a new version from virutualbox .org. 
I used the package manager to uninstall the old package and to download and install the new package. 

Should be a winner, do you think???

It froze on the installation (it wanted me to give permissions for the users to use the software. Who else would be using???) 

I closed the window that had frozen and the installation continued and the terminal log showed that things were progressing until it said done.

Now there is no indication of any form of VirtualBox anywhere on my computer. All it tells me is that no file or directory exists. 

Remember, I said I was 'INSTALLING'. It said it had 'INSTALLED'. It said it  was on my computer, and that I would now be happy and proud and productive and all the things that go with fighting a long battle and coming out the other end alive, except----

Now it says there is no such file or directory.

I used ls -home, and it shows VirtualBox is there. Except that it doesn't exist and I can't use it because even though it is there it isn't there.

'Howtoforge' has an extensive guide to getting and installing Virtualbox. There is one thing that you have to do before you even download the program.
I have pasted it below:


[http://www.howtoforge.com/virtualbox_ubuntu](http://www.howtoforge.com/virtualbox_ubuntu)

apt-get install bcc iasl xsltproc xalan libxalan110-dev uuid-dev zlib1g-dev libidl-dev libsdl1.2-dev libxcursor-dev libqt3-headers libqt3-mt-dev libasound2-dev libstdc++5 linux-headers-`uname -r` build-essential


What makes me really happy about the above is that this is what I needed to know, get, and install, before I even downloaded the progrm.

WHAT?WHAT?WHAT?

It is going to take a year of study just to figure out what all that stuff is. That is insane.

below is the address for the download. It is simple, fast, and very intuitive. Watch out for it. It is like baited bear trap. It smells good, but once you are into it you will have to gnaw off your own foot to get out.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)


I have not given up, but I can see that this is not a journey, it is a quest. I must somehow carry this ring Linux to the mountain of Virtualbox.

---

### Post by mindoms on 2008-10-04
> **randancing said:**
> This has been a frustrating journey. I have tried everything that has been given here as well as things I have found on at least twelve other forums, and I still couldn't get the thing to install.
I finally did the right thing and decided to un-install the ose version and get a new version from virutualbox .org. 
I used the package manager to uninstall the old package and to download and install the new package. 

Should be a winner, do you think???

If there exists an Ubuntu Package, then you should really use that one.
> **randancing said:**
> 
It froze on the installation (it wanted me to give permissions for the users to use the software. Who else would be using???) 

Linux is a multi-user operating system. There could be an other family member using your computer. You are actually using 2 accounts too. your normal account and die administrator account (sudo command). So you need to specify what user should be allowed to run virualbox (and therefore use the virtualbox-daemon)

> **randancing said:**
> 

apt-get install bcc iasl xsltproc xalan libxalan110-dev uuid-dev zlib1g-dev libidl-dev libsdl1.2-dev libxcursor-dev libqt3-headers libqt3-mt-dev libasound2-dev libstdc++5 linux-headers-`uname -r` build-essential


What makes me really happy about the above is that this is what I needed to know, get, and install, before I even downloaded the progrm.

WHAT?WHAT?WHAT?

It is going to take a year of study just to figure out what all that stuff is. That is insane.

I dont know most af those packages either. but all packages appended with "-dev" contain source code. the build-essential package will install compilers and other programs needed to compile stuff.

But you don't want to compile stuff. you want to install it using the ubuntu-packages.
Just follow the steps in my previous posting.

btw. do you run 32 or 64 bit ubuntu?
```
 uname -m 
```
please post the output, just to be sure

---

