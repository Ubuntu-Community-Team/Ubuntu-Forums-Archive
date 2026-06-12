---
title: "World of warcraft"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by chadbentley8 on 2009-01-14
I've tried installing WOW. i looked it up and did all the tweaks and everything that a few threads said to do, unfortunatly my launcher loads up and i click "play" then the launcher closes and nothing happens. Before i did any tweaking, when my launcher closed my screen resolution would change and i'd get a bunch of white lines across my whole screen. now, not even that happens. could anyone help me out?

---

### Post by utnubuuser on 2009-01-15
Can't help you here, but it's probably a good idea to give a little more info.  --What exactly did you do?  Did you have to add a line to wine.conf at some point?
What have you tried?
There are some help threads at wineHQ too.

---

### Post by hyper_ch on 2009-01-15
I used this here:

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

I did have an install on windows and just copied that over and did necessary changes. Also I used the wine repos to get more up-to-date versions of wine.

---

### Post by chadbentley8 on 2009-01-15
Thats what i used too Hyper. but still it doesnt run :(

---

### Post by hyper_ch on 2009-01-15
well, I haven't tried with Lich King....

---

### Post by LowSky on 2009-01-15
if its on Turn off Compiz, it can sometime effect games that need graphics support, right click on desktop, choose change background, go to the tab called advanced graphics turn off eye candy (should be the tab all the way to the right). Sorry I'm on a Windows PC

If you need to turn compiz off and on more often install the fusion-icon, from synaptic. It installs a program that can sit in the system try so you can instantly turn compiz off or on. I use it alot

---

### Post by chadbentley8 on 2009-01-15
Tried that out lowsky, i do have compiz. turned all effects off. Launcher opens fine, click play and my resolution goes from 1280x800 to 1024x768 and no WOW. just sits like that till i change the reso back.

---

### Post by chadbentley8 on 2009-01-15
im trying to Play lich king by the way. if that is any different then the first 2

---

### Post by floatingpoint on 2009-01-15
this could be a blessing in disguise, bud

---

### Post by chadbentley8 on 2009-01-16
ok, i've reinstalled/updated wine. reinstalled WOW. i have tweaked absolutly nothing. wow opens up to the intro movie, it plays through, when its done playing  (or when i hit enter or esc to skip the vid) it crashes and takes my to my login screen.

---

### Post by chadbentley8 on 2009-01-16
UPDATE:

i copied the config file from my desktop (where i play wow) to my laptop (where im trying to get it to run using ubuntu) and i added these lines 

SET gxApi "opengl"

when i added this i still had the game crashing on my after the intro so i added

SET ffxDeath "0"
SET ffxGlow "0"

now i can get to the login page of WOW. but, the login is all messed up, distorted, the colours are right, but i cant read any words and the background looks like a collage of squares and triangles

anyone know what is going on?

---

### Post by Zeroberry on 2009-01-16
Could be your graphics drivers, have you installed proprietary drivers?

---

### Post by chadbentley8 on 2009-01-16
umm im not sure, im gonna say no since i dont know how to do that. mind telling me?

---

### Post by chadbentley8 on 2009-01-16
update:

i've been looking at this:

[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting)

and i did this:

f you have troubles running the installation or even the game itself, you may need to get a few .dll files from a windows installation or here:

    *

      msvcp60.dll (MD5: 6050bcc1b23f3df7a1876cbdcbac8232)
    *

      mfc42.dll (MD5: 7e4d1b552ee1dfa859ba9033b3670590)
    *

      riched20.dll (MD5: 878f0ebc1bef45694311f7d4f7fe3344)
    *

      riched32.dll (MD5: 804d815826fe00d6471c72d8299fcbb5) 

    *

      and place them in /home/<username>/.wine/drive_c/windows/system32. You will, however, need a Windows license to use these files.

      Note: Remember to change <username> to your personal computer login username


now the game doesnt even open.

i tried opening in terminal and this is what it read:

chad@chads-laptop:~$ wine c:/program\ files/world\ of\ warcraft/wow.exe
fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\expansion.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x39edbc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ebe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f2d8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f434,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f59c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f530,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f520,0x00000000), stub!
X Error of failed request:  GLXBadDrawable
  Major opcode of failed request:  157 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  588
  Current serial number in output stream:  588
chad@chads-laptop:~$

---

### Post by chadbentley8 on 2009-01-18
bump.

---

### Post by chadbentley8 on 2009-01-25
im still having problems, nothing seems to be working..

---

### Post by S0m3th1ngw13rd on 2009-01-25
I was having same issue. I went to wine config
graphic tab and checked the box that said  emulate a virtual desktop. Then set it to Resolution of my desktop.  After this when I log into game I changed in game video resolution to match the emulated resolution in wine config. This worked for me.

---

### Post by flicman on 2009-08-24
I know it's been a long time on this one, but I was having the same problem with my new Laptop (the ghetto Toshiba L355) and doing 'winecfg' and then UN-checking "Allow Pixel Shader (if supported by hardware)" solved my problem.

---

