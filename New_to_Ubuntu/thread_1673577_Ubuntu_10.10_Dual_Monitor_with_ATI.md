---
title: "Ubuntu 10.10 Dual Monitor with ATI"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by laus_deo on 2011-01-22
I just recently upgraded to 10.10 and was trying to get my dual monitor set up to work because when i try to change the monitor settings it tells me to log in and log out while nothing changes. I tried a few solutions I found online, but nothing seemed to work. This lead me to look through the ATI Catalyst Control Center, where I found I could switch it to extended screen there. Then it told me to restart, and now my computer won't boot up regularly. I can get it up in limited graphics mode, only on my second screen, but now I can't change the setting back because when I try to access the Control Center it says 

> There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.

Any ideas on how to fix that and/or how to get two monitors?

---

### Post by Claus7 on 2011-01-22
Hello,

lot of questions:
1) how did you install ccc?
2) which graphics card do you use?
2) how did you install (if you did) the drivers of your card?

From the message you get it seems to me that you not configured correctly your card. Did you try aticonfig --initial, in order to create a xorg.conf file?

I'm not an expert on dual monitor, yet I tampered with ati on how to work, and from what I have seen, if you are able to make it work on one monitor, the dual thing is not a big issue.

Just that up to now,
Regards!

---

### Post by laus_deo on 2011-01-26
Well I don't know very much about how I did any of those. 

1) I know I was trying to make Braid work one day, and looked through and found the CCC

2)I don't know if this is the exact answer you are looking for, or how to find it if you didn't, but I know I run on an ATI radeon graphics

3) As I said above, when I was trying out how to figure out how to get the graphics to work, I did some upgrade, but I'm not quite sure what that did. But I ended up getting it to work? 

I'm sorry I know so little. 
but I tried aticonfig --initial and here's what I got

```

Found fglrx primary device section
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx-0

```

could you tell me what that means?

---

### Post by Mark Phelps on 2011-01-27
"ATI Radeon graphics" tells us nothing useful.

To find out what make and model graphics card/chipset, open a terminal and enter "lspci".  Look for the line containing "VGA".

Post that result back here. That will help us determine whether or not your card/chipset can actually support fglrx.

---

### Post by Claus7 on 2011-01-30
Hello,

> **laus_deo said:**
> Well I don't know very much about how I did any of those. 

1) I know I was trying to make Braid work one day, and looked through and found the CCC

2)I don't know if this is the exact answer you are looking for, or how to find it if you didn't, but I know I run on an ATI radeon graphics

3) As I said above, when I was trying out how to figure out how to get the graphics to work, I did some upgrade, but I'm not quite sure what that did. But I ended up getting it to work? 

I'm sorry I know so little. 
but I tried aticonfig --initial and here's what I got

```

Found fglrx primary device section
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx-0

```

could you tell me what that means?

first of sorry for the late response, with so many posts lately, your...just escaped me. 

Now there are many posts concerning your issue, yet it seems that you have a basic knowledge, which is bad concerning the issue you wan to solve. Yet, dealing one by one, you will be able finally to find a solution.

1) I have not a dual monitor thing, so I'll try to guide you with the basics, maybe someone else come and help while doing so.

2) it's important, when you want some help to provide as much info as possible in order to take better responses.

Now in order to find your graphics card open a terminal and type the command:
```
lspci | grep VGA
```

IF your graphics card is recognised by ubu, then you will have an output from this command. And you will find out which card you've got.

The aticonf... what it did is: to find out your configuration, meaning your hardware like the screen, graphics card, e.t.c. and create a xorg.conf file under /etc/X11 simultaneously backing up the previous xorg.conf file you had with the name xorg.conf.fglrx-0. 

I told you to that in order to create automatically such a file that should work. That does not mean that it will work and it might mean that it needs some tweaking. Usually, this file, if created correctly, gives all the info needed for your graphics card to word normally with the hardware you have got.

You should be able to check for yourself more about that on how to configure your card with dual monitor harnessing... 

If catalyst gives some warnings that is something bad. One thing would be to reinstall the drivers. A clean fresh installation of ati graphics card can be found here:
[http://ubuntuforums.org/showpost.php?p=9887702&postcount=12](http://ubuntuforums.org/showpost.php?p=9887702&postcount=12)
[http://ubuntuforums.org/showpost.php?p=9901012&postcount=13](http://ubuntuforums.org/showpost.php?p=9901012&postcount=13)

these apply for one monitor... don't know if your configuration was good enough for one monitor as well...

Also will help you to identify some things for your system in order to advance for your specific issue. Have in mind that your card might be different than mine...

and this:
[http://ubuntuforums.org/showthread.php?t=85215](http://ubuntuforums.org/showthread.php?t=85215)
for dual..ing...

Regards!

---

