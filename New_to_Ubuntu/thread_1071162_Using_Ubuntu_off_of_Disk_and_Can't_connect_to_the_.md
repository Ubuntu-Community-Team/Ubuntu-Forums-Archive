---
title: "Using Ubuntu off of Disk and Can't connect to the internet"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by adrianrodriguez on 2009-02-15
Hi, I am completely brand new to Ubuntu and before I installed it on a separate partition I wanted to know why I couldn't connect to my wireless internet.

I have a Windows Vista Home Premium Hp Dv6000 Notebook. Internet works fine when running Vista, but not when running Ubuntu. Could anyone help me?

Also, just to add, what is the best way to use Ubuntu. As an app, a live cd, or a partitioned drive? 

If it's partitioned, will I be able to uninstall it and get the partitioned space back. This is the first time I have ever done this. Thanks and God Bless!

---

### Post by x33a on 2009-02-15
the best way to run any os is to run it off a hard disk.

as for the internet, you might have to configure your network first, in order to use it.

how do you connect to the net on vista? if you are using a router and dhcp, then it should work on ubuntu without any configuring. if you use a dialer, then you'll have to configure the network in ubuntu also.

as for uninstalling ubuntu, you can simply delete the partition it will be installed upon, and then reconfigure/fix the bootloader.

give ubuntu a try, you'll love it.

if you come across any problem, the community is here to help you out :)

---

### Post by sandyd on 2009-02-15
For newbies like you, the best way to install Ubuntu is as an app.

It might be a tad slower than normal, but thats fine because your only testing it.

As for the internet, hmm... try installing it as an app, then see if it works. 

P.S. are you using wireless for internet or cable (ethernet) or dir3ctly connnecting whatever modem (Cable / DSL) to your comp?

---

### Post by MarblePanther on 2009-02-15
> **carlee said:**
> For newbies like you, the best way to install Ubuntu is as an app.

It might be a tad slower than normal, but thats fine because your only testing it.

As for the internet, hmm... try installing it as an app, then see if it works. 

P.S. are you using wireless for internet or cable (ethernet) or dir3ctly connnecting whatever modem (Cable / DSL) to your comp?

I believe she is referring to WUBI install...to clarify

---

### Post by sandyd on 2009-02-15
> **adrianrodriguez said:**
> Hi, I am completely brand new to Ubuntu and before I installed it on a separate partition I wanted to know why I couldn't connect to my wireless internet.

I have a Windows Vista Home Premium Hp Dv6000 Notebook. Internet works fine when running Vista, but not when running Ubuntu. Could anyone help me?

Also, just to add, what is the best way to use Ubuntu. As an **app**, a live cd, or a partitioned drive? 

If it's partitioned, will I be able to uninstall it and get the partitioned space back. This is the first time I have ever done this. Thanks and God Bless!

he knows its wubi :)

P.S. just noticed this
livecd isn't really the best way to use ubuntu, theirs alot of things you cannot do on a livecd. For example, if you had to restart your computer, you would lose everything you were doing a few seconds ago on livecd.

---

### Post by adrianrodriguez on 2009-02-15
Thanks for responding so fast guys. Right now I connect to my home router through wireless and that's on Vista, but when I ran Ubuntu, it said it couldn't find any wirless networks, and the option to search or click on one, was grayed out. 

Any thoughts?

---

### Post by sandyd on 2009-02-15
aww noo.. wireless cards....
ubuntu hates them.....

could you type this in terminal and post the output please... (yes, sometimes a little research is needed for wireless cards to function properly, but it works in the end)

```

lspci

```

---

### Post by adrianrodriguez on 2009-02-15
How do I open the terminal? lol, Told ya I'm a newb.

---

### Post by drjimm on 2009-02-15
I have been running UBUNTU for some time on 2 computers.  I tried to upgrade from 8.04.1 to 8.1 with disastrous results and had to reload 8.04, which works great. I have burned 8.04.2 discs that work OK in 4 computers, 2 KOOBOXes one XP notebook, and one Vista desktop, BUT - I'm trying to configure a new notebook running Vista Home premium for a friend, and when I try to load 8.04.2 it loads initially and asks whether I want to run from the disc or install, but no matter what I choose, all I get then is various patterns on the screen and never the login screen.  I've pretty much given up on that and have let Wubi download and install 8.1.  It at least runs, BUT (another big one) I can't get it to connect to the internet.  This is supposed to be the final issue of 8.1 and not the beta, so why doesn't it contain ALL the files necessary to do what it is supposed to?

I'm certainly not a newbie to UBUNTU, but I sure could use some help now.
I would prefer to put 8.04.2 on my friend's new notebook.  He is handicapped, knows nothing about computers, and UBUNTU would be MUCH easier for him to use to surf the net, do e-mail, and word processing, That is about the extent of his computer usage.

---

### Post by sandyd on 2009-02-15
theirs two ways to do that....

because i don't know what window manager your using, and and i'm not about to get into that. try either of these


Applications -> Accessories -> Terminal
OR
Menu -> System -> Konsole

---

### Post by sailthesea on 2009-02-15
To adrianrodregez I would say just go ahead and try installing within windows with Wubi I hesitated for ages but it was dead easy and you start learning right away You WILL have to tinker with your wireless, but don't be scared to try stuff, the help is great and if you mess up you can simply reinstall and start again I,m pretty new to Ubuntu but it can really work for you if want it to
 Good Luck!

---

### Post by sandyd on 2009-02-15
> **drjimm said:**
> I have been running UBUNTU for some time on 2 computers.  I tried to upgrade from 8.04.1 to 8.1 with disastrous results and had to reload 8.04, which works great. I have burned 8.04.2 discs that work OK in 4 computers, 2 KOOBOXes one XP notebook, and one Vista desktop, BUT - I'm trying to configure a new notebook running Vista Home premium for a friend, and when I try to load 8.04.2 it loads initially and asks whether I want to run from the disc or install, but no matter what I choose, all I get then is various patterns on the screen and never the login screen.  I've pretty much given up on that and have let Wubi download and install 8.1.  It at least runs, BUT (another big one) I can't get it to connect to the internet.  This is supposed to be the final issue of 8.1 and not the beta, so why doesn't it contain ALL the files necessary to do what it is supposed to?

I'm certainly not a newbie to UBUNTU, but I sure could use some help now.
I would prefer to put 8.04.2 on my friend's new notebook.  He is handicapped, knows nothing about computers, and UBUNTU would be MUCH easier for him to use to surf the net, do e-mail, and word processing, That is about the extent of his computer usage.

i can probably smell wireless signals comming from your comp.....

is that right? your using a wireless network?

P.S. thread hijacking isn't considered nice. your issue may be COMPLETELY different than what this guy has, and as a result, you may just end up frustrated because noone gave you the right answer.

---

### Post by David2009 on 2009-02-15
I have a Toshiba A300 series, 64-bit laptop.  I couldn't get OpenSuse to connect with my wireless...and I have version 11.1 installed.  So, as a test, I put in the Ubuntu 8.1 LiveCD.  I had to enter the password for my network three times, but finally it took.  I've been online for over an hour.

True, when I reboot, and/or exit the program, I will lose my connection.

---

### Post by ugm6hr on 2009-02-15
It is likely your wifi uses a Broadcom (BCM) chipset.

To work with Ubuntu, it needs to download "firmware" which is not available on the LiveCD.

Therefore, it is unlikely you will be able to get this to work until you install.

You can confirm this with:
```
lspci
```

See the Code in Terminal link below re: Terminal use

EDIT: If it is a supported BCM chipset - this *might* work with the LiveCD: [http://ubuntuforums.org/showthread.php?p=6028741#post6028741](http://ubuntuforums.org/showthread.php?p=6028741#post6028741) - perhaps if you boot up connected to a wired network the System -> Admin -> Hardware Drivers menu will have the b43 driver available for you to activate?

---

### Post by adrianrodriguez on 2009-02-16
After installing the Wubi version of Ubuntu I was able to download the drivers for my Broadcom Wireless and use the internet. When I was getting ready to use firefox, I noticed Adobe Flash Wasn't installed, when I tried to install it, it told me to go to the terminal and install it from there. From that point on I was lost. How do I install something From the terminal?

---

### Post by sailthesea on 2009-02-16
Hi again
 Glad to see you are testing the water and welcome Like you I,m a pretty new user so I can't tell you exactly what to do at this point as I'm still picking things up The best thing to do is post threads in the right places for the best advice, if you look in the various forums you will get your answers It can be tricky finding your way around Search your posts from the toolbar and follow up when you get a reply and don't be afraid to sound like a noob theres lots of us out here I still haven't got flash player on but I'm going to try now If I win I'll come back to you
 Good Luck!!

---

### Post by ugm6hr on 2009-02-16
> **adrianrodriguez said:**
> How do I install something From the terminal?

See the link below re: Code in Terminal

[Install Flash]("apt:flashplugin-nonfree")

or

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by sailthesea on 2009-02-16
I also found that removing gnash solved this but lost the thread for a bit

 [http://ubuntuforums.org/showthread.php?t=1071051&highlight=gnash](http://ubuntuforums.org/showthread.php?t=1071051&highlight=gnash)

 It might help you

 I just went to youtube and updated Flash player from within Firefox it's what  you're used to and easy enough This Terminal stuff doesn't come easily after you've been a slave to windows but stick with it Having a machine that does what YOU make it is the point  ( mostly, Ubuntu isn't perfect! )
 Hope it works for you

---

