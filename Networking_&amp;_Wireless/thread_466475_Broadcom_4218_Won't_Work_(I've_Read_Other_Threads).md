---
title: "Broadcom 4218 Won't Work (I've Read Other Threads)"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by plinydogg on 2007-06-06
Hi everyone,

Like a lot of people, I'm having trouble getting my Broadcom 4318 wireless card to work. I found several threads  devoted to this specific card and tried doing everything they suggested. The most recent thread I followed was this one:

[http://ubuntuforums.org/showthread.php?t=197102&highlight=4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=4318)

After following the instructions for Feisty, not only does my wireless not work, but now it doesn't even recognize my wireless card!

I've tried so much different stuff, I'm just not sure what to do next. I just installed Ubuntu today after a lot of help from the wonderful community here, but I can't really start to explore Ubuntu until wireless works because I don't have any other Internet connection. Do I need to reinstall Ubuntu to undo all the damage I did?

Help!!!!!

---

### Post by plinydogg on 2007-06-06
I did what was suggested on this post: [http://ubuntuforums.org/showthread.php?t=197102&highlight=4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=4318)

It looked like I was okay: my wireless card was recognized, I saw no green bars, so I rebooted. After rebooting, the computer wouldn't recognize the card at all (i.e., I was back to square one). I opened up the log file that was created and the when it was trying to install Ndiswrapper 1.9, it said it couldn't find the file (even though I had the livecd in the disk drive as the post suggested). So, I guess I need to download Ndiswrapper 1.9 (through Vista since I can't get online via Ubuntu). Where do I do this?

J#$%S this is frustrating.

---

### Post by GWoitena on 2007-06-06
Can you hook up an ethernet connection?  The best way to do this is to get Ndiswrapper plus the utils from synaptic.  (I learned my lesson to install [I]everything[I] through synaptic).  Install the driver using sudo ndiswrapper -i bcmxx.inf  (or whatever)  Then download fwcutter from synaptic and run it.  

I had my broadcom 4318 card running in 5 minutes after I did a clean install of Feisty.  It took several days with Edgy.

---

### Post by plinydogg on 2007-06-06
Gwoitena: Thank you so much for responding....I thought I was out of the wilderness once I got the OS installed but I am seriously sinking!

The only ethernet connection I could get would be through the cable that is connected to my wireless router. Will unplugging it (to plug it into my computer) mess up my router? I seem to remember when I set up my wireless (ages ago) that it was particularly finicky about what order things were done in.

As far as synaptic goes, is there a guide on what it is and how to use it? I am a total newbie here (just got my Ubuntu installed a few hours ago!). 

And when you say install the driver using sudo ndiswrapper -i bcmxx.inf I'm assuming you mean put my windows driver on the desktop and then do sudo ndiswrapper for that driver? 

I don't think I have ndiswrapper installed and I'm not sure which version I need to get....I had originally planned on just downloading it in Windows, putting it on my USB key, and then copying it onto my linux drive but I don't know which to get, where to get it, etc. 

Feel free to tell me to shut up if I'm a lost cause....

Thanks again for responding!

---

### Post by esavato on 2007-06-06
Nothing worked for me either, until I followed these instructions, and added some steps.
[http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)

---

### Post by plinydogg on 2007-06-06
esavato: thanks for responding! I will definitely give this a shot but in order to use apt-get I need to have an internet connection right? Is there a way to avoid this or am I going to have to mess with my wireless router (which I'm scared silly will be messed up)?

I'm about to go to bed but I will try this in the morning (or whenever I get an internet connection) and will report back here. 

I hope it works! Thanks for the help!

---

### Post by GWoitena on 2007-06-06
> **plinydogg said:**
> Gwoitena: Thank you so much for responding....I thought I was out of the wilderness once I got the OS installed but I am seriously sinking!

The only ethernet connection I could get would be through the cable that is connected to my wireless router. Will unplugging it (to plug it into my computer) mess up my router? I seem to remember when I set up my wireless (ages ago) that it was particularly finicky about what order things were done in.

As far as synaptic goes, is there a guide on what it is and how to use it? I am a total newbie here (just got my Ubuntu installed a few hours ago!). 

And when you say install the driver using sudo ndiswrapper -i bcmxx.inf I'm assuming you mean put my windows driver on the desktop and then do sudo ndiswrapper for that driver? 

I don't think I have ndiswrapper installed and I'm not sure which version I need to get....I had originally planned on just downloading it in Windows, putting it on my USB key, and then copying it onto my linux drive but I don't know which to get, where to get it, etc. 

Feel free to tell me to shut up if I'm a lost cause....

Thanks again for responding!

FYI, there is very little similar between installing software in Windows and Linux.  Check out [https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement).  There's info there about installing software from not only synaptic, but also the command line.  Also, there is a ton of documentation about just about everything you want to know.  

I know some of it doesn't make a lot of sense right away because you're still in a Windows state of mind.  Forget all that.  You're not sticking a CD in and running setup.exe any more.  You're learning something completely new and unrelated.  You're starting from scratch and are going to have to learn step by step just like you did with Windows.

---

### Post by plinydogg on 2007-06-07
I'm looking forward to learning everything!

---

### Post by plinydogg on 2007-06-07
I can't try any of your suggestions right now because I won't be around an ethernet connection for a few hours but something else just occurred to me (and I asked about it on a separate post): 

The wireless network I'm trying to connect to is has WPA-Personal and I've read somewhere that additional steps can be needed before you can connect to such a network. If this is true, doesn't it mean, hypothetically at least, that I may have actually got wireless working at some point but just couldn't connect because of the separate WPA issue? 

[If you want to repsond to this specific issue, please do it in the following thread just to keep the issues separate and help future searchers of the forums: [http://ubuntuforums.org/showthread.php?p=2798851#post2798851](http://ubuntuforums.org/showthread.php?p=2798851#post2798851) ]

Thanks!

---

### Post by plinydogg on 2007-06-07
Okay. Even though I'm without ethernet right now, I tried to follow the instructions in the thread you posted about esavato. Specifically, I did the following:

(1) Blacklisted the pre-installed driver by running this in a terminal:

[HTML]sudo gedit /etc/modprobe.d/blacklist[/HTML]

The last line in the file says the following:

[HTML]#module below does not work with Broadcom 4318 wireless cards
blacklist bcm43xx[/HTML]

(2) Got ndiswrapper utils. rather than getting it using aptget, I went here: [http://archive.ubuntu.com/ubuntu/pool/](http://archive.ubuntu.com/ubuntu/pool/) and downloaded a copy of ndiswrapper utils. There were several versions so I downloaded them all. The one that I went with was the only one that didn't produce a dependency error when I tried to install it. It was named:

ndiswrapper-utils_1.8-Oubuntu2_i386.deb

I installed this by double-clicking on it from my desktop.

(3) I used ndiswrapper to configure the drivers. First I tried doing it with the bcmwl6.sys driver that my Windows Vista used but that didn't work. So then I tried doing it with the bcmwl5.inf and bcmwl5.sys drivers and it looked like that did work. 

(4) Then I typed in:

[HTML]sudo ndiswrapper -m[/HTML]

(5) I rebooted and it didn't work, so I tried the other recommended lines of code, specifically:

[HTML]modprobe ndiswrapper
echo ndiswrapper >>  /etc/modules[/HTML]

Nothing happened even after a reboot and when I typed in the second line of code I got some kind of access denied error. 

(6) Finally, I followed the suggestion to do this:

[HTML]sudo gedit /etc/modprobe.d/ndidswrapper[/HTML]

And then changed the reference from "wlan0" to "eth1" since back when my card was detected this is what it was called. 

------------------------

It still doesn't work. I can't think of what the problem would be other than that I have both drivers installed. Here's the output of sudo ndiswrapper -l:

[HTML]Installed ndis drivers:
bcmwl5[/HTML]

---

### Post by plinydogg on 2007-06-07
Sorry about that. The output of sudo ndiswrapper -l is:

```
Installed ndis drivers:
bcmwl5          driver present, hardware present
bcmwl6          invalid driver!
```

Help!

---

### Post by plinydogg on 2007-06-07
ARGH!!!!! I tried to connect my Ethernet (by plugging into the cable) and it didn't work. So I did a clean install of ubuntu and tried the method above (described in the prior two posts) again but installed bcmw15 instead of bcmw16. Same exact result:

(1) the bcm43xx driver is blacklisted
(2) ndiswrapper -l says that the driver and the hardware are both present
(3) but when I go to System->Admin->Network, the wireless card isn't there. 

What should I do? Is all hope lost? I can't realisticallly use Ubuntu if I can't get online. This shouldn't be so hard :(

---

