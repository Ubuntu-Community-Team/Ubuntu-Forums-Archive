---
title: "WinFast A6200-tdh questions"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by Just A # on 2009-11-17
I just installed/am running Xubuntu 9.04 on my old desktop. In it, I have a WinFast A6200 TDH graphics card by Leadtek (AGP 64bit 128MB nVidia GeForce 6200).

I'm not sure if my graphics card is working correctly though. I tried to run default chess game that comes with Xubuntu in 3D mode but it immediately crashes. As well, when I start up Google Earth it warns me that my system will run very slow since no 3D acceleration is installed and it will be emulated by software. And yes, it was slow! I was under the impression that this GPU should be able to slay these two programs.

As a sidenote, I'm using whatever default drivers the install disk set me up with. I didn't switch from the non-canonical to nVidia drivers. I tried this before, and my system froze constantly.

I would appreciate any help that anyone can provide in terms of what/where to check to see if my card is working correctly.

---

### Post by Just A # on 2009-11-17
What capabilities of my GPU are being used? Is all 3D being done using OpenGL? How can I check?

---

### Post by Just A # on 2009-11-17
Well, I strongly recommend you not activate the "nvidia accelerated graphics driver (version 185)" if you have the same configuration as me...

***look at all the pretty colours!!!***

---

### Post by Just A # on 2009-11-17
[FONT=Arial][SIZE=2]I'm having a great conversation with myself!

I forgot to mention in my last post that I just upgraded to Xubuntu 9.10. I should probably change my signature as well.

Anyways, as I mentioned earlier I gave the proprietary nvidia driver a try (the ones that Xubuntu could find using the Applications>System>Hardware Drivers" utility). Three drivers were listed: NVIDIA accelerated graphics driver - versions 96, 173 and 185, with version 185 being the recommended driver. I tried all three drivers, and all three drivers after restart (required) failed. I didn't see splash screens or anything before my entire screen was filled with irregular patterns of colour (with 96 + 185) or black/white/grey with version 173. A hard reboot was the only solution that I managed to figure out to start over.

On restart, I pressed <esc> when prompted to enter GRUB. From the menu I chose the root commandline option and ran the following commands as suggested by this link:
[/SIZE][/FONT]
[http://blog.danfego.net/2009/11/fixing-nvidia-driver-issues-on-ubuntu-karmic/](http://blog.danfego.net/2009/11/fixing-nvidia-driver-issues-on-ubuntu-karmic/)

[FONT=Arial][SIZE=2]note* I didn't use sudo since I was already root[/SIZE][/FONT]

[FONT=Courier New][COLOR=Blue]root@computer~/: jockey-text -l[/COLOR][/FONT]

[FONT=Arial][SIZE=2]which told me about the three versions of NVIDIA drivers that were available, and in each case which was activated. By the way, Jockey is the name of the program that looks after these vender hardware drivers. I'm assuming jockey-text is the commandline version of the same.
[/SIZE][/FONT]
[FONT=Courier New][COLOR=Red]xorg:nvidia-173 - NVIDIA accelerated graphics driver (Proprietary, Disabled, Not in use)
xorg:nvidia-185 - NVIDIA accelerated graphics driver (Proprietary, Disabled, [/COLOR][/FONT][COLOR=Red]Enabled, In use[/COLOR][FONT=Courier New][COLOR=Red])
xorg:nvidia-96 - NVIDIA accelerated graphics driver (Proprietary, Disabled, Not in use)[/COLOR][/FONT]

[FONT=Arial][SIZE=2]since the above linked article was about enableing a driver using the[/SIZE][/FONT] [FONT=Courier New][COLOR=Blue]-e[/COLOR][/FONT] [FONT=Arial][SIZE=2]flag, I guessed[/SIZE][/FONT] [FONT=Courier New][COLOR=Blue]-d[/COLOR][/FONT] [FONT=Arial][SIZE=2]would work for disableing *fingers crossed*[/SIZE][/FONT]

[COLOR=Blue]root@computer~/: jockey-text -d xorg:nvidia-185

[COLOR=Black][FONT=Arial][SIZE=2]I was then able to reboot[/SIZE][/FONT]

[FONT=Courier New][COLOR=Blue]root@computer~/: shutdown -r now[/COLOR][/FONT]

[FONT=Arial][SIZE=2]where shutdown was the command, -r meant restart, and now = now!
[/SIZE][/FONT][/COLOR][/COLOR]

---

### Post by Just A # on 2009-11-17
One more thing,

Since Chess kept crashing, I uninstalled it using the Applications>Add/Remove Applications utility (it removed all of my installed games). I then reinstalled just Chess, and it started up in 3D mode! recall, switching to 3D mode was the last thing that I did before it crashed every time before I had the chance to do anything. Somehow, the setting of 3D survived the uninstalling procedure. However, it was painfully slow, so I will assume that the 3D rendering is being done by OpenGL or something... but at least it isn't crashing!

---

### Post by Just A # on 2009-11-19
...by the way, I have recommended merging this thread that I started with

[http://ubuntuforums.org/showthread.php?t=1328043](http://ubuntuforums.org/showthread.php?t=1328043)

Since it had a catchier title, involving the actual GPU that need configuring instead of the whole video card, I will be posting to that thread instead (until they are merged)

Although, perhaps a title like "pppppppppPlease HELP ME!!!!!!!!" without any info about what the thread was about would have been better. It worked for someone!

---

