---
title: "Grub not booting after install"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by garth813 on 2011-04-18
I have installed Ubuntu desktop edition and each time I restart after finishing the installation my computer sounds like its doing something and then my monitor just goes black and nothing happens.  I have a nvidia video card and when I install at the Ubuntu screen I have to select F6 and choose the "nomodset" option.  I have gotten to the grub screen once and I think I tried system recovery mode and successfully logged into the system, but now I can't even try that again because there is no grub screen.  I have  live booted from my Ubuntu 10.10 CD and tried to get something going using the terminal, but I have not been successful (I am very new to linux so the terminal is kind of confusing). If anyone could help that would be great.  Thanks

---

### Post by Quackers on 2011-04-18
If you needed to use the nomodeset option to boot the live cd, you will need to use it for the first boot of the installed system too.
Whilst booting hold down the shift key to get to the grub menu. When it appears the top item should be Ubuntu and it should be highlighted. If so, press the "e" key and a new screen will appear.
Using the arrow keys navigate to the end of the kernel line which currently ends with "quiet splash". At the end of quiet splash press the space bar then type in "nomodeset", but without the quotes. Then press ctrl+X to boot.
The desktop should now load. Install the Nvidia driver and you should then be ok on rebooting. The system should automatically run Additional Drivers and you should be prompted to install the required drivers. If not, go to System > Admin > Additional Drivers

---

