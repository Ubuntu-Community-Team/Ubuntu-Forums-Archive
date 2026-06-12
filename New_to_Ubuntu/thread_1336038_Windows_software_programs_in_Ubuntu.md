---
title: "Windows software programs in Ubuntu"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by acidb on 2009-11-24
Good morning to all,
 
I am a little computer geek. I am currently running Windows XP Pro SP3 on my work laptop. At work, the main server with all our info on runs on Windows XP Server, and a linux box as the gateway to the internet.
 
We are an accounting firm and because everyone 'knows' Windows, our software that we use is programmed for Windows. All the people I have spoken to tells me that I cannot install these software (Pastel Partner, Caseware and related apps, MS Office 2007 Enterprise, network printer, etc.) onto an Ubuntu OS.
 
I would like to convert to Ubuntu, but havn't done this due to this problem. I would like to know if this is really true? If not, please guide me as to how i would be able to have these 'dedicated' windows apps running on Ubuntu.
 
I would really like to convert to Ubuntu as it is a more secure, stable and predictable OS.
 
Your time and energy will be much appreciated.
 
Kind regards,
acidb

---

### Post by blazemore on 2009-11-24
The Wine project allows Windows applications to be run on Linux, with varying degrees of success.

If you're interested in running Wine, take a look at the website [www.winehq.com](www.winehq.com)
It is well supported in Ubuntu, and is available through the official repositories.

The open-source nature of Wine means there are a few commercial offerings, the most well-known of which is CodeWeavers Crossover Professional, which offers (among others) support for Office 2007.

The best thing to do is take a look at Wine's AppDB database, which maintains user-provided ratings on how well individual software works with Wine.

If you can't seem to find your program working well on there, take a loom at the Crossover website ([http://www.codeweavers.com/products/cxlinux/](http://www.codeweavers.com/products/cxlinux/))

See if they support your application.

If nothing works there, then, well stop trying to play xbox games in a ps3! Linux is not Windows, and there's a lot of open source alternatives available ([www.osalt.com](www.osalt.com))

As far as printers go, Wine won't help you. Most printers work out the box on Ubuntu.

---

### Post by bilalakhtar on 2009-11-24
There is a very good alternative to MS Office that comes preinstalled in ubuntu, its called OpenOffice. It supports all the office file formats including those of office 2007.
In case of network printing (of course) ubuntu supports it.
go to [http://www.osalt.com/](http://www.osalt.com/) if you need any more linux alternatives to windows programs.
In case no alternative is available, you can run the Windows program in Wine. [http://www.winehq.org/](http://www.winehq.org/)

---

### Post by Sir Jasper on 2009-11-24
Hi,

Sadly, I rate your chances of success as zero and you cannot afford to fail.  

An Accountancy Forum or your Institute(s) may be places to double check.

My regards

---

### Post by anaconda on 2009-11-24
office2007 installs and works flawlessly with a new version of wine. (i have 1.1.30)

the other programs you mentioned are not familiar to me, but I recommend you to try it out. Eg. install ubuntu in o virtualbox (wirtual machine) on top of windows, and then get the latest wine version, and try if the programs work with it. 

I would be positive, because I just installed a couple of windows programs with wine, and all of them installed OK.

---

### Post by zaphod777 on 2009-11-24
I recommend try installing on a test machine and configure it the way your users need it configured and then present it to the business if they like it then go for it. You may want to do it on your machine and see what problems you may run into. If it makes life better and it is cost effective because you can use free software then go for it. But remember your time is valuable too. 

will you be making your live easier or more difficult from a IT perspective? 

As far as the server goes XP isn't really a server it sounds like a regular workstation hosting files and printers. If so you can probably run a Linux server to do the same tasks however does your company run quickbooks or some proprietary software on the server? if so then you are probably stuck.

I would definitely test before implementing you don't want to get canned because you are not familiar with Linux and end up hosing everything.

---

### Post by acidb on 2009-11-24
Thank you guys.

zaphod777: I am hoping to pick up an old laptop for cheap and experiment with it. I just wanted to know what I need, if any. I will be checking out WineHQ. I am not looking to transform the whole office, just my own machine. So, I don't really care what the company does.

---

### Post by QLee on 2009-11-24
[QUOTE=acidb]zaphod777: I am hoping to pick up an old laptop for cheap and experiment with it. I just wanted to know what I need, if any. I will be checking out WineHQ. I am not looking to transform the whole office, just my own machine. So, I don't really care what the company does.[/QUOTE]

Just want to mention here in case you haven't thought about it.

Some IT departments will not want a GNU/Linux running machine connected to their network. Often a policy like that is implemented because the IT guys don't have a clue about Linux and thus don't want something they don't understand doing things they don't understand. If there is a problem, they might be too quick to assume your system is the problem. They would probably be incorrect about that (unless you actually did cause something by accident or lack of knowledge) but I think you should seek permission first, in order to cover your "6".

---

### Post by acidb on 2009-11-24
QLee:
Thank you for the advise. I will keep this in mind. Like I did mention, I first want to experiment before implementing it as I do not know anything about Ubuntu, yet.

I have been wanting to get to know Linux/Ubuntu, and I have seen what it looks like, but haven't had any experience with it. So first, I want to know more so that I know what to do if there is a problem.

---

### Post by prenoob on 2009-11-24
[SIZE=2][FONT=Verdana]I assume the programs you mention are accountancy related, in which case I suggest you take a look at the cross platform, open source software on Sourceforge.[/FONT][/SIZE]

---

### Post by qwerty2009 on 2009-11-24
you could try using ubuntu in live cd first to see if your hardware works, then either dual boot or use wubi to install ubuntu like a normal application so you can remove it any time

---

### Post by gdonwallace on 2009-11-24
There is one other way to go.  Crossover for Linux is the pay version of Wine.  Crossover is a little more refined and stays more up to date than Wine.  Not that there is anything wrong with Wine, I just got lucky and got a free copy of Crossover.

You can find it at [http://www.codeweavers.com/products/cxlinux/](http://www.codeweavers.com/products/cxlinux/).  You can download and try it for free for 30 days.  They do maintain a database of programs that are known to install into Crossover, but I would not think to find any specialty programs listed.

---

### Post by gatorbrit on 2009-11-24
You could also install WUBI, which will let you mess with ubuntu on your windows machine and not have to change partitions or do anything too drastic.   I also like crossover office, it makes things a little easier.

But, I doubt that you'll be able to install and run effectively all that you want.  In the end, if you are running everything in WINE, then you're not really getting the benefit of ubuntu.

---

