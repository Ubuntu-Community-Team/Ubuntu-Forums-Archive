---
title: "[SOLVED] Bellsouth wireless in Xubuntu Gutsy"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by Killa Frog on 2007-11-23
Hey, guys. I just put Xubuntu Gutsy on my cousin's computer so he could run a decent system (used to be XP, which ran like an old man with two bum legs) at a decent speed so he can do his homework and research and whatnot, and everything works great except I can't figure out how to get him on the internet. Currently his house has a wireless setup with Bellsouth FastAccess, and the USB wireless adapter they provided isn't recognised by Xubuntu. In fact, Xubuntu doesn't seem to even want to let me set up an internet connection that isn't modem, presumably because the hardware would indicate that nothing else would be possible. 
Computer is an eMachines T1100
1 GHz Celeron
128 MB RAM
No ethernet ports, just a 56k modem (it's an old computer, if you haven't noticed) 
The model number on the back of the adapter is SWL-2300U, if that helps at all. Any help y'all could give me would be extremely useful, as I have only a couple days to resolve this issue before I'll be forced to put Windows back on his machine (which I really, *really* don't want to do).  Much thanks in advance, and if there's any other information you need from me, please let me know.

---

### Post by ugm6hr on 2007-11-23
This seems to suggest it is possible with ndiswrapper (assuming it's the same device - Netopia / Samsung SWL-2300U):
[http://ubuntuforums.org/showthread.php?t=383981](http://ubuntuforums.org/showthread.php?t=383981)
At least that gives you some hope....
```
lsusb
Should return (if same stick): 
Bus 001 Device 006: ID 055d: a230 Samsung Electro-Mechanics Co.
```

---

### Post by Killa Frog on 2007-11-23
See below post.

---

### Post by Killa Frog on 2007-11-23
Thanks for the direction, ugm6hr. Right now I'm struggling with the terminal (well, not really *struggling*). Looks like there's a bug that returns the user to the login screen when opening up Accessories -> Terminal, so I'm changing the color depth to 16 (I read that fixes it) in /etc/x11. If there's an easier way to fix this little roadblock that you know of, please let me know. At any rate, I can't fix the wireless problem until this is resolved, so I'll update with the results of your advice when I get the chance to actually run it. What a silly little (mad inconvenient!) bug I stumbled across :(.

---

### Post by ugm6hr on 2007-11-23
> **Killa Frog said:**
> Thanks for the direction, ugm6hr. Right now I'm struggling with the terminal (well, not really *struggling*). Looks like there's a bug that returns the user to the login screen when opening up Accessories -> Terminal, so I'm changing the color depth to 16 (I read that fixes it) in /etc/x11. If there's an easier way to fix this little roadblock that you know of, please let me know. At any rate, I can't fix the wireless problem until this is resolved, so I'll update with the results of your advice when I get the chance to actually run it. What a silly little (mad inconvenient!) bug I stumbled across :(.

Perhaps try installing a different Terminal program.... From memory, there's aterminal, xterminal and a few others.

I suspect the issue is with the XFCE terminal program.  Altho I have never encountered it.

---

### Post by Killa Frog on 2007-11-23
Okay I resolved the terminal issue, and there is some good news:
lsusb returns what you said it would, but:
when I try to use ndiswrapper, it says there are no ndiswrapper utils found! I tried 
sudo apt-get install ndiswrapper-utils
and it told me the package was replaced by ndiswrapper-common. So I installed that, tried to run the script again, and it tells me there are no ndiswrapper utils... I'm at a loss. What am I doing wrong?

---

### Post by Killa Frog on 2007-11-24
Never mind my last post. I had to add the version number to the end of ndiswrapper-utils (plain stupidity on my part). So now the problem seems to be finding the right driver for this adapter, which for the life of me I can't seem to do. It's looking more and more like I'm going to have to put Windows back on his machine, just so he has internet... Someone please help me save him from this cruel, cruel fate!

---

### Post by ugm6hr on 2007-11-24
> **Killa Frog said:**
> So now the problem seems to be finding the right driver for this adapter, which for the life of me I can't seem to do. !

Try one of these:
[http://www.wireless-driver.com/download/samsung/2007-8-1/Samsung-MagicLan-WLAN-USB-AdapterSWL-2300U2350U-Driver-for-Windows.htm](http://www.wireless-driver.com/download/samsung/2007-8-1/Samsung-MagicLan-WLAN-USB-AdapterSWL-2300U2350U-Driver-for-Windows.htm)
[http://members.driverguide.com/driver/detail.php?driverid=385927](http://members.driverguide.com/driver/detail.php?driverid=385927)
[http://ftp.bellsouth.net/drivers/Netopia_3D_Reach_PCMCIA_WIFI_Card/ME/WifiDrivr/SamSungUSB/Win9x/](http://ftp.bellsouth.net/drivers/Netopia_3D_Reach_PCMCIA_WIFI_Card/ME/WifiDrivr/SamSungUSB/Win9x/)

Or if he's still got the original CD that came with it - that will probably work too.

EDIT: If the USB wifi device needed a driver for Windows, and you haven't got it - you could probably ask Bellsouth to provide it again (but don't mention Linux).

---

### Post by Killa Frog on 2007-11-24
I've installed all of these drivers, and running ndisconfig -l tells me they are all invalid... is there a way to install drivers that aren't .inf files? Or would they not do me any good anyway? I've never had this problem before, it's really starting to drive me crazy.

---

### Post by ugm6hr on 2007-11-24
> **Killa Frog said:**
> I've installed all of these drivers, and running ndisconfig -l tells me they are all invalid... is there a way to install drivers that aren't .inf files? Or would they not do me any good anyway? I've never had this problem before, it's really starting to drive me crazy.

It's been a while since I used ndiswrapper - so I'm not sure.

But I think the file has to be a .inf file, and you have to have the matching .sys file in the same folder.

If the Windows driver is not a .inf file - you have to extract / install it in a Windows machine, and then search for the .inf file in the Windows folder to copy to Ubuntu.

Can anyone else help with this?

---

### Post by altongary on 2008-04-28
I just figured this out by accident. Here's what you have to do:
sudo modprobe acx
sudo modprobe ndiswrapper
sudo ndiswrapper -i swlubtl.inf (from whatever folder your driver is in)
sudo ndiswrapper -i netswl3u.INF 
sudo ndiswrapper -m

Unplug and then plug in your adapter. You should now have a working wireless interface.:guitar:

---

### Post by Killa Frog on 2008-05-12
Thank you everybody for all of your help. I met back up with my cousin recently, who found an alternate means of cennection, but i tried some of the last suggestions for giggles and it looks like it would work fine. It's a shame it's too late to return his other card, could have saved him some money... Let me know if there's some official way to thank you all for your help so it shows up in y'all's future posts, I'd be more than happy to let others know how helpful you all were!

---

