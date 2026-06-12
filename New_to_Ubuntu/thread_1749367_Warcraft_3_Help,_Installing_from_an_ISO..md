---
title: "Warcraft 3 Help, Installing from an ISO."
date: 2011-05-04
forum: New to Ubuntu
---

### Post by Turtlicious on 2011-05-04
Hi,I am running Ubuntu, the latest one Unix (11.04 Ubuntu default) I have downloaded a Warcraft 3 ISO and would like a step by step guide as to how to Mount it, Install it, and run it.
 
I am using an old CD key, so I don't even know if I can update
 
I had almost everything done I used Acetone ISO to mount it, I installed it fine with wine, and finally when it came time to play I got the No cd in CD tray error
 
I have seen plenty of threads explaining this. But none were primarily focussed on JUST installing it from a mounted ISO.
 
I am not familiar with the terminal, and just switched from XP saturday.
 
(Mostly because I had 7 tried to install XP from a usb drive and ended up formatting my hard drive D: In the end I didn't want to pay for the install CD so I installed Ubuntu and LOVE IT)
 
I have an ASUS EEE PC P1001x
 
If someone could help me with nub friendly instructions and I'd be really appreciative, as I've been lurking the forums since Saturday looking for tips that would help me.

---

### Post by MasterProg on 2011-05-04
I could be wrong, but the latest patch doesn't have copy protection any more. Just go ahead and install it. :)

---

### Post by Turtlicious on 2011-05-04
Ahh... I did not know that...
 
I have AT&T the cheapest one, so I will tell you if that worked in...
 
5 hours...
 
Maybe I should just do it from starbucks... 
 
Thank you so much though Prog I did not know that.

---

### Post by Turtlicious on 2011-05-04
```
justin@justin-1001PX:~$ wine /home/justin/.wine/drive_c/Program\ Files/Warcraft\ III/Warcraft\ III.exe -opengl
Warning: could not find DOS drive for current working directory '/home/justin', starting in the Windows directory.
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x33f108,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5d4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f60c,0x00000000), stub!
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  17 (XF86VidModeGetGammaRamp)
  Value in failed request:  0x4800006
  Serial number of failed request:  1261
  Current serial number in output stream:  1261
```

Now what do I do? I was able to start the game, but all the textures were removed... So, I searched the forums for the answer... it told me to try the code at the top it didn't work.

---

### Post by Turtlicious on 2011-05-05
I feel awful for bumping but I really want this to work could someone please help me?

---

### Post by skyline-racer on 2011-05-05
Are you running the game from a NTFS formatted drive? It could cause problems if you are. 

If so, try coping it to your linux drive and running it then. Otherwise i would try re-installing it and using a NOCD patch from gamecopyworld.com providing that it is a legal copy of the game your using. That would solve the CD error.

---

### Post by Turtlicious on 2011-05-05
I used the blizzard Patch, I installed it through wine and yes it's the hard drive Linux is installed on.

Is there anything else you could reccomend?

I am using two monitors if that changes anything

---

### Post by Turtlicious on 2011-06-16
Solved the problem, I ran it through windowed mode and everything went fine, also used -openGL and re-installed it.

^~^

Thank you MasterProg and SkylineRacer.

---

