---
title: "Problems connecting my eeepc to my tv"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by CaptainMark on 2011-06-28
Ive recently bought an eeepc 1001 and i love the little gizmo, works so well with ubuntu but im having a little trouble with connecting to the tv, when i plug in via vga cable to the tv then the aspect ratio output from the eeepc to the screen changes to 4:3 so i can view it through the tv screen but with big black bars on either side, obviously when i full screen a 16:9 video i lose a further chunk off the top and bottom so i end up with a screen about half the size of what it should be, if i go to the monitors preferences then the option for a 16:9 screen (which is normally default with no tv attached) has dissapeared off the list so i cannot change it, i want it to output the signal to the tv at the normal aspect of 16:9 so i can use the whole tv screen.

Can anyone help me???

Thanks 
Mark

---

### Post by cariboo on 2011-06-29
The normal native resolution on TVs using the vga input is 1368X768, if you aren't seeing the full screen, check the zoom mode on the TV, on the two LCD's I've connected to I have to set the zoom mode to just scan. I have since upgraded the video card on the Atom 220 powered system and can now use the native 1920X1080 via the HDMI port, I still have to use the just scan setting to get the proper picture size.

---

### Post by CaptainMark on 2011-06-29
if i change the picture size on the television it just streches the 4:3 image sideways and distorts everything, i tried changing the picture size first and plugging the cable in afterwards too, no effect, also tried plugging in with both machines off just in case

---

### Post by CaptainMark on 2011-06-29
after googling a lot all the responses i get say to add an entry for external monitor in xorg.conf which i remember hating playing around with years ago when i made the mistake of buying an ati gpu, but i guess its some way changed now in 11.04 because i cant find the xorg.conf now

---

### Post by CaptainMark on 2011-06-29
im am sure this not a problem with the way my tv is setup but someway ubuntu is at fault in the way the xserver is being run because when i switch to tty1 i get a full screen of the text console in good resolution on my television but as soon i switch back to tty7 it cuts a huge chunk off the sides of the display,

---

### Post by aeiah on 2011-06-29
are you sure your tv can accept above 1024x768 through vga? maybe your only course of action (or perhaps just the easiest) is to put up with a stretched 1024x768 image. if you're just using this for video, then it isnt really a problem. you can use your video player to correct the aspect ratio its self, or use xbmc to do it. i used to use mplayer with aspect ratio correction before putting xbmc on my netbook.

---

