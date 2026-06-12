---
title: "Problems with Realtek RTL8139/810x Family Fast Ethernet NIC"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by Jormanks on 2007-03-14
Well, here's the thing:** I don't have internet in ubuntu**. Currently I'm dual booting with winxp, and do my internet stuff with win.... I would love to improve my ubuntu scenario, I would love to install and work on it. I would love any help, really.

By the way: there's some posts about netcard issues like this one:
[http://ubuntuforums.org/showpost.php?p=1102399&postcount=29](http://ubuntuforums.org/showpost.php?p=1102399&postcount=29)

But... really, I can't make it work. I also read that with synaptic I can remove the network manager... I'm afraid to do that...

My board is a MSI K8MM-V, AMD Sempron 2800+
1 Gb Ram
220 GB HD
2 netcards: the board one (VIA fast ethernet compatible) and the Realtek RTL8139/810x Family Fast Ethernet NIC

And it says that the Realtek one is supported by ubuntu...

What can i do?

Thanks even for reading it.

Seriously.

---

### Post by handaxe on 2007-03-15
outputs of sudo ifconfig and sudo lshw -C network please whilst clipped in.

HA

---

### Post by rclobes on 2007-10-10
I HAD this exact same problem!  I have an emachines T2615 that had Windows XP on it for a few years.  Recently, I created a dual boot system and was able to install Ubuntu v 6.06.1 on it and had it working perfectly for a few days.  Unfortunately, The WinXP side became corrupted beyond repair and wouldn't even boot up.  (that's a long story which involves the number one daughter)  Anyhow, I tried several techniques to repair the Master Boot Record to no avail.  I finally decided to rebuild the hard drive from scratch.  I got out my copy of Windows XP upgrade and started over.  I installed Windows XP and then started the long process of downloading the updates and updates of updates.

I finally got all the critical updates and not so critical updates installed and saw that there were 4 driver updates...one of which was for the network card.  I installed all of these.

I finally got the XP side working to my satisfaction and turned my attention to the Ubuntu side.  I installed v7.04 and I noticed that I couldn't get online.  The ethernet card was displayed in the device manager (System | Administration | Device Manager).  No lights on the router or at the ethernet port.  It was completely dead.

I tried re-installing Ubuntu v6.06.1.  That is what I originally used.  Still had the same network issue.  This was completely frustrating as I just had it working last week!  What Changed?!?

I finally decided to take a look over on the Windows XP side again.  Under the Device Mangler, the Network Card's driver was "Realtek RTL8139/810x Family Fast Ethernet NIC"  Bringing up the properties gives you access to the Driver tab.  I clicked on the Roll Back to Previous Driver button and it came back with a "TE100-PCBUSR 32-Bit Cardbus PC Card"  Then, for good measure, I looked under the "Power Management" tab and unchecked the "Allow the computer to turn off this device to save power."

Went back over to the Ubuntu side and I had a glorious working internet connection!  KEWL!  I then tried re-installing the Realtek driver under Windows XP, but left the "Allow computer...save power" box unchecked.  My ethernet problem came back in Ubuntu.  Guess the check box is not the problem.  I think the Realtek driver for Windows XP is the issue.  Maybe there is a new driver for Linux, but I am too new at this Ubuntu stuff to know how to get it and install it.

For now, The Realtek driver on the Windows XP side is the "TE100-PCBUSR 32-Bit Cardbus PC Card" driver and I can surf the net in Windows XP with no problems.  The Ubuntu side works just fine also so I am content to leave well enough alone for now.

Hope this helps...

Sincerely:

Ron

---

### Post by dopievoli on 2007-10-10
> **rclobes said:**
> I HAD this exact same problem!  I have an emachines T2615 that had Windows XP on it for a few years.  Recently, I created a dual boot system and was able to install Ubuntu v 6.06.1 on it and had it working perfectly for a few days.  Unfortunately, The WinXP side became corrupted beyond repair and wouldn't even boot up.  (that's a long story which involves the number one daughter)  Anyhow, I tried several techniques to repair the Master Boot Record to no avail.  I finally decided to rebuild the hard drive from scratch.  I got out my copy of Windows XP upgrade and started over.  I installed Windows XP and then started the long process of downloading the updates and updates of updates.

I finally got all the critical updates and not so critical updates installed and saw that there were 4 driver updates...one of which was for the network card.  I installed all of these.

I finally got the XP side working to my satisfaction and turned my attention to the Ubuntu side.  I installed v7.04 and I noticed that I couldn't get online.  The ethernet card was displayed in the device manager (System | Administration | Device Manager).  No lights on the router or at the ethernet port.  It was completely dead.

I tried re-installing Ubuntu v6.06.1.  That is what I originally used.  Still had the same network issue.  This was completely frustrating as I just had it working last week!  What Changed?!?

I finally decided to take a look over on the Windows XP side again.  Under the Device Mangler, the Network Card's driver was "Realtek RTL8139/810x Family Fast Ethernet NIC"  Bringing up the properties gives you access to the Driver tab.  I clicked on the Roll Back to Previous Driver button and it came back with a "TE100-PCBUSR 32-Bit Cardbus PC Card"  Then, for good measure, I looked under the "Power Management" tab and unchecked the "Allow the computer to turn off this device to save power."

Went back over to the Ubuntu side and I had a glorious working internet connection!  KEWL!  I then tried re-installing the Realtek driver under Windows XP, but left the "Allow computer...save power" box unchecked.  My ethernet problem came back in Ubuntu.  Guess the check box is not the problem.  I think the Realtek driver for Windows XP is the issue.  Maybe there is a new driver for Linux, but I am too new at this Ubuntu stuff to know how to get it and install it.

For now, The Realtek driver on the Windows XP side is the "TE100-PCBUSR 32-Bit Cardbus PC Card" driver and I can surf the net in Windows XP with no problems.  The Ubuntu side works just fine also so I am content to leave well enough alone for now.

Hope this helps...

Sincerely:

Ron
Huh I have exactly the Same problem, I tried the same thing on my Ubuntu 7.04 and it did not work either.

I do not have any good knowledge on Linux just yet but could it have something to do with the new update?

I hope this works out soon because I love using ubuntu on my desktop, for now I'm sticking to the my ubuntu laptop

---

### Post by noob12 on 2007-10-10
You probably should read this thread carefully to see if this is the problem that you have or not:  [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

---

