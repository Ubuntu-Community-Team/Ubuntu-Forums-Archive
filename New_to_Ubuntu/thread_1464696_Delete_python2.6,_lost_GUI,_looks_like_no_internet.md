---
title: "Delete python2.6, lost GUI, looks like no internet connection on Ethernet"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by MorrisseyJ on 2010-04-28
Hi, i do hope that someone can help me. I feel like an idiot.

I have, like a number of other people, tried to remove python 2.6 and i have now lost my GUI ([http://ubuntuforums.org/archive/index.php/t-1383590.html](http://ubuntuforums.org/archive/index.php/t-1383590.html) , [http://ubuntuforums.org/showthread.php?t=1383588](http://ubuntuforums.org/showthread.php?t=1383588)).

The exact same thing has happened to me: While uninstalling Python 2.6 my machine jumped to a TTY login screen.

When i try and reboot i get a message saying "Ubuntu is running in low-graphics mode"...The following error was encountered. You may need to update your configuration..."(EE) open /dev/fb0: Nosuch file or directory"

I click OK and get 4 options:

>Run Ubuntu in low graphics mode...
>Reconfigure Graphics
>Troubleshoot error
>Exit to console

I click the first one which takes me to a TTY screen.

I have tried following the solution in this thread: [http://ubuntuforums.org/showthread.php?t=1383588](http://ubuntuforums.org/showthread.php?t=1383588)

and so i try
> 
sudo apt-get install ubuntu-desktop pythonI then got a message saying

> dpkg was interrupted, you must manually run 'sudo --configure -a' to correct the problem So i run

> sudo --configure -aI can't remeber what the screen brought up after that.

I then tried again with

> 
sudo apt-get install ubuntu-desktop pythonI get the option to proceed and install and get a whole bunch of text repeatedly mentioning something like: 'could not resolve 'no.archive.ubuntu.com'' which is similar to this thread [http://ubuntuforums.org/showthread.php?t=785928&page=2](http://ubuntuforums.org/showthread.php?t=785928&page=2).

The last comment on this page (Tony Flurry) points out that the problem is that i am not online.

Solution then is to connect via an ethernet cable - [http://ubuntuforums.org/showthread.php?t=785928&page=3](http://ubuntuforums.org/showthread.php?t=785928&page=3) - 3rdalbum's solution.

Problem is that i am already connected with an ethernet cable and i am still getting 'could not resolve 'no.archive.ubuntu.com'' suggesting that i am not connected to the internet.

I feel like a fool for having made this mistake which i now see is all over these forums. If anyone knows how to fix this or has any ideas that would be greatly appreciated.

---

### Post by Bachstelze on 2010-04-28
You could try simple DHCP configuration of your wired interface:

```
sudo dhclient eth0
```

Hopefully that will get you connected.

---

### Post by nothingspecial on 2010-04-28
Try 
```

ifconfig eth0 up
dhclient
```

to get yourself a connection.

You may have to sudo it.

[COLOR="Blue"]SNAP[/COLOR]

---

### Post by MorrisseyJ on 2010-04-28
Thank you both so much.

I tried 

> sudo dhclient eth0and that worked (so i don't know about nothingspecial's solution).

Then i ran 

> sudo apt-get install ubuntu-desktop pythonThings installed, i rebooted and now have my GUI back.

Lesson learned this side regarding simply removing programmes. 

On this front does anyone know how i might communicate something with people organising the forums/ubuntu web pages. I ask because i see a lot of tutorials which describe the software centre as being like the add/remove option in Windows. As a recent windows user, now ubuntu convert, i did so however this python experience tells me that this is clearly not the case. I feel like it would be useful if somewhere there was a cautionary note on removing programmes from the machine, but i am not sure who to suggest this to.

Anyway, thanks very much to you both as well as to all the people who helped on other threads.

---

### Post by nothingspecial on 2010-04-28
> **MorrisseyJ said:**
>  

and that worked (so i don't know about nothingspecial's solution).


It`s the same thing, different syntax - hence snap.
> **MorrisseyJ said:**
>  

On this front does anyone know how i might communicate something with people organising the forums/ubuntu web pages. I ask because i see a lot of tutorials which describe the software centre as being like the add/remove option in Windows. As a recent windows user, now ubuntu convert, i did so however this python experience tells me that this is clearly not the case. I feel like it would be useful if somewhere there was a cautionary note on removing programmes from the machine, but i am not sure who to suggest this to.

Anyway, thanks very much to you both as well as to all the people who helped on other threads.

It is a common pitfall. Just make sure you have a look at what else will be removed when you remove something. If it gives a big long list of important looking packages, then don`t remove it. Ignore it.

---

### Post by MorrisseyJ on 2010-04-28
Yup, will do in future. I guess this is one of the ways you learn.

Thanks again for all the help.

---

