---
title: "Random Freezes in 9.10 and Other &quot;Related&quot; Issues"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by Naturally-Simple on 2009-12-23
So I'll give this another shot, this time with my own thread since I wasn't getting responses from other postings.

Ubuntu 9.10 just freezes sometimes. I can move the mouse, but can't click on anything. It happens while I'm running any number of different programs, so I haven't noticed a pattern to the freezing. Many help threads have suggested ctrl-f1, ctrl-f7, ctrl-alt-bkspace, alt-printscreen-reisub, etc. etc. etc. but NOTHING WORKS. All that's left for me to do is push the power button until it all shuts down. 

Here's a kicker that I haven't found in other threads: When I turn it back on, it will sometimes work fine, but other times it will load without any display. Even though I can't see, I move the mouse cursor to where I think the shut-down menu is, and I shut the computer down in this way (pressing the other ctrl-alt combos don't do anything). Then when it restarts, sometimes it works fine, but it will often be a repeat of the blank screen, even though I can hear that Ubuntu has loaded fine. This blank-screen start up usually seems to come in pairs, sometimes three in a row.

I looked at the syslog file and from the last time the freeze happened, which was two hours ago. The freeze happened at 21:11, and here is the log file for that time and a little afterward:
> Dec 22 21:09:51 kevin-laptop wpa_supplicant[1024]: CTRL-EVENT-SCAN-RESULTS 
Dec 22 21:11:04 kevin-laptop dhclient: DHCPREQUEST of 192.168.0.102 on wlan0 to 192.168.0.1 port 67
Dec 22 21:11:04 kevin-laptop dhclient: DHCPACK of 192.168.0.102 from 192.168.0.1
Dec 22 21:11:04 kevin-laptop dhclient: bound to 192.168.0.102 -- renewal in 4251 seconds.
Dec 22 21:11:04 kevin-laptop NetworkManager: <info>  DHCP: device wlan0 state changed reboot -> renew
Dec 22 21:11:04 kevin-laptop NetworkManager: <info>    address 192.168.0.102
Dec 22 21:11:04 kevin-laptop NetworkManager: <info>    prefix 24 (255.255.255.0)
Dec 22 21:11:04 kevin-laptop NetworkManager: <info>    gateway 192.168.0.1
Dec 22 21:11:04 kevin-laptop NetworkManager: <info>    nameserver '192.168.0.1'
Dec 22 21:11:51 kevin-laptop wpa_supplicant[1024]: CTRL-EVENT-SCAN-RESULTS 
Dec 22 21:13:51 kevin-laptop wpa_supplicant[1024]: CTRL-EVENT-SCAN-RESULTS 
Dec 22 21:14:09 kevin-laptop kernel: [13677.287627] SysRq : Changing Loglevel
Dec 22 21:14:09 kevin-laptop kernel: [13677.287640] Loglevel set to 5
Dec 22 21:14:11 kevin-laptop kernel: [13679.756685] SysRq : Changing Loglevel
Another problem: the sound has been sorta choppy. Not when I play music, but just the Ubuntu start-up theme music. Streaming music is fine online, so long as I let it download a bit before I play. Videos, on the other hand, don't work that way. Even if it's downloaded completely in the embedded window (ie. with flash/shockwave), it will not play smoothly. If I choose to save the file to my computer, then video usually plays fine, but there have been minor issues with this as well.

Sounds like a graphics card issue? Maybe. It's an Intel Corp. 82845G (Brookdale-G) GE Chipset Integrated Graphics Device (rev 03). Or is it a virtual memory issue? Perhaps. But I have no idea how to fix these issues since I'm not a techie or programmer-type person. I need really simple, clear beginner-talk to try and figure out and solve this problem. I found a thread about Vesa drivers, but how can I replace my Intel driver with a Vesa one? Is that even a good idea?

System info (what I know): Dell Inspiron 1100, kernel: 2.6.31-16-generic, 256 MB RAM

My apologies is this is something I should be reporting as a bug. I just don't know if it's a bug, or what the problem is at all.

Any help is appreciated!

---

### Post by Temposs on 2009-12-23
Are you using Compiz/Visual Effects on your Ubuntu?

EDIT: If you're not sure, check by going to System->Preferences->Appearance->Visual Effects and see if it's set at "None" or "Normal" or "Extra".

---

### Post by Naturally-Simple on 2009-12-23
Nope, no compiz or any special effects. It's set to None.

EDIT: I just looked at a thread about editing xorg.conf. I opened that file with gedit, and it's blank. Isn't there supposed to be something in that file? Maybe I found the wrong xorg.conf file (/etc/X11/xorg.conf)? Also in this thread was something about resolution, and when I looked at my appearance/visual settings, I can't choose any resolution.

---

### Post by jonamak on 2009-12-23
Just a week ago I installed ubuntu 9.10 on my PC( Fujitsu Siemens Scenic, Intel 82845G Graphics card)  for the first time. Initially was really overjoyed with the user friendliness and speed of  my desktop with Ubuntu, but alas it was short lived. Ironically I too face the same problem as described by [Kevin-dell1100]("http://ubuntuforums.org/member.php?u=974101"). The PC just hangs and I can only move mouse cursor. This occurs mostly when I view streaming videos in Firefox from Dailymotion. Also a few times my PC hung while some other application was running. Most irritatingly, I have to do hard reset and start all over again - several times a day !!!  Can anyone please help to solve this problem ? Has it something to do with Intel graphics card ?

---

### Post by Naturally-Simple on 2009-12-23
Jonamak, I found [this blog]("https://www.blogger.com/comment.g?blogID=14821769&postID=2859699115000218973&page=1&token=1261545796807_AIe9_BHGOSwAdHErPouE2TcfG6Xoze2AfDBvAQr5uz6tl6xeLABXM7OskX9HcOj5abW4RdkIC6uZ3thPsfzz2z9zITjmCS7VM4ZFIyEnHuoWOKrhm81nA232sNyRaokudzgB-zv0kyWyFB9r3kvuucinryWmJYSD0kNExDVKVPU8sRb2ONwyijm4a21tl2WC1JbAaV4_bfp_QzUNWsSNldPFtzuExbvBLAufn-AS937_wawkAb32Jx8") that looks promising for our problem (assuming our respective problems have the same cause), but I don't know what to do with the information that's given. I asked, but I'm doubtful I'll get a response. All it mentions is editing xorg.conf and changing the driver to a Vesa driver. Two problems with that for me are: a)my xorg.conf is blank, and I don't know if I should just copy and paste stuff into it, and b) I went to the Vesa website, but it doesn't mention which one could replace this Intel one. So I have no idea whether this is a safe thing to experiment with. If you're feeling brave, go ahead and try! Maybe I will too if I don't get any other help. I don't want to mess with things, but I suppose I don't have much to lose if I need to reinstall. Any other help out there?

---

### Post by Naturally-Simple on 2009-12-23
I've been told about [Bug #466310]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/466310") and [Bug #456902]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/456902") but nothing has been resolved, or if it has, no one has mentioned a fix yet. If anyone stumbles on this thread and takes a look at these bugs, could they offer a fix? Need to pool resources as much as possible! :)

---

### Post by jonamak on 2009-12-23
[Kevin-dell1100]("http://ubuntuforums.org/member.php?u=974101"), I had a look at blog mentioned by you. It seems someone have already encountered the same "our" problem with Intel 82845G chipset and solved it. But I am perplexed :confused: 
I can't find xorg.conf in my /etc/x11 !! Even the person who wrote the blog says he didnt find the xorg.conf  - but he wrote his own.
What should I do add a new xorg.conf if it was not at all existing in my ubuntu ?
Or do you think it is sensible to go back to an earlier version of ubuntu which is stable on Intel 82845G chipset ? and is this possible ?

---

### Post by Naturally-Simple on 2009-12-23
oops! :oops: I should've mentioned that I also don't have the xorg.conf file. Originally, when I looked for it, I couldn't find it, like you, so what I did was use a terminal and typed something involving gedit to open the file, which I guess simply creates a blank file if the filename doesn't yet exist.

I don't know if you should just copy/paste that blogger's xorg.conf file, mostly because in a later posting by him on one of those bug sites I mentioned in my last post, he mentions still having problems, and this is from maybe a week or two ago, whereas his blog post was from a month ago.

So I don't think that installing a Vesa driver and editing your xorg.conf file based off his edits are the solution.

Jonamak, did you check out those bug reports? I don't know exactly how they work, but I think it's good to at least post something to let others know you also have the same problem. The idea is that a fix will eventually get posted. But again, I hope a smart and Ubuntu-savvy person out there is reading this thread and knows about these bugs and can figure something out.

---

### Post by Naturally-Simple on 2009-12-24
Jonamak and whoever else stumbles on this thread, the blogger I mentioned earlier just contacted me and said the solution to my problems will be to use Ubuntu 9.04 Jaunty Jackalope. Perhaps he's right. I have been wondering whether a slightly older version of Ubuntu would be a better option, even if it'd be nice to run the newer 9.10. Maybe I shouldn't get so caught up in the hype of newness. :)

Click [here]("http://isohunt.com/torrent_details/77728753/ubuntu-9.04-desktop-i386.iso?tab=summary") for the page of the torrent I'm currently downloading (ubuntu-9.04-desktop-i386.iso is the file--if you have an AMD processor, you'll need a different file). I have a slow internet connection, so it'll take me until tomorrow. But once I've got the file, I'll see if I can partition my Dell, one part 9.10 and the other part 9.04 and see if that works. If not, I'll do a complete installation of 9.04 and see if I encounter the same problems I've been having with 9.10.

I'll post my findings on this thread.

---

### Post by ovid9 on 2009-12-24
I had the exact same problem on my wife's Dell Inspiron 1100 with 9.10 though it was Xubuntu the guts are the same.

I went back to 8.04 (only other thing i had lying about) and none of the freezing issues at all.

---

### Post by jonamak on 2009-12-24
I am too not willing to backtrack to the older version of ubuntu; liked 9.10 so much
the screen appearence, the speed and overall performance is quite pleasing . But I had a terrible time today - lost the count how many times i had to hard reboot the PC :-) 
So surely i am gonna give a try with ubuntu 9.04. 
Will keep posted with the outcome....

---

### Post by jonamak on 2009-12-26
so.. here is the latest from me ...
I downgraded my PC to ubuntu 9.04.. and it's stable so far !!!
It's more than a day the PC is operating uninterrupted.. so I am quite relieved :P
Once the installation is complete, the "Update Manager" suggests some "Security" and "Recommended". I allowed only "Security" updates. In the "Recommended" list, I found something related to Intel 825*** Graphics driver and I am hesitant to perform this update. Has anyone tried or done this update ? and Is the system stable afterwards ?

---

### Post by Naturally-Simple on 2009-12-26
Jonamak, yeah, so far for me 9.04 has been fine. I even had a moment when Firefox was not responding, but I just right clicked on the bottom bar and opted to close it, and it worked and reloaded just fine.

And, yeah, man, what to do with that update file... I just clicked update without looking anything over, which is maybe not what I should do, but I figure the updates shouldn't harm anything. But right now, there is at the bottom of my Recommended list the following:

Xserver-org-video-intel:
x.Org X server -- Intel i8xx, i9xx display driver

I don't know what this is, and I suppose for people like you and me who have had problems with our graphics card, it makes sense to be leery of such updates... So I don't know.

I actually need to get rid of the 9.10/9.04 partition, because I set 9.04 too low and need more space for the updates, so I'm going to do a full re-install of 9.04, and I figure I may as well update everything on that list.

Can anyone who reads this comment on whether it's good to just automatically update everything Update Manager lists?

---

### Post by jonamak on 2009-12-26
some more on the video performance of ubuntu 9.04: it's not fully perfect. Streaming videos are better watching in small browser window, but in full screen view they tend to be a bit slower - and this makes videos as if in slow motion and very jerky. can anyone suggest a solution for this ?

---

### Post by Naturally-Simple on 2009-12-28
My only issue right now with 9.04 is using the same wireless internet USB stick (Belkin 802.11G, model: F5D7050) which was working just fine in 9.10. The signal strength is really weak with 9.04, unless I'm sitting right next to the router. I've looked at a fix [here]("http://ubuntuforums.org/showthread.php?p=7605785"), but having issues with following this process (also feel like it's above my head since I'm not Linux-savvy in the slightest). 

Sigh... 

If I may vent briefly: I thought Ubuntu/Linux, in general, was supposed to be more user-friendly, easier to troubleshoot, etc. etc... All it's been, since the first time it froze, is a nuissance. If anything, it has pushed me in the direction of getting a Mac, even if I hate all of those trendy i-hipsters. Maybe I'm just jealous.

Anyway, those are my two cents. I'll still try to figure this out. Maybe I'll look at Ubuntu 8.04, which Ovid9 said works just fine.

Ovid9, what can you tell me about how video streaming or wireless connections work with that setup?

---

### Post by Temposs on 2009-12-28
> If I may vent briefly: I thought Ubuntu/Linux, in general, was supposed to be more user-friendly, easier to troubleshoot, etc. etc... All it's been, since the first time it froze, is a nuissance. If anything, it has pushed me in the direction of getting a Mac, even if I hate all of those trendy i-hipsters. Maybe I'm just jealous.

Anyway, those are my two cents. I'll still try to figure this out. Maybe I'll look at Ubuntu 8.04, which Ovid9 said works just fine.

Ovid9, what can you tell me about how video streaming or wireless connections work with that setup?

The reason Macs are easier is that all the hardware and software is one package. Likewise, with the companies that build Windows machines, you get, well, machines made for Windows, which is likely what you have.

If you want to for the most part eliminate the hassle of troubleshooting your hardware compatibility issues, then you should get a computer built for...you guessed it, Ubuntu!

There are three companies that build systems for Ubuntu and preload them with Ubuntu. Here are a few links:

[http://www.dell.com/ubuntu](http://www.dell.com/ubuntu)
[http://www.system76.com/](http://www.system76.com/)
[http://www.zareason.com/](http://www.zareason.com/)

Rather than buying a Mac, if you want your hardware to work right with your OS of choice, then buy a machine that's made for it, instead of trying to fit Ubuntu onto a machine built for Windows.

P.S.: As you can see in my sig, I have a machine from System76. It's very solid and has great support, and even its own section in the Ubuntu Forums.

---

### Post by Naturally-Simple on 2009-12-29
Temposs, with all due respect, and I really mean that, I don't understand your position. Yes, I can see how a machine made specifically for Ubuntu will work better with Ubuntu (duh!) but correct me if I'm wrong, but part of being "open-source" and the basic system behind a Linux-based OS is flexibility and customization. That is, if I really knew what I was doing, programming-wise, I would be able to customize my Linux OS specifically for my machine. And again, correct me if I'm wrong, but getting a machine built specifically for Ubuntu doesn't mean using special hardware; it's just getting programmers/testers at Dell or System76 or wherever else to make sure their machine will work with the chosen OS.

Perhaps I've been misunderstanding this whole open-source idea all along?

I have a Dell, by the way, and like your system, there is also an entire section devoted to Dell in the Ubuntu forums. I don't think the fact that a system has it's own dedicated section means it's a superior machine. ;)

I'm not loyal to Dell. In fact, I think Dell sucks. The only reason I'm using this laptop is because it was sitting around and collecting dust, and I read on various websites that a nice way to breathe new life into older, unused laptops is by installing Ubuntu.

My guess is that an older version will work just fine on my Dell Inspiron 1100. I was rather upset before when I wrote my last post. I didn't mean to bash Ubuntu. I'm currently in problem-solving mode, and I want some version of Ubuntu to work. But yeah, I'm up for the idea of looking at a pre-installed Ubuntu machine. I just don't think that I should HAVE to, ya know? Besides, there's so much computer waste out there... it just doesn't feel right to me.

So I'll try to make do with what I've got and try not to be negative! haha! :) The worst case scenerio is that I buy a pre-installed Ubuntu machine. Never actually heard of System76 or Zareason before, so I might go that direction. Thanks for the advice!

Update on my 9.04: I've done a full installation, and am waiting on Update Manager to finish. I have a sloooowww internet connection here. So far, there were three boots that gave me blank screens, two of which I was able to enter a terminal and type sudo reboot, and then it rebooted without a problem. We'll see if it does this after the updates are all installed.

---

### Post by candtalan on 2009-12-29
> **Temposs said:**
>  There are three companies that build systems for Ubuntu and preload them with Ubuntu. Here are a few links:
[http://www.dell.com/ubuntu](http://www.dell.com/ubuntu)
[http://www.system76.com/](http://www.system76.com/)
[http://www.zareason.com/](http://www.zareason.com/) 

In UK I know of Linux Emporium and some of my friends have purchsased from them with excellent results
[http://www.linuxemporium.co.uk/](http://www.linuxemporium.co.uk/)

---

### Post by candtalan on 2009-12-29
> **Kevin-dell1100 said:**
>  That is, if I really knew what I was doing, programming-wise, I would be able to customize my Linux OS specifically for my machine. And again, correct me if I'm wrong, but getting a machine built specifically for Ubuntu doesn't mean using special hardware; it's just getting programmers/testers at Dell or System76 or wherever else to make sure their machine will work with the chosen OS.

As I understand it, yes in theory you could do anything with your chosen hardware if you had enough knowledge. However, in practice, the hardware or some parts of it, sometimes does not have useful information available from the manufacturers. Either they play golf with Microsoft or simply do not care to reveal some hardware information. In such cases it is a very difficult task though maybe not impossible to create drivers for GNU/Linux for those hardware aspects.
So in practice there are some hardware things which in a practical sense, cannot be usefully used just as you wish.

Some manufacturers are more GNU/Linux friendly than others, and so companies like Linux Emporium can make useful choices with desktops and laptops, and it is much easier for the end user. Although it is likely that you can get the same information they have and use if you wish.

I am careful to only spend money and effort towards companies which make free software possible. 
hth

---

### Post by glubbdrubb on 2009-12-29
Kevin-dell1100 upgrading your RAM will probably help improve your general system performance no matter what kernal/drivers you are running.

However I realize that it may be difficult to do so in your situation.

---

### Post by Temposs on 2009-12-29
Kevin-dell1100: Simply having a Dell does not make it built for Ubuntu. If your computer came preloaded with Windows, it was put together with optimization for Windows in mind, and Dell includes a bunch of custom-made drivers and such to make sure everything works with Windows out of the box when you get your computer. So, just having a Dell does not help. In fact, the reason for Dell having their section on Ubuntu Forums(like System76) is to support those systems they've preloaded with Ubuntu, not just any Dell that you may have. Dell releases their own versions of Ubuntu customized for these systems, and works with hardware manufacturers to make sure they're offering hardware with open specs and that have compatibility with Linux.

In many cases, yes, you can get your computer to work completely with Ubuntu, but a lot of hardware doesn't have open specs. This makes it extraordinarily difficult, if not impossible in some cases, to create a driver for that hardware, even if you are the theoretical elite programmer. You simply can't write code for a piece of hardware if you don't know what the hardware is doing.

Being part of the open source community means supporting hardware that has open specs or that was made to work well with open source software(as candtalan stated). Buying from one of those companies accomplishes that, as these companies will tell hardware manufacturers that they need something that works with Ubuntu, and preferably make it have open specs, and the hardware manufacturers will listen, because they are the customer. Besides that, folks working for these system builders like Dell or System76 contribute driver code and bug fixes to critical software that improves the operating system for everyone. And the more people buy Ubuntu preloaded machines the more sway those system builders have versus the ones that sell Windows, or MacOS.

The reason Ubuntu and Linux in general has a focus on making their OS work on any system is out of necessity that historically, consumer-grade computer systems have not been developed with Linux in mind at all. It's an adaptation but it is not the ideal. Now that there are some companies that can survive building and supporting Ubuntu-optimized systems, we should support those companies in order to increase hardware compatibility with our OS of choice, which helps everyone in the open source community, in the end.

---

### Post by woodmaster on 2009-12-29
same issues Dell Dimension 2400...going to wipe and install 8.04LTR...can't wait to buy a System76 PC!  I upgraded my RAM to 2GB and it helped a lot but still random freezes...I think I got a sound card(SB Live card) driver issue but unsure...the log file entries are inconsistent at best on what the problem is...the last was:
Dec 29 15:28:06 Sam-Jenn rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="699" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Dec 29 16:13:13 Sam-Jenn kernel: [ 4120.580862] SysRq : Keyboard mode set to system default
Dec 29 16:13:13 Sam-Jenn kernel: Kernel logging (proc) stopped.
Dec 29 16:13:13 Sam-Jenn kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Dec 29 16:13:13 Sam-Jenn rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="2408" x-info="http://www.rsyslog.com"] (re)start

Previously most had been about suppressed pulseaudio events

---

### Post by bingobingo on 2010-01-09
It is not a graphic issue it is a kernal issue,  I am constantly getting freezing. I do not know if it is a upgrade issue vs clean install. I do not have cd for a clean install. I am going back to 9.04, but I hate that because of Ubuntu will not support it for long. At least I have the cd and do not need to download it. Upgrades never seem to work for me.

---

### Post by candtalan on 2010-01-10
> **bingobingo said:**
> I am going back to 9.04, but I hate that because of Ubuntu will not support it for long. At least I have the cd and do not need to download it. Upgrades never seem to work for me.
Upgrades have been ok for me, although I have had a problem or two with 9.10 on one machine, but another machine has been ok.

9.04 will be supported for 18 months, which is not bad. And betweeen now and then, the long term support (LTS) version 10.04 will be released, hopefully with an emphasis upon stability.

I am *still* using the LTS version 8.04.3, which is stable, and this will be supported until 2011. Although I always try the latest releases too.
hth

---

### Post by jonamak on 2010-02-11
looks like my woes are finally over.
since last 4 days my computer won't freeze :D
here's the link: [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)
ps: I have ubuntu 9.04 running on P4 + Intel  82845G Integrated Graphics Device

---

### Post by sleepee on 2010-02-11
> **bingobingo said:**
> It is not a graphic issue it is a kernal issue,  I am constantly getting freezing. I do not know if it is a upgrade issue vs clean install. I do not have cd for a clean install. I am going back to 9.04, but I hate that because of Ubuntu will not support it for long. At least I have the cd and do not need to download it. Upgrades never seem to work for me.

i think you may be right, because i see most people on this thread have dells.  but i have an hp with nvidia graphics and i still have the same problem.
but now that i think of it, i only got this freezing problem after i upgraded my kernel.
i always save the last working kernel i had, so i'm going to go back and boot into 2.6.31-17 and see what happens...

---

### Post by vikramdawar on 2010-03-07
) just uninsall ubuntu 9.10 format the drive u wanna put it into. then make a fresh install
2) When the installation is complete it asks to update the system.
3) when u update then update every thing except all mozilla updates, linux image generic 2.6.31.14 comes when u install it from the cd. so let this image be and dont intall when updateing the 2.6.31.19. and ofcourse dont intall the linux headers for 2.6.31.19 image..

I tried it for a few days now ,,, think its working properly at the moment.. been 3 days now..

Hope this should solve the problem. cuase there must be a bug in 2.6.31.19 generic image and mozilla updates.... enjoy
u can try the new one 2.6.31.20 image;):)
 

Vikram

---

