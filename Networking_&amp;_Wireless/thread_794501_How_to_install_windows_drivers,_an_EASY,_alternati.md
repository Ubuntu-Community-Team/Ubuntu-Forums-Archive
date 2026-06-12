---
title: "How to install windows drivers, an EASY, alternative method."
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by Master_Z on 2008-05-14
I'm writing this in hopes that you guys will get your wireless working as I did today. The main way windows drivers are installed is through a utility called ndiswrapper. My way is the same concept, only WAY easier. I use a derivative of it called ndisgtk. Basically it does all the installing for you. Enjoy, and best of luck.

1) Download the Windows XP driver of your wireless. If you dont know where to get it, google it. Extract it (drag folder out) to the desktop. 

2) Download ndisgtk by going to SYSTEM, ADMINISTRATION, SYNAPTIC PACKAGE MANAGER. Type in ndisgtk in the search box. It should appear. Check the box and hit apply. This should cause it to download ndisgtk, as well as a couple other necessary files. 

3) Go to SYSTEM, ADMINISTRATION, WINDOWS WIRELESS DRIVERS. Click Install New Driver and browse for it. It should be in that same folder on your desktop. The file should be in .inf format. Once selected, it will take only a few seconds to install.

4) By this point, it should say hardware present in the box. This shows that it successfully detected and installed your wireless card. Now, on the taskbar, left click your network icon. It should now have wireless, and it you should be able to see all wireless networks in range. Choose your network, connect, and you're done!

I hope this simplifies a lot of problems users have had with their wireless not working. Ndiswrapper is a great utility, but its too complicated for most users. Ndisgtk is much better and is very easy to use. Thanks.

---

### Post by dmizer on 2008-05-14
ndisgtk is simply a graphical interface for ndiswrapper.

most people giving help or howto's for ndiswrapper give directions in cli commands so that someone using ubuntu, kubuntu, or xubuntu can use it.

---

### Post by Master_Z on 2008-05-14
I stated that in my post. Its so much easier to use and faster than ndiswrapper.

---

### Post by dmizer on 2008-05-14
in your post, you said it's a derivative.  ndisgtk is ndiswrapper, not a derivative or alternate version, but perhaps i'm just splitting hairs.  however, it still doesn't work for those users with kubuntu (which is not a gtk interface), unless they also install all the gtk dependencies.

the official documentation for ndiswrapper does make mention of ndisgtk: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?)

---

### Post by zoro41 on 2008-05-15
Hi
I am a very new linux and ubuntu user. I have installed ubuntu 8.04 Desktop  for x64 . I have a zyxel usb wireless card. I was trying to find a way to install it and came uo with ndiswrapper. I downloaded it ( from my other computer ) and followed the instaructions on the sf site. when I entered "make install" it came up with lots of errors. Then i kept searching and found this thread. I managed to install everything as you described and in the wireless drivers window, it said hardware present. But when go to the Edit wireless Networks, it doesnt show any networks. From the terminal i looked with "iwconfig" and ealised that the system doesnt see my wlan0 ( or whatever it should be ) but only the physical ethernet ports on the computer. Now i am stuck :) Any ideas ???

Thanks in advance

---

### Post by zoro41 on 2008-05-15
By the way, 
I can see the usb wireless card ( zyxel g-260 ) when entered "lsusb" but not with iwconfig

---

### Post by zoro41 on 2008-05-15
Ok, discovered one more thing
From the dmesg output, I saw that it says something like :
"kernel is 64-bit but windows driver is not ..... bad magic ...
 couldn't prepare driver 'wlanutg'
 couldn't load driver wlanutg; check system log messages ....."

The problem is my cpu is 64 bit and I have 4 GB of ram which i cannot use totaly with 32-bit OS. 

Is there a workaround for this or I am doomed to buy a card with 64-bit driver ???

---

### Post by getabetterpic on 2008-05-15
I did some google work trying to turn something up on a 64-bit driver for that adapter, but can't find anything.  What you could try if you wanted to is go to [Zyxel's website]("http://www.zyxel.com/web/support_download_list.php?indexflag=20040906164721") and download some of the other 64-bit drivers and see if you can get one of them to work with your card.  Or, you could go buy one that has the 64-bit drivers.

---

### Post by Master_Z on 2008-05-15
Yeah, perhaps it was made for 32 bit systems, so you might need to find 64 bit drivers.

---

### Post by Master_Z on 2008-05-17
Bump.

---

