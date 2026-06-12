---
title: "Not able to Install any software via Ubuntu Software Centre"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by Cool G5 on 2009-11-10
As the title explains, I'm not able to install any software via the Ubuntu Software Centre. I tried installing gdesklets but got the following error;

```
[SIZE=4][B]Package Operation Failed
[/B][SIZE=2]The installation or removal of a software package failed.

Details:

E:I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package.: [/SIZE][/SIZE]
```

---

### Post by MelDJ on 2009-11-10
hi again
try [http://ubuntuforums.org/showthread.php?t=446363](http://ubuntuforums.org/showthread.php?t=446363)

---

### Post by Cool G5 on 2009-11-10
Thanks MelDJ for the prompt reply.

First I tried with,

```
sudo aptitude -f install
```

Got this,

```
gaurav@gaurav-desktop:~$ sudo aptitude -f install
[sudo] password for gaurav: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following partially installed packages will be configured:
  adobe-flashplugin 
0 packages upgraded, 0 newly installed, 0 to remove and 38 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download

```

The second command i.e.

```
sudo aptitude clean
```

Worked fine but then I checked again but still the software centre throws up the same error as mentioned in my first post.

---

### Post by mac9416 on 2009-11-11
Hey,

Try this...

```
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way
```

---

### Post by joepz on 2009-11-14
Hi All,

Now I am an absolute beginner, installed 9.10 today. Already surfing the net and very happy with the looks and speed of things. Good bye XP.

Now of course the first thing I am looking into is installing software, updates, plugins what have you. But...

I cannot install anything. Have looked at my rights (should be able to do everything). Enter my password without problems, but whatever I do, each new package fails.

E.g. for Flash plugin I get  detail error message: E:I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package.: 

I have browsed this forum a bit and see code:

sudo apt-get install ubuntu-restricted-extras What is this? Where to enter such code?

I gather I have a more general/overall problem as no software is installing at all.

Any tips for this enthusiastic absolute beginner :D

Thanks!

---

### Post by mac9416 on 2009-11-14
Hey, jeopz, welcome to Ubuntu!

The first thing you'll have to do is run the four commands I posted above. Go to Applications > Accessories > Terminal. Then copy and paste the commands in one at a time. When it promts you for your password, just type it and hit ENTER. You won't see the password as you type for security reasons, but it is being entered.

After running those commands, you'll be able to install software ans run any other commands you want (like 'sudo apt-get install ubuntu-restricted-extras').

Best of luck!

---

### Post by cariboo on 2009-11-14
For a new user, go to System-->Administration--Synaptic Package Manager, and enter ubuntu-restricted-extras in the quick search box, right click on it and select **mark for installation** then click apply. This meta package will install most of the audio/video codecs you need to play most media, as well as flash, java and mscorefonts.

---

### Post by joepz on 2009-11-15
Thanks! It worked\\:D/

After I entered the 4 sentences of code (by mac9416) Flash was working and now I am able to install whatever package I like. Also Synaptic is working now (wasn't before)
Is this some kind of insiders password?

I also installed the Ubuntu-restricted-extras without any problems.

Thanks again! :biggrin:

---

### Post by mac9416 on 2009-11-15
> Is this some kind of insiders password?

Haha, not exactly. I've seen the "E:I wasn't able to locate file for the adobe-flashplugin package." error quite a few times, and these commands have always succeeded in forcing adobe-flashplugin to remove properly.

Glad it worked for you!

---

### Post by Cool G5 on 2009-11-16
> **mac9416 said:**
> Hey,

Try this...

```
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way
```

Sorry for the late reply but the four commands you mentioned worked perfectly. Now I'm able to install software via Ubuntu Software Center, by double-clicking the deb & also via console. Thanks a lot. :)

---

### Post by asoutar on 2009-11-27
> **mac9416 said:**
> Hey,

Try this...

```
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way
```


That worked perfectly .. Thanks!    =D>

---

### Post by RefinersFire on 2010-04-17
I tried all of the commands shown and nothing has worked.

I cannot completely install any software or System Updates. They all fail.


Ubuntu Restricted Areas:
```
installArchives() failed: Selecting previously deselected package ubuntu-restricted-extras.

(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 144975 files and directories currently installed.)

Unpacking ubuntu-restricted-extras (from .../ubuntu-restricted-extras_36_i386.deb) ...

Setting up yiff-server (2.14.5-5.1) ...

Starting Y Sound Server: invoke-rc.d: initscript yiff-server, action "start" failed.

dpkg: error processing yiff-server (--configure):

 subprocess installed post-installation script returned error exit status 1

Setting up ubuntu-restricted-extras (36) ...

Errors were encountered while processing:

 yiff-server


```

System Update:
```
E: yiff-server: subprocess installed post-installation script returned error exit status 1
```
[[img]http://www.freeimagehosting.net/uploads/th.711c81594b.png[/img]](http://www.freeimagehosting.net/image.php?711c81594b.png)

---

