---
title: "Xubuntu 15.04 - File Manager freezes when opening Windows 7 shared folder"
date: 2015-10-20
forum: Networking &amp; Wireless
---

### Post by Derf_Skren on 2015-10-20
Hi,

I apologise in advance for posting this question as I'm sure it must have been answered many times but I've had no luck searching out an answer on my own.

In short when I go via network:/// or use Gigolo I am able to enumerate the shares on the Windows 7 box on my LAN, but if I attempt to open a share I get a blank FileManager window and when I try to close it I get the "busy and not responding" dialog. Edit: The behaviour is different from time to time, going via the network path sometimes I can open a share but it just says "Loading folder contents..." forever. If I keep bashing at it the behaviour devolves and I get prompted for a password for an open share (share and filesystem permissions to full control for Everyone under Windows 7) where I would not normally get that if I reboot and try from scratch.

In case it matters, I've installed Xubuntu 15.04 from DVD and have allowed it to update itself. I haven't removed any software, but I have added a few things: Chrome, BOINC, Shrewsoft VPN, Timemon... I think that's it. I did try to build Shrew myself so I think I apt-getted cmake and mcrypt and possibly some other things following recommendations at the terminal prompt.

Any help with this would be greatly appreciated. I know Windows and Linux are very different beasts but I feel like I'm back in the bad-old-days trying to get two Windows 98 boxes to talk!

Thanks!

---

### Post by Derf_Skren on 2015-10-27
So this is the legendary hospitality of the open source community. :-)

It has started working by itself tonight, for posterity I will keep updating this post if I ever discover why or if it turns out to be a one-off fluke.

---

