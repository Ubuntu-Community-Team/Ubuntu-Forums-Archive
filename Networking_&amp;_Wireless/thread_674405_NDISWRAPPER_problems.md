---
title: "NDISWRAPPER problems"
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by schwahney on 2008-01-21
I've tried getting wireless working with two different wireless cards, TrendNet TEW-423PI and D-Link DWA-552. ndiswrapper shows hardware present in both cases after installing Windows card drivers. Running "lshw -C network" shows both cards present, though no line indicating driver or "on" state or anything (HELP says to verify this but does not say what one should see or how to change if not present). Network Settings show no wireless network to configure. HELP also says to use "System...Administration...Device Manager", but it is not present (not KDE desktop). This is very frustrating for us newbies.

I've blacklisted 88w8335, AR5416, mrv8335, and net5416 not knowing which of these is the actual name of the chipsets. Then rebooted.

Can someone please identify what I may do to get my wireless working or what info I can provide to diagnose the problem?:confused:I looked in MANY other posts, gone to tutorial pages, etc.

Most recently, run ndiswrapper -v and get:
utils version: 1.9
driver modinfo: could not find module ndiswrapper

Prior to messing around more, I would get a system lockup with 'sudo modprobe ndiswrapper'. That doesn't happen anymore, but neither does anything else.

Thanks in advance.

---

### Post by kirsche on 2008-01-22
did you compile the ndiswrapper successfully?
did ndiswrapper -i <WIN.INF> work?
what does ndiswrapper -l show?

---

### Post by NullHead on 2008-01-22
> **schwahney said:**
> I've tried getting wireless working with two different wireless cards, TrendNet TEW-423PI and D-Link DWA-552. ndiswrapper shows hardware present in both cases after installing Windows card drivers. Running "lshw -C network" shows both cards present, though no line indicating driver or "on" state or anything (HELP says to verify this but does not say what one should see or how to change if not present). Network Settings show no wireless network to configure. HELP also says to use "System...Administration...Device Manager", but it is not present (not KDE desktop). This is very frustrating for us newbies.

I've blacklisted 88w8335, AR5416, mrv8335, and net5416 not knowing which of these is the actual name of the chipsets. Then rebooted.

Can someone please identify what I may do to get my wireless working or what info I can provide to diagnose the problem?:confused:I looked in MANY other posts, gone to tutorial pages, etc.

Most recently, run ndiswrapper -v and get:
utils version: 1.9
driver modinfo: could not find module ndiswrapper

Prior to messing around more, I would get a system lockup with 'sudo modprobe ndiswrapper'. That doesn't happen anymore, but neither does anything else.

Thanks in advance.

OK I can tell ndiswrapper isn't functioning correctly > driver modinfo: could not find module ndiswrapper
 and what you need to do is go to [ndiswrapper-HQ]("http://ndiswrapper.sourceforge.net/joomla/") and download the newest .tar.gz and install build-essestial ```
sudo apt-get install build-essential
``` and then unpack and install ndiswrapper ```
cd ~/Desktop/ndiswrapper*
```
```
make && sudo make install
```then make sure it loads on boot. ```
echo 'ndiswrapper' >> sudo tee -a /etc/modules
```

Then review and remove you're drivers and reinstall them.
```
ndiswrapper -l 
```
```
ndiswrapper -e <driver>
```
```
sudo ndiswrapper -i <driver.inf>
```

---

### Post by schwahney on 2008-03-14
Thanks, NullHead. Sorry it's taken very long to get back to this problem with other stuff going on, but I appreciate your patience. 
All was fine until I tried 
> **NullHead said:**
> ```
cd ~/Desktop/ndiswrapper*
```
The response was,"bash: cd: /home/stephen/Desktop/ndiswrapper: No such file or directory"
I found an ndiswrapper directory under /etc/ but there was no makefile...
remember, I'm a newbie so if there was an impled step, I missed it :(
Can you still help?
Thanks again.

---

### Post by NullHead on 2008-03-15
Yes I can still help. 

I'm sorry I did assume you had ndiswrapper downloaded to your desktop. 

These two commands will download ndiswrapper to your desktop. ```
cd ~/Desktop
``````
wget http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.52.tar.gz
```
Then continue from the steps I gave earlier.

---

### Post by your.pal.cookie on 2008-03-18
First, thanks a lot for the help, NullHead.

It just so happens that I'm having this same problem with my D-Link DWA-552 wireless card on Gutsy. I seem to be in exactly the same boat as schwahney,

Once the driver is installed with

```
sudo ndiswrapper -i net5416.inf
sudo ndiswrapper -m
sudo ndiswrapper -ma
```

The ndisgtk app, and command line queries show that the driver is successfully installed, and that the hardware is present. There's no wireless functionality, yet. I understand that the system needs a restart for this.

On startup, booting hangs on the initialization of the device, which I can tell because I opt to watch the log while the computer starts up. The point of hanging is when it claims to be initializing the device on IRQ 20.

I have to physically remove the card to boot successfully (bypassing this initialization, of course).

I went through the steps you outlined for schwahney, and they were all successful (no error messages), but the hanging still occurs. Lame.

Any ideas on what's causing this problem? Is it a hardware issue, an issue with the driver, or an issue with ndiswrapper? Or is it just too much of a pain to figure out?

Thanks for any more input you can offer.

After building ndiswrapper w/the make dealie per your advice, ndiswrapper -v reports
```
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.45
vermagic:       2.6.22-14-generic SMP mod_unload 586 
```

I think this is what you would expect, but I don't know. I'm beyond newbie.
I've just installed Gutsy Gibbon.

---

### Post by NullHead on 2008-03-18
@your.pal.cookie: 

You did a great job giving information! You've eliminated a few steps by already giving me the information that could possibly be the cause. 

When you showed me the output of ndiswrapper -v I noticed that it said "version:        1.45" It should read with the newest version. 

So what I want you to do is star up synaptic and run a search for "ndiswrapper" and remove what you find that has names along the line "ndiswrapper-common, ndiswrapper-utils-1.9" and use my instructions given earlier. 

> **NullHead said:**
> Yes I can still help. 

I'm sorry I did assume you had ndiswrapper downloaded to your desktop. 

These two commands will download ndiswrapper to your desktop. ```
cd ~/Desktop
``````
wget http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.52.tar.gz
```
Then continue from the steps I gave earlier.

> **NullHead said:**
> OK I can tell ndiswrapper isn't functioning correctly  and what you need to do is go to [ndiswrapper-HQ]("http://ndiswrapper.sourceforge.net/joomla/") and download the newest .tar.gz and install build-essestial ```
sudo apt-get install build-essential
``` and then unpack and install ndiswrapper ```
cd ~/Desktop/ndiswrapper*
```
```
make && sudo make install
```then make sure it loads on boot. ```
echo 'ndiswrapper' >> sudo tee -a /etc/modules
```

Then review and remove you're drivers and reinstall them.
```
ndiswrapper -l 
```
```
ndiswrapper -e <driver>
```
```
sudo ndiswrapper -i <driver.inf>
```

Use them in the order I just quoted. When you're done show me the output of ndiswrapper -v

---

### Post by your.pal.cookie on 2008-03-18
Okay. I'm posting this with my DWA-552 wireless card, which is excellent and thanks to you, NullHead.

According to synaptic, I didn't have any of the ndiswrapper packages installed. I didn't know if it would help, so I installed them, and then "completely removed" them again. It didn't help. Probably because I don't know what I'm doing.

Instead, after changing to the ndiswrapper directory
```
cd ~/Desktop/ndiswrapper*
```

I uninstalled ndiswrapper using make...
```
sudo make uninstall
```
Which removed a bunch of stuff including the ndiswrapper.ko that was reporting the 1.45 version number:
```

removing /sbin/loadndisdriver
removing /usr/sbin/ndiswrapper
removing /usr/sbin/ndiswrapper-buginfo
removing /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
removing /lib/modules/2.6.22-14-generic/misc/ndiswrapper.ko

```

Then I rebuilt the thing:
```
make && sudo make install
```
and confirmed that the version numbers were now correct. Hooray!

And went on from there as per NullHead's original steps.

I'm pretty happy about getting this working. Thanks again.

---

### Post by NullHead on 2008-03-18
Glad I could be of help to you :) 

You probably had a older version installed form source that you didn't know about. And installing and removing the package will help only if you had installed it from synaptic before.

---

