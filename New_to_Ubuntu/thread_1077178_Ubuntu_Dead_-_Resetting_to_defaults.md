---
title: "Ubuntu Dead - Resetting to defaults?"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by den160593 on 2009-02-22
Hi, I was wondering. Is there a way of resetting Ubuntu to it's defaults? Because I changed my screen resolution, and that made my screen go haywire. I rebooted, but now I can't even load Ubuntu it just goes to a multi-coloured screen of death.

So is there a way to reset Ubuntu to it's defaults without entering Ubuntu graphically? As it doesn't work. I have XP Dual boot and thats what i'm on right now

Thanks
-Den

---

### Post by quinnten83 on 2009-02-22
if your having trouble with your display, you could log in with a live cd.
and then copy the xorg.conf file from the live cd to your harddrive.
That should reset it to the standard.
But don't quote me on that.

---

### Post by paydaydaddy on 2009-02-22
Please do not cross post, or post the same thing in multiple locations.

I posted a suggestion in the other thread you started.

---

### Post by den160593 on 2009-02-24
Still can't fix this... Anyone have any ideas?

---

### Post by cariboo on 2009-02-24
Start in recovery mode nad at the menu choose xfix, once xfix is finished select resume and  continue to the desktop. THis assumes you are rinning Intrepid (v. 8.10) if you are running an older version, in recovery mode  type at the prompt:

```
dpkg-reconfigure -phigh xserver-xorg
```

both actions will reset your /etc/X11/xorg.conf file to the default, and you should be able to get to your desktop.

Jim

---

### Post by den160593 on 2009-02-24
Hi, I tried it, however it didn't fix my problem. Now for some reasn when I click resume it loads a blurred and un-responsive windows XP background.

---

### Post by den160593 on 2009-02-24
If I went to the 'Drop to root shell prompt' option and then did:

dpkg-reconfigure -phigh xserver-xorg

Reckon that would fix my problem? Or does that do exactly the same thing as what was stated?

Or could I do something with the Live CD?

---

### Post by Roadbloc on 2009-02-24
I just reinstalled when this happened 2 me. BUT- i lost all of my work, but i had a backup.

---

### Post by den160593 on 2009-02-24
I'd like to see if there are any other options before I do that :(

---

### Post by den160593 on 2009-02-24
Anyone?

---

### Post by den160593 on 2009-02-26
... still having this problem almost 2 weeks after I logged my first launchpad support / 5 days since I logged here. Had two replies... where is this good support?

---

### Post by Peter09 on 2009-02-26
Have you tried going through recovery mode to the comand shell and then type startx. It may give you a GUI. If this does not work try the following command 

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.save
```
then reboot.

this removes your xorg.conf file and may initiate a reset of the video setup.

To reinstate the file do

```
sudo mv /etc/X11/xorg.conf.save /etc/X11/xorg.conf
```

---

### Post by utnubuuser on 2009-02-26
How about this thread:> [http://ubuntuforums.org/showthread.php?t=1060406](http://ubuntuforums.org/showthread.php?t=1060406)

---

### Post by den160593 on 2009-02-26
Thanks for replies. Peter, sadly that didn't work, thanks heaps for the response though :( Just before I try the second method, would doing this work maybe? Well, would it not stuff me up even further?

> sudo aptitude reinstall ubuntu-desktop

---

### Post by Peter09 on 2009-02-26
You need to get the package manager working with no errors, once you have done that then yes reinstall. 

By all means try it, the commands I gave you will not fix the problem of missing packages, rather they should set the package manager back to match your current configuration. If it has done that then try the re-install.

---

### Post by den160593 on 2009-02-26
Hi, I tried it. THe package manager worked, but it didn't fix my problem. Any other ideas? I installed a new ATI driver as well, can I go back to the default Ubuntu driver somehow?

---

### Post by Peter09 on 2009-02-26
To get back to your original driver:

Can you post the output of

```
more /etc/X11/xorg.conf
```

---

### Post by den160593 on 2009-02-27
It's this (had to write out on paper then type it up. But hopefully it's accurate)

> 
Section "Device"
Identifier "Configured Video Device"
End Section

Section "Monitor"
Identifier "Configured Monitor"
End Section

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
End Section

Sorry about my late reply ;(

---

### Post by Peter09 on 2009-02-27
Try envy

Get to the recovery mode command shell and

```
apt-get install envyng-core
```

when complete

```
envyng
```

Note if it cannot find envyng when you come to run it try envy<TAB KEY> this will auto complete (I'm not sure of the exact executable name.

---

### Post by Peter09 on 2009-02-27
Forgot to mention that you will need the -t switch

```
envyng -t
```

---

### Post by den160593 on 2009-02-27
Thanks for reply. It didn't work, it says that it couldn't locate some packages using apt-get. Then i tried running it (envyng -t) and it told me to do the apt-get thing. Tried again, twice but it fails all the time :(

Could I somehow install it otherwise? Is it possible to edit my installation via the LiveCD?

---

### Post by Peter09 on 2009-02-27
How are you connected to the internet, wireless or wired?

---

### Post by den160593 on 2009-02-27
wireless. I had problems with that as well, but I managed to fix it eventually ([http://ubuntuforums.org/showthread.php?t=1034071](http://ubuntuforums.org/showthread.php?t=1034071)). I can't connect to a wired network though. I have full access to internet on my WinXP boot.

---

### Post by Peter09 on 2009-02-27
Are you sure that you have Internet connectivity in command mode?

Can you post the apt-get errors

---

### Post by den160593 on 2009-02-27
It completes both the strings (both are Done for apt-get errors)

I tried envyng-core thing again. My error was more specifically:

Could not resolve au.archive.ubuntu.com

It says for me to maybe run apt-get update or try --fix (the rest of the text I can't read as it's off the screen).

---

### Post by Peter09 on 2009-02-27
That suggests that you are not connected to the internet properly. Can you post the output of 

```
ifconfig
```

---

### Post by den160593 on 2009-02-27
Link encap: Local Loopback
ine addr [my address, won't post publicly for now] Mark [same reason]
UP LOOPBACK RUNNING MTU: 16436 METRIC: 1
RX Packets 240, errors 0, dropped 0, over (can't read my writing here lol) 0,
TX Packets 240, errors 0, dropped 0, over (can't read my writing here) 0, collisions 0, txqueuelen : 0
RX Bytes: 15040 (15kB) TX Bytes: 15040 (15kB)

Thanks again for reply!

---

### Post by den160593 on 2009-02-27
I did some more tests, turns out I don't have internet connnectivity on the root shell..

Is there a way to re-install the graphic settings (default ones) from the LiveCD?

---

### Post by Peter09 on 2009-02-28
Apart from **xfix** and **xranr --auto** I really do not know. I would work on getting a wired connection to the internet.

---

### Post by den160593 on 2009-02-28
What about reinstalling Ubuntu. If I installed it again, would it overwrite the existing installation? Becuase I don't really have anything important on it

---

