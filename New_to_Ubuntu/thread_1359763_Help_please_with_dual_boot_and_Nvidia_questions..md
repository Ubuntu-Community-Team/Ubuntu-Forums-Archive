---
title: "Help please with dual boot and Nvidia questions."
date: 2009-12-20
forum: New to Ubuntu
---

### Post by big.d on 2009-12-20
I've been hunting around and I have a few questions about how to do things, so I'll just shoot them off. Any help would be greatly appreciated. Bear in mind that the computer in question has no internet connection, so the only way I can directly access the internet with it is to take the thing to a friend's house, which I can only do like 1 day a week.

1) I can't figure out how to dual-boot in my situation. I just installed Windows XP Pro alongside Ubuntu 9.10. (9.10 was installed first. Lacking a proper partition tool, I used 9.10's setup disc to resize the Ubuntu partition, then installed XP on the empty resized partition that I made. XP Setup told me that I would have to mark the Ubuntu partition inactive to install XP, and that I could mark it as active from XP once Setup was finished. I tried that with no luck, since XP won't recognise the 9.10 partition's filesystem. 

I found a guide on this forum, on how to reinstall GRUB from the Ubuntu Live CD, but is that all there is to it? Or do I have to do anything else with GRUB to make dual-booting work?

2) The Nvidia driver installation is confounding me. I have tried downloading and installing the actual Nvidia drivers, but always seem to have no luck. (note: I'm trying to install them by downloading them from Nvidia's site onto a flash drive, copying them to my PC, and installing from there.

Could someone please walk me through the installation process for the Nvidia drivers (190.53) on 9.10, or link me to an already existing guide?

3) I need a music program for 9.10. I always used Winamp for Windows, so I'm looking for something similar. I don't really like Rythmbox or Songbird, since the don't have a playlist feature like Winamp does.

Thanks in advance for any help you can give me. I really appreciate you taking your time to read this.

big.d

---

### Post by allenbradley on 2009-12-20
(a) The dual boot can be done using windows (EASYBCD) or ubuntu (GRUB). AFAIK, modifying GRUB will do. Maybe you can link to the forum where you found the tutorial.

(b) Rhythymbox has a playlist. If you like a song, right click and add to playlist. Otherwise, install banshee using ```
sudo aptitude install banshee
```

---

### Post by big.d on 2009-12-20
Thank you!

---

### Post by leef on 2009-12-20
> **big.d said:**
> 
2) The Nvidia driver installation is confounding me. I have tried downloading and installing the actual Nvidia drivers, but always seem to have no luck. (note: I'm trying to install them by downloading them from Nvidia's site onto a flash drive, copying them to my PC, and installing from there.

Could someone please walk me through the installation process for the Nvidia drivers (190.53) on 9.10, or link me to an already 
existing guide?


It would be much easier to go to "System > Administration > Hardware Drivers" to install the nVidia drivers but if you want to install the 190.53 drivers here's a guide;

[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

> **big.d said:**
> 
3) I need a music program for 9.10. I always used Winamp for Windows, so I'm looking for something similar. I don't really like Rythmbox or Songbird, since the don't have a playlist feature like Winamp does.


You could try audacious it's almost identical to winamp, you can even use winamp themes with it IIRC.

---

