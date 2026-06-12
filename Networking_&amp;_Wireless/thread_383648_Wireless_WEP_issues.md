---
title: "Wireless WEP issues"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by karachuonyo on 2007-03-13
This time i do need some guidance badly. I was trying to set up my desktop to connect wireless and followed this thread on setting up WEP [http://www.ubuntuforums.org/newthread.php?do=newthread&f=136](http://www.ubuntuforums.org/newthread.php?do=newthread&f=136). I then edited my network interfaces and then rebooted but since the boot screen will freeze just after the kubuntu logo but before the login screen. When i try to boot on recovery mode it seems to be fine until i get the login cursor but immediately i get a page or two of text then it ends up with text proclaiming [1717960.660000] <0> kernel panic - not syncing: Fatal exception in interrupt. After this i have to hard reboot to get the PC starting again. Share ideas please.

OK its now 20 hours since i posted this and no replies so far. Anyway I've spent lots of time on the forums and google and it seems that my editing the network interfaces will not have led to the kernel panic. The most common thought seems to be a hardware related issue but i have windows xp on the same disk and it's working as usual. I've dug out my live edgy CD and that boots up as expected and shows up my partitions and devices as they should be. I would like some assistance on how to be able to undo the editing  of the networking interfaces to what they were before so that i can rule that out as a cause before anything else.

---

### Post by karachuonyo on 2007-03-15
Ok problem is solved and thanks to all who read the post but could not understand my dilemma. For reference in case some one experiences a similar problem my web search led me to believe it's a hard ware issue. So i ended up by unplugging all the peripherals connectted to the PC, then disconnected the cd-rom, floppy, graphics card, sound card and wireless card. After disconnecting each component i booted the pc to see if it was the culprit. As luck my have it after removing the wireless pci card and booting the pc it ended up with my login screen. I was then able to login and then edit my /etc/network/interfaces as they before. Then it was just a matter of putting everything back together. 
  Now my initial problem is still existing in that my pc cannot connect wirelessly. My wireless pci card seems to be properly installed and can even detect my network but i end up with not associated when i try to connect.. My network has a WEP key on it but that seems not to be problem 'cos my laptop running ubuntu connects immediately WLAN assistant.

---

