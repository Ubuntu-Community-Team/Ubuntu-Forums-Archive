---
title: "Ralink 2500"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by sapoleon on 2008-11-04
I start using Ubuntu with the version 7.10. I like it, and start using it frequently except for playing. 
All worked almost without problem, and I had to install my own nvidia drivers and touch some other small things...
I don't have too much time to play with it, so it was very nice that all worked almost without trouble.

I tried to make an upgrade to 8.04, and despite all my efforts, I couldn't make the Ralink 2500 wireless get to work. (it works, but like a slug). I star reading posts and everything, but couldn't get to it. Tried to install the serialmonkey drivers but it seems that I didn't do it right. 
With a lot of disappointment, I downgrade my laptop and pc to 7.10. (new install). (unfortunately, i have the same wireless chipset in both machines).

Now, I thought that after reading forums and post that in 8.04 the Ralink didn't work, the bug of driver will be fixed for this new version. And I installed it in my PC. 

Again a disappointment. The same problem. With the Ralink 2500 chipset, the internet is not working properly. very slow rate....

So my question is like this. What should I do?????
Is there a nice post or help to change drivers or to solve the sluggishness?
Or I should just buy new wireless cards? And if so, which ones? (one PCI, one PCMCIA). (And I should say that I don't think this is the way to go, because the wireless cards do work like a charm in Windows!!!!)

Thanks for your help.

---

### Post by mdc on 2008-11-10
Just upgraded 7.10 to 8.04, and hoped the Ralink 2500 would now work without quirks. It did not, the rt2500pci driver seems useless at the current stage.

I have spent several evenings googling. This page gave the best tricks

[http://http://ubuntuforums.org/showthread.php?t=602180]("http://http://ubuntuforums.org/showthread.php?t=602180")

But the source package in the repository seems too old. It can build, but not load on the current kernel.

Instead, go down the page where it is suggested to download a fresh .tar.gz from serialmonkey.com at 
[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads]("http://rt2x00.serialmonkey.com/wiki/index.php/Downloads")

That works. Then blacklist the rt2500pci driver in  /etc/modprobe.d/blacklist as shown, and the whole setup from 7.10 with WPA info edited into /etc/network/interfaces works again. :)

---

### Post by royleith on 2009-04-10
I have had the problem for some time with the RaLink 2500. I got the card to work by using the Windows Wireless Drivers tool to install the RaLink Windows driver in the NDIS wrapper. 

Just pop the driver files from the drivers CD into a convenient folder and select the appropriate .inf file using the installation program (there is something similar in Kubuntu and Ubuntu).

It works at full speed for a while, but often stops working requiring a reboot. Sometimes it works for hours without problems.

I have taken to using a ZyXEL usb wireless module which only works at 24 MBit.s, but is reliable. I have also got an Intel mini PCI card to replace the RaLink, but cannot find my way to the PCI slots.

Regards
Roy Leith

---

