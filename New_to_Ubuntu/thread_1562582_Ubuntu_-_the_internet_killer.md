---
title: "Ubuntu - the internet killer"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by finalmike on 2010-08-27
I installed the newest Ubuntu on my win7 machine today. After completing the installation and booting up Ubuntu I figured that I'd automatically be connected to the internet. Lo and behold, no connection. After trying with no avail to connect I booted back into win7. Now win7 will not connect to the internet. It's as if windows doesn't recognize that I've got my modem/router plugged in. I tried to connect, with both Ubuntu and win7, with router and straight into the modem. I reinstalled my network adapter with no avail. The only way I'm able to connect now is by plugging in a USB wireless adapter in. Any idea why this is happening? Is this a normal occurrence? Any ideas/need any other info? Thanks guys~

---

### Post by Muscovy on 2010-08-27
This is not a normal occurrence.

Does a wired (Ethernet) connection work in either OS?

I don't know what's going on with Windows, but sometimes you have to install extra drivers in Ubuntu. Open System -> Administration -> Hardware Drivers and check there.

---

### Post by Iowan on 2010-08-27
*Sometimes*, machines can reset (software) faster than the hardware. Have you tried a full power-down reboot?

---

### Post by finalmike on 2010-08-27
My wired connection has worked perfectly until I ran Ubuntu for the first time. After that, it won't even work in win7 anymore.

I have also hard rebooted a few times.

I  checked the device manager in win7 and it doesn't look like any drivers  have disappeared... even if they did, a quick "detect new hardware"  would reinstall them.

---

### Post by LiquidMeson on 2010-08-27
Do you know the model of the motherboard?/ or computer/laptop?

Sounds like someone put a (I hate linux fail switch) in your computer. Could try seeing if it works in the live cd, and also looking through the bio's settings. Typically f2, delt, esc, or something like that on startup.

---

### Post by Rasa1111 on 2010-08-27
definitely not normal. 
I havent seen Ubuntu not instantly connect yet, 
on all the pc's ive installed it on,
which is quite a few.. 
not sure what's up, sorry. 

 good luck

---

### Post by egalvan on 2010-08-27
Separate Ubuntu Install, on it's own partition?
or Wubi Install, inside Windows?


I can echo rasa1111 (post #6)....
I have installed Linux on close to 80 machines in the past two years....
every install automatically found the **wired** network card, and the Internet (if available)
Intel wi-fi cards were all found...
most other wi-fi's were problematic.

---

### Post by ankspo71 on 2010-08-27
Hi,
Did you have a working wired internet connection while using the Ubuntu live cd (desktop cd)?

As for what could have happened... in my experience, I have noticed that resizing partitions can make operating systems not work as well as they once did. With that said, I think this is why defragmenting is highly recommended before resizing a windows partition. 

System Restore might be able to get you back online in windows. You might even try creating a new connection in windows (instead of trying to revive the old one.) That's what I had to keep doing with wireless connections in XP on my neighbor's PC (and Kubuntu on my PC too). Try unplugging your modem and router for about 3 minutes for it to reset the connection too.

---

### Post by finalmike on 2010-08-27
I installed it via the windows installer. Regardless of the install, I should still be able to connect when I boot back into windows.

Also, I tried to make a new wired connection; still no go.

I can check the model number tomorrow but it's a newer Asus mobo.

---

### Post by Ocxic on 2010-08-28
Reset your Router, some routers will actually not give out a new IP to different computers, especially if your using a cable modem, just turn it off, or remove the power cord for 10 seconds, and then try again.

---

### Post by finalmike on 2010-08-28
I've tried all of the reboots and obvious stuff, i.e. modem, pc, router, cat5, etc. 

Now I'm not getting lights on my NIC. While this would normally indicate a hardware failure, this is a PC that is less than 6 months old, has never had any issues of any kind, and I maintain it very well (I'm an IT). I find it hard to believe that installing Ubuntu would cause any sort of hardware issue. Hell, I installed Ubuntu just moments after downloading it. Also, this happened right when I booted into Ubuntu; it never found a wired network.

While in Ubuntu (I recently uninstalled it in hopes of this issue being fixed to no avail), since it did not find my wired network, I added a new wired network, which of course did not connect, but could this have caused any issues? I don't see how this could harm anything but it's worth asking. When I attempted to create this wired network I did not change any options; I just selected "create wired network" and saved. 

My network adapter is "Realtek PCIe GBE Family Controller." I've uninstalled and reinstalled this. There are also no newer versions to install. Now, strangely enough, in device manager this displays as "Realtek PCIe GBE Family Controller #2." Obviously I do not see a "#1" or just "Realtek PCIe GBE Family Controller." Perhaps this has something to do with trying to create a new wired network while Ubuntu was booted? Also, when I attempt to delete this wired network my PC freezes and requires a hard reboot. 

This absolutely baffles me.

---

### Post by finalmike on 2010-08-28
FIXED!

I found the solution here: [http://ubuntuforums.org/showthread.php?t=1436667](http://ubuntuforums.org/showthread.php?t=1436667). What an easy fix: unplug the power cable for a few minutes, plug it back in, and back to wired network land.

I knew I wasn't crazy!

Granted this is an error that should never happen, but maybe I'll give Ubuntu another try. I had many scenarios in my head, including one that had a virus in the Ubuntu download!

Thanks for the help! :p

---

### Post by egalvan on 2010-08-28
> **finalmike said:**
> FIXED!

I found the solution here: [http://ubuntuforums.org/showthread.php?t=1436667](http://ubuntuforums.org/showthread.php?t=1436667). What an easy fix: unplug the power cable for a few minutes, plug it back in, and back to wired network land.

yeah, that's what *Iowan* in post #3 suggested you do :)

"Full power-down re-boot"


> 
Granted **this is an error that should never happen**, but maybe I'll give Ubuntu another try. I had many scenarios in my head, including one that had a virus in the Ubuntu download!
Thanks for the help! :p

It happens to Microsoft also... yet few seem to blame them, for some odd reason...
(e.g. there is an abundance of code in the BIOS whose sole purpose is to provide work-around's for faulty MS coding)

---

### Post by mc4man on 2010-08-28
> It happens to Microsoft also... yet few seem to blame them, for some odd reason
I have a new boarder here who **only uses win 7 **and the same thing happened to him the other day - could not connect to my network here (wired
The only solution that worked was the same - shutdown, pull the power cord for a few, ect.

---

