---
title: "3C900B-TPO crashing?"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by Balaam's Miracle on 2007-04-21
In my PC i have 2 NICs, on eth0 i have a built-in NIC of an unknown brand/type and on eth1 i have a 3Com 3C900b-TPO.
Eth1 connect to the internet, eth0 is the LAN.

The problem is with eth1. Since my upgrade to Feisty "the internet" stops responding.
At first i thought it was a DNS issue, but discarded that idea after i've found that even IP addresses outside my LAN couldn't be pinged at that time.

I've tried restarting networking by executing a [FONT="Courier New"]/etc/init.d/networking restart[/FONT] but that didn't help.

Right now, all that seems to help is restarting the PC but that is hardly a solution to the problem.

I've found the following in /var/log/syslog:
```

[ 2442.499383] NETDEV WATCHDOG: eth1: transmit timed out
[ 2442.499396] eth1: transmit timed out, tx_status 00 status 8601.
[ 2442.499405]   diagnostics: net 0cc8 media 8880 dma 0000003a fifo 8800
[ 2442.499410] eth1: Interrupt posted but not delivered -- IRQ blocked by another device?
[ 2442.499517]   Flags; bus-master 1, dirty 169764(4) current 169764(4)
[ 2442.499521]   Transmit list 00000000 vs. dfa4e480.
[ 2442.499526]   0: @dfa4e200  length 8000002a status 0001002a
[ 2442.499529]   1: @dfa4e2a0  length 8000002a status 0001002a
[ 2442.499533]   2: @dfa4e340  length 8000002a status 8001002a
[ 2442.499536]   3: @dfa4e3e0  length 8000002a status 8001002a
[ 2442.499539]   4: @dfa4e480  length 80000036 status 00010036
[ 2442.499543]   5: @dfa4e520  length 8000004a status 0001004a
[ 2442.499546]   6: @dfa4e5c0  length 8000004a status 0001004a
[ 2442.499549]   7: @dfa4e660  length 8000002a status 0001002a
[ 2442.499552]   8: @dfa4e700  length 8000002a status 0001002a
[ 2442.499555]   9: @dfa4e7a0  length 8000002a status 0001002a
[ 2442.499559]   10: @dfa4e840  length 8000002a status 0001002a
[ 2442.499562]   11: @dfa4e8e0  length 8000002a status 0001002a
[ 2442.499566]   12: @dfa4e980  length 8000002a status 0001002a
[ 2442.499569]   13: @dfa4ea20  length 8000002a status 0001002a
[ 2442.499572]   14: @dfa4eac0  length 8000002a status 0001002a
[ 2442.499576]   15: @dfa4eb60  length 8000002a status 0001002a
[ 2442.499580] eth1: Resetting the Tx ring pointer.
```

The times of these entries coincide with the times that the NIC stops responding.

Now for my questions:
1: Is there a way to restart the NIC (not just the networking!) without rebooting the system?
2: Is there a more permanent solution known for this problem?

I would like to emphasize that this problem started after my upgrade to Feisty yesterday. Before that, there was no problem at all.

---

### Post by Calavera07 on 2007-04-21
Same problem, with 3c905C-TX/TX-M [Tornado]. Product id: 37376 (0x9200)

I also have two ethernet interfaces, and the problem is with eth1, which is connected to the internet.

Please, help!!

---

### Post by Balaam's Miracle on 2007-04-21
Although it's still too early to tell for sure, it does look like it could be a problem with the 3c90x drivers.
I wonder if there is a way to tell for sure, besides waiting for more reports...

---

### Post by Calavera07 on 2007-04-22
My computer loads the 3c59x.ko module for the network card.

---

### Post by Balaam's Miracle on 2007-04-22
> **Calavera07 said:**
> My computer loads the 3c59x.ko module for the network card.

How can i check which one it loads on my box?

P.S. The NIC has survived the night somehow. But i'm still wary...

---

### Post by Calavera07 on 2007-04-22
> **Balaam's Miracle said:**
> How can i check which one it loads on my box?

P.S. The NIC has survived the night somehow. But i'm still wary...

I used ```
lsmod | grep 3c
```

---

### Post by Balaam's Miracle on 2007-04-22
> **Calavera07 said:**
> I used ```
lsmod | grep 3c
```

Allright, my machine uses that same driver. So no difference there.

Someone gave me the tip to try the following:
[INDENT][FONT="Courier New"]modprobe -r 3c59x
modprobe[/FONT][/INDENT]
However, that did not work for me and i still had to reset my machine when the NIC stopped working again.
I'm just mentioning it in case it does work for other people.

Now i wonder, is the driver at fault or something else that's attached to the kernel?

---

### Post by Balaam's Miracle on 2007-04-24
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/109629](https://bugs.launchpad.net/ubuntu/+bug/109629) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've restarted into an older kernel (2.6.17-11) 24 hours ago, and i now appear to have a stable internet connection but of course that's not a solution, just a workaround.

Oh, i've forgot: bug reported as [https://bugs.launchpad.net/ubuntu/+bug/109629](https://bugs.launchpad.net/ubuntu/+bug/109629)

---

### Post by Ph0B1uS on 2007-04-28
A late reply perhaps but I'm having the same problems as previously described in this thread.

I've got a 3c905 and an integraded nic which is disabled so i've only got one active interface.
My problems seems to be related to sustained download rates above 1,1Mb/s.

I can't use X because i'm on a nvidia card and can't compile the drivers because of the differing gcc-versions edgy <-> fiesty.

---

### Post by Balaam's Miracle on 2007-05-03
> **Ph0B1uS said:**
> A late reply perhaps but I'm having the same problems as previously described in this thread.

I've got a 3c905 and an integraded nic which is disabled so i've only got one active interface.
My problems seems to be related to sustained download rates above 1,1Mb/s.

I can't use X because i'm on a nvidia card and can't compile the drivers because of the differing gcc-versions edgy <-> fiesty.

Until we've got (or found) a solution to this problem, i am just using the nv drivers instead of the nVidia ones. 
I'm no gamer and don't really need 3D acceleration anyway.

Interestingly, you too have 2 NICs in your machine, so it now looks as if that is what causes the problem, even though in your case the second NIC is disabled.
Looks like we are getting somewhere. Let's see what we have so far:

- 3Com PCI NICs lock up after a certain period of substantial data traffic.
- Problem occurs *only* with kernel version 2.6.20 so it must be related to that.
- So far, all that reported this problem have 2 NICs in their machine.
- Disabling one of the two NICs makes no difference. Problem persists.

Did i miss anything? I have the feeling i did...

---

### Post by Ph0B1uS on 2007-05-04
> **Balaam's Miracle said:**
> Until we've got (or found) a solution to this problem, i am just using the nv drivers instead of the nVidia ones. 
I'm no gamer and don't really need 3D acceleration anyway.

Interestingly, you too have 2 NICs in your machine, so it now looks as if that is what causes the problem, even though in your case the second NIC is disabled.
Looks like we are getting somewhere. Let's see what we have so far:

- 3Com PCI NICs lock up after a certain period of substantial data traffic.
- Problem occurs *only* with kernel version 2.6.20 so it must be related to that.
- So far, all that reported this problem have 2 NICs in their machine.
- Disabling one of the two NICs makes no difference. Problem persists.

Did i miss anything? I have the feeling i did...

My integrated nic is disabled in the bios so it doesn't show in linux.
The problem is definitly related to the 3c905-driver and the 2.6.20-kernel.

The bug is reported but nothing's happened to its status or anything yet.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109629](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109629)

I can't use the nv-driver because the fan on my graphics card is at its max all the time without the 
closed source-driver and that noise is reaaally loud on nvidas stock cooler I kid you not.

---

### Post by Balaam's Miracle on 2007-05-04
> **Ph0B1uS said:**
> My integrated nic is disabled in the bios so it doesn't show in linux.
The problem is definitly related to the 3c905-driver and the 2.6.20-kernel.

I used to work in a computer shop, building computers.
Someone ordered a PC and opted for another soundcard than the standard onboard thing so i've disabled the onboard beastie and went ahead with installing the PCI soundcard.
I blew 3 PCI soundcards before i realized that although disabled in the BIOS, the onboard soundcard still affected the entire system.

My point is that even though you've disabled the onboard NIC and Linux ignores it (i don't think it can't see it), you still have 2 NICs in your machine and the other one still has an effect on your system.

> The bug is reported but nothing's happened to its status or anything yet.

Give it some time. This kind of bug will not get the critical status because obviously, we can still get on the internet.
I'm sure there are other, more critical bugs to be solved and even if there weren't, it would only be logical to deal with bugs on a FIFO basis.
I think it will take weeks, if not months, before this bug will be solved, though i hope it will be sooner.

> I can't use the nv-driver because the fan on my graphics card is at its max all the time without the 
closed source-driver and that noise is reaaally loud on nvidas stock cooler I kid you not.

That sux0rs. and how about the SVGA/VESA driver?

---

### Post by Ph0B1uS on 2007-05-05
> **Balaam's Miracle said:**
> I used to work in a computer shop, building computers.
Someone ordered a PC and opted for another soundcard than the standard onboard thing so i've disabled the onboard beastie and went ahead with installing the PCI soundcard.
I blew 3 PCI soundcards before i realized that although disabled in the BIOS, the onboard soundcard still affected the entire system.

My point is that even though you've disabled the onboard NIC and Linux ignores it (i don't think it can't see it), you still have 2 NICs in your machine and the other one still has an effect on your system.



Give it some time. This kind of bug will not get the critical status because obviously, we can still get on the internet.
I'm sure there are other, more critical bugs to be solved and even if there weren't, it would only be logical to deal with bugs on a FIFO basis.
I think it will take weeks, if not months, before this bug will be solved, though i hope it will be sooner.



That sux0rs. and how about the SVGA/VESA driver?

Interesting point about the disabled nic, I do recall being able to detect disabled hardware now that you mention it.

Those drivers are the same, I need the nvidia bin-drivers to control my fan.
Nothing else seems to be able to handle it.

---

### Post by Balaam's Miracle on 2007-05-05
> **Ph0B1uS said:**
> Those drivers are the same, I need the nvidia bin-drivers to control my fan.
Nothing else seems to be able to handle it.

Hmm... And it's impossible to install older nVidia drivers when running kernel 2.6.17 ?

Oh, an update: I didn't know that it was possible for bug reporters to cange the status of a bug and/or assign a bug to a person or team.
So just now, i did change the status to confirmed (since a total of 3 people reported it) and assigned it to the ubuntu-core-dev team.
Had i known this sooner, i would have changed the status a long time ago....

---

### Post by Ph0B1uS on 2007-05-05
> **Balaam's Miracle said:**
> Hmm... And it's impossible to install older nVidia drivers when running kernel 2.6.17 ?

Oh, an update: I didn't know that it was possible for bug reporters to cange the status of a bug and/or assign a bug to a person or team.
So just now, i did change the status to confirmed (since a total of 3 people reported it) and assigned it to the ubuntu-core-dev team.
Had i known this sooner, i would have changed the status a long time ago....

Can't compile the module as the GCC versions differ, 6.10 runs one version and 7.04 another.

Ah good thing you changed the status and assignment of the bug, hopefully that'll set things in motion.

---

### Post by RichJacot on 2007-05-16
Just posting that I have the same issue.  

 lsmod | grep 3c
3c59x                  46632  0 
mii                     6528  1 3c59x


I just finished a fresh install of Feisty.  Is there a workaround until this bug is fixed?


Rich

---

### Post by Ph0B1uS on 2007-05-16
> **RichJacot said:**
> Just posting that I have the same issue.  

 lsmod | grep 3c
3c59x                  46632  0 
mii                     6528  1 3c59x


I just finished a fresh install of Feisty.  Is there a workaround until this bug is fixed?


Rich

The easiest way around this is to compile your own kernel.

---

### Post by RichJacot on 2007-05-16
What about the stuff about Nvidia I'm seeing in regards to recompiling?  I do have an Nvidia card. (ignore my signature line, that's my other system)

If having an Nvidia card isn't an issue do you have a link on how to do it?

I found one, but I've never done it before so I'm a little apprehensive.

[http://azio.org/2006/10/18/howto-compiling-a-kernel-on-debian/]("http://azio.org/2006/10/18/howto-compiling-a-kernel-on-debian/")

Thanks

---

### Post by Ph0B1uS on 2007-05-17
> **RichJacot said:**
> What about the stuff about Nvidia I'm seeing in regards to recompiling?  I do have an Nvidia card. (ignore my signature line, that's my other system)

If having an Nvidia card isn't an issue do you have a link on how to do it?

I found one, but I've never done it before so I'm a little apprehensive.

[http://azio.org/2006/10/18/howto-compiling-a-kernel-on-debian/]("http://azio.org/2006/10/18/howto-compiling-a-kernel-on-debian/")

Thanks

I know it says it's for pendrives but I'm pretty sure it works for regular systems too.
Note that this is for the Nvidia proprietary driver. There is one in the ubuntu repos that you can use
and if you've got no noisy fan that's uncontrollable other than via the mentioned driver then you'd probably
want to use the one included with ubuntu.

[http://www.pendrivelinux.com/2007/02/23/installing-proprietary-video-drivers-for-ubuntu/](http://www.pendrivelinux.com/2007/02/23/installing-proprietary-video-drivers-for-ubuntu/)

---

### Post by FarmerDave on 2007-06-26
> **Balaam's Miracle said:**
> 
Give it some time. This kind of bug will not get the critical status because obviously, we can still get on the internet.


Not me;  I've got two 3c59x's in my module list, and I get the IRQ collision *during boot*, which means I never get a chance to connect to anything.  So, it may not necessarily have to do with high traffic.

Just upgraded to Feisty 7.04 last night, and it's a good thing I've got this XP laptop sitting around.

---

### Post by FarmerDave on 2007-06-26
Just for the hell of it, I tried the suggestion in [http://ubuntuforums.org/showpost.php?p=1667545&postcount=4](http://ubuntuforums.org/showpost.php?p=1667545&postcount=4) and added "irqpoll" to the kernel parameters in my /boot/grub/menu.lst file for the 2.6.20 kernel, and it came right up!  As I said in my previous post, my eth0 was usually hosed by the time the system was done booting, so this is a big improvement.  Remains to be seen whether or not it can take some real traffic.  And whether or not "irqpoll" has bad side-effects somewhere else.

---

### Post by Balaam's Miracle on 2007-07-07
The following WORKAROUND works for me. I've performed these steps 3 days ago and my machine have been running non-stop, using the latest Feisty kernel (2.6.20-16-386):

From a terminal, open menu.lst with:
[FONT="Courier New"]sudo nano /boot/grub/menu.lst[/FONT]

Using Ctrl+W,  Find the line that says: 
[FONT="Courier New"]# defoptions=quiet splash [/FONT]
and change it to:
[FONT="Courier New"]# defoptions=quiet splash irqpoll[/FONT]

Close nano with Ctrl+X and confirm saving of file.

Next, execute:
[FONT="Courier New"]sudo update-grub[/FONT]

After a reboot, both NICs worked for me and kept working.
However, and i want to stress this: This is only a workaround, not a fix since a fix would make this workaround redundant.
I hope this works for other people as well.

Good luck everyone!

---

### Post by Balaam's Miracle on 2007-07-07
Sorry FarmerDave, didn't see your post before i posted mine....

---

