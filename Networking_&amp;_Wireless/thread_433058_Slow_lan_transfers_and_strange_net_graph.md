---
title: "Slow lan transfers and strange net graph"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by manuelb on 2007-05-04
Hi all,
i'm pretty new to Linux in general so i decided to get my foot wet with Ubuntu Feisty, installing it on an external USB SATA hard drive and booting from there: it's all good, but i've found a couple of interesting "oddities" i thought good to share with you, hoping to understand what's going on with your help.

My network card is an Intel Pro 1000 (using the e1000 driver) and the first strange thing are my network graphs: going to System->Administration->System Monitor, my network graph with 1-second pool delay (Edit->Preferences->Resources) looks this way:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=31754&stc=1&thumb=1&d=1178306170[/IMG]
[graph_1sec]

But setting the delay to 2 seconds i got a clean graph:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=31755&stc=1&thumb=1&d=1178306170[/IMG]
[graph_2sec]

This is odd: so i've setup another Ubuntu box (with a Realtek-chipset eth card) and graphing with 1-second delay produce a non-rollercoaster'd result ;)

What's up with the e1000 driver? Could the delay problem lie in the way the pooling process does query about network statistics?
Or maybe that behavior is by design? [??]
Whatever it is, GKrellM seems to produce graphs the same way, with interleaved vertical scanlines when no statistical data is received/retrieved, but only on my main box (moontwo): the secondary box (nirvana) i setup in order to test things out is not affected:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=31756&stc=1&thumb=1&d=1178306760[/IMG]
[gkrellm_graph]


Mmm.. anyone with an Intel Pro 1000 can confirm this odd behavior?


The other issue i'm facing is slow network transfers: i was copying one big file from an ubuntu box (sbm share) to another ubuntu box and i noticed the transfer was using only 18/20 Mbit/sec out of 100.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=31757&stc=1&thumb=1&d=1178306871[/IMG]
[iftop_nautilus]

So, i tried to boot Windows XP Pro and doing the transfer from there and it completed in less than half the time!
I decided to reboot the machines and retry the ubuntu-to-ubuntu transfer but without luck, still 18Mbit.
Could the slowdown be due to Nautilus and the way it handle smb:// shares? What's under-the-hood with it? So i decided to stick to terminal and copying from there... and wow, i got 65.5Mbit/sec!
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=31758&stc=1&thumb=1&d=1178306871[/IMG]
[iftop_smbclient]

So, Samba could have overhead and stuff like this, but it's definitely working correctly: 65Mbit aren't full bandwidth, but i do know the other box is slow as hell and Windows results are pretty the same, with Linux just a little faster ;)

While reading these forums searching for a solution  i found out that "slow lan transfer" problems are pretty diffuse, may this helps some of you.

---

### Post by voeck on 2007-06-04
Hi!

The strange net graph is an issue with the e1000 driver. I have the same problem here. The only solution would be to modify the kernel module. You can find more details here:

[http://lists.jutley.org/pipermail/gkrellm/2006-April/000036.html](http://lists.jutley.org/pipermail/gkrellm/2006-April/000036.html)

---

### Post by manuelb on 2007-06-18
Hi Voeck,
thank you for your reply: i was just thinking about modifying the kernel module myself and then submitting a patch, anyway thank you for letting me know that thing!

---

