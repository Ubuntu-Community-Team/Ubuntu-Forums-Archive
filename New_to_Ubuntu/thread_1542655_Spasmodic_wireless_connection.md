---
title: "Spasmodic wireless connection"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by bally_bal on 2010-07-30
[SIZE=3]I'm a very new Ubuntu user having just installed Ubuntu10.04 on my laptop which previously ran Windows Vista followed by an unsuccessful Win 7 upgrade. I enjoy exploring new software but I am not a tech head so I would appreciate a simple explanation if that is possible.
I did a clean install of Ubuntu because of major issues with Windows. Wireless connectivity was a problem with Windows 7 and it still appears to be now. Every boot up is different - sometimes I can connect wirelessly and other times not. There appears to be 2 network adapters installed at the moment - that is how I'm on the net (see attached screenshot) but on the last bootup, there was only one (Atheros) and then I could only connect with a wired connection. In plain English, is there anyone who has any idea why this is happening and what can I do about it? [/SIZE]

---

### Post by jtarin on 2010-07-30
Have you setup any connections, at all, in [Network Manager]("http://ubuntuguide.org/wiki/Ubuntu:Lucid#Networking")? 
Issue the command ifconfig -a in a terminal and post the output.

Some like [WICD ]("http://wicd.sourceforge.net/")to set up their connections.

Tell us how you normally connect.

---

### Post by bally_bal on 2010-07-31
[SIZE=3]When I first installed Ubuntu, I  was only able to connect if I used a hard wired connection. After a few more  bootups, the wireless connection suddenly appeared in the Network  Manager and after entering our network's name & password, I was  connected.  Since my post a few hours ago, I have shutdown and re-booted  on several occasions, some with wireless connectivity and some without.  This is exactly what used to happen when Win 7 was on this laptop which  makes me think it is a hardware issue and not an OS one. The wireless is  working at the moment and attached is the output of the ifconfig -a command. 
The next time I boot up and the wireless connection is missing, I'll issue the same command and post it via my PC if that's of any use. Thanks for your help.
[/SIZE]

---

### Post by jtarin on 2010-07-31
I'm going to link you to [this ]("https://lists.ubuntu.com/archives/kernel-team/2010-March/009475.html")which gives some insight into the problem. It seems to be a suspend, resume problem rather than what you would typically think directly as a hardware problem.At the very least Ubuntu is working on it. Any word from Win7? :) All I can say is do the best you can with your working connections and watch for a kernel update on this.As a further note Intel is aware there is a problem on disconnects with this chip.

---

### Post by bally_bal on 2010-08-01
[FONT=Verdana][SIZE=3]I issued the command ifconfig -a today when the wireless connection didn't start and that screenshot is attached. I had to boot up 4 times before the wireless finally kicked in but at least it eventually did....... at least it only takes 15 secs to boot up.[/SIZE][/FONT]


[FONT=Verdana][SIZE=3]Thanks very  much for the link to the website ..... very interesting especially as the Intel Corp PRO/Wireless 3945ABG tops the list of problem Intel wireless adapters. Wouldn't you have thought that someone at Asus or one of a dozen or so "experts" could have told me that months ago after my initial inquiries! Ultimately my laptop which was just out of warranty, spent 3 weeks at a local IT doctor. $350 later it was pronounced "cured" as they had found a new driver for it but in fact the "cure" was only temporary and the laptop reverted back to its old ways of spasmodic wireless connectivity. To make matters worse, if I updated Windows, all I got was the dreaded BSOD. That was why I abandoned Windows and tried Ubuntu which I must say I am quite enjoying.  Being a newcomer, I really appreciate your time and patience with me.[/SIZE][/FONT]:razz:

---

### Post by jtarin on 2010-08-01
In addition I did come across a mention of updating the bios as a possible solution to this....someone seems to have had some luck. I can't vouch for it. There is the PCI wireless card route if you want trouble free wireless. I would choose one that has a high success rate. If you go that route remeber to disable the onboard one in the bios. I wish I could be more help but it seems the cards are stacked.

Here's a [method]("http://dilationtime.wordpress.com/2008/06/07/linux-automating-wireless-connection/") that foregoes Network Manager during the boot process....worth a shot.

---

