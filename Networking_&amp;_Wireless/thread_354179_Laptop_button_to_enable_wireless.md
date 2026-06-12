---
title: "Laptop button to enable wireless"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by jonnymccullagh on 2007-02-05
I have been converting a friend to Ubuntu and we are stuck on the wireless bit.
His laptop is an e-system 3086 and the wireless chip is Realtek RTL 8187 54Mbps USB 2.0
Ubuntu recognises the device fine and I have set up wireless networking for WPA in the same way for his laptop as I did for my own desktop (which uses wireless fine with Linksys WMP55AG wireless PCI card). 
On the laptop I can see the wireless networks but the signal strength is zero for each. 
I think the problem may be that he has 3 buttons above the keyboard: one to launch a web browser, one to launch email and one to enable wireless. The button to enable wireless works on Windows and a green light begins to flash to show it is working - but in Ubuntu the button doesn't seem to work.
I have not found any other way to enable this wireless button (I checked the BIOS etc.).

Has anyone got any ideas?
Thanks in advance,
jonny

(Using Ubuntu 6.10 edgy)

---

### Post by EttanA on 2007-02-05
I had the same problem, not the same type of computer though. I have a HP nx6325, but the design seems to be kinda alike. I have one button for slideshow, one for wireless and one for internet. At first (when I used ndiswrapper to get the drivers) my (blue) light wouldn't come on. I thought it might be a hardware issue. However, when I used [this]("http://ubuntuforums.org/showthread.php?t=185174") guide without using ndiswrapper, it suddenly started shining again. I must admit I tried that guide after already using ndiswrapper to install another driver, but i removed it and it still works.

So, to make it short, it _might_ be that you've configured it wrong, it doesn't necessarily have to be a hardware issue, just to make you feel a little bit better I guess :-)
However, as your network card and computer differs from mine I unfortunately have no idea what could be wrong (still a Linux newbie).

---

### Post by jonnymccullagh on 2007-02-06
So rather than trusting that Ubuntu got the driver right you think I should try ndiswrapper? 
Do you suggest I try the Broadcom driver with ndiswrapper even though the device is showing as Realtek (and showing as the same device as Windows sees).
:confused:

---

### Post by EttanA on 2007-02-06
I was mainly talking about your issue with the light that wouldn't come on, and telling you that when I tried another way to install it, the light worked again. So I don't think you have to be going into BIOS and trying to get that part to work, if you find the correct way to get the network up and running it should be indicated by the light coming back on.

But on the other hand, it might be broken, I can't know for sure, sorry.
And about using ndiswrapper, I have no idea about your Realtek since I don't have it, but it seems like it has worked for a lot of people. When i was in your situation i spent like 5 hours googling ^^
(3rd reinstall of Ubuntu right now :-)) 
And I don't think you should go with the Broadcom driver, but maybe you can find a driver for your card on the homepage where you bought the computer if you decide to try ndiswrapper.

---

