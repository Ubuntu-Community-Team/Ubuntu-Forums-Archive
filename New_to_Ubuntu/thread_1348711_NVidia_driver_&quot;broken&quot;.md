---
title: "NVidia driver &quot;broken&quot;"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-12-07
Three weeks ago, I posted about [Compiz]("http://ubuntuforums.org/showthread.php?t=1328435") causing some problems. I never received a reply.

After 3 weeks of struggling with this, I'm now convinced the problem is not with Compiz, but rather, with the NVidia driver(s).

I thought compiz the prob, because on every boot (warm or cold) the screen resolutions is skewed. The icons across the top row on the desktop have moved "under" the panel. The screen prevents "seeing" the top part of Firefox, Chrome, etc.

I've looked around for what happens to the OS, if the NVidia driver is removed. Some posts, while a while ago, seem to indicate that's a real problem, due to certain WiFi cars. I can get no satisfaction about my card: D-Link WDA2320 wireless as a problem.

My question is: if I remove the Nvidia driver (in my case: Nvidia driver version: 173.14.20.) will I be left with no X until I reboot? Even if I reboot? 

How do I "safely" (microsoft think here), remove this driver and re-install it, without "blowing up" the screen . . .  I'm at a loss for words to describe what I mean. As I type this Message, in a box at this forum with a slightly darker color -- will this appear or the "full screen" terminal or Ubuntu's "safe mode"? I'm apologize for being so wordy, but I'm feeling shakey about removing this driver. Yet, I'm sure it is not perfectly, or fully installed.

I want to "go back" to the state of this OS, before the installation of the Nvidia driver, without causing myself more harm.

Thanks, community.

---

### Post by LuisGMarine on 2009-12-07
I think this might help you out a bit.  Good Luck :popcorn:

[https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")

---

### Post by Mark_in_Hollywood on 2009-12-07
Semper Fi!, guy.

I read that and the "mere" binary driver install. I didn't see talk about my problem. Well, OK.

I did load the other NVidia driver that is available for this vid card. On reboot, it still required opening System/Preferences/Appearance/Visual Effects and re-selecting the "Normal" style. I've enclosed a screen shot.

At the top left of the screen shot, you will see how the panel "cuts off" the Chrome icon. If I use the "screen" as is, Chrome opens and part of the top of it is also "cut off".

---

### Post by falconindy on 2009-12-07
You can disable compositing in /etc/X11/xorg.conf. Add the following:

```
Section "Extensions"
        Option         "Composite" "Disable"
EndSection
```
If the "Extensions" section already exists, just add the option to that section.

---

### Post by Mark_in_Hollywood on 2009-12-07
> **falconindy said:**
> You can disable compositing in /etc/X11/xorg.conf. Add the following:

```
Section "Extensions"
        Option         "Composite" "Disable"
EndSection
```
If the "Extensions" section already exists, just add the option to that section.

When I opened /etc/x11/xorg.conf

there is NOTHING in the file! Is that normal?

---

### Post by falconindy on 2009-12-07
> **Mark_in_Hollywood said:**
> When I opened /etc/x11/xorg.conf

there is NOTHING in the file! Is that normal?
Sure. xorg.conf is supposed to be deprecated, but it's still used from time to time. If you want a generic xorg.conf, you can use nvidia-xconfig (i think the 173 driver comes with it) to generate one.

---

### Post by Mark_in_Hollywood on 2009-12-07
falconindy

I surely wish I could understand what you are saying. I am using the Nvidia driver ver. 173.14.20. I'm guessing that by deprecated you mean that the file: xorg.conf is no longer used, except when doing something like you describe in your previous post to me. Lastly, trying your idea:

mark@Lexington-19-karmic:~$ nvidia-xconfig
Error: you don't seem to have the permission to modify your /etc/X11/xorg.conf.
Try using "sudo"
mark@Lexington-19-karmic:~$ sudo nvidia-xconfig
[sudo] password for mark: 
mark@Lexington-19-karmic:~$ sudo nvidia-xconfig
mark@Lexington-19-karmic:~$ 

huh?

---

### Post by falconindy on 2009-12-07
That is indeed weird. You've interpreted my last post 100% correctly. To expand, deprecation means that a method is still available, but its unsupported and can/will disappear soon. After you got the null reply from nvidia-xconfig, did you check to see if xorg.conf was still the same? It's **supposed** to tell you that it made a backup... perhaps the 173 version of xsettings is different from the one bundled with the newer drivers?

---

### Post by Mark_in_Hollywood on 2009-12-08
I'm closing this as it's not leading to a solution. I have limited computer skills. Especially where it involves the video. I can cut &  paste, but I have NO idea of what to do next. 

Thank you, community.

---

