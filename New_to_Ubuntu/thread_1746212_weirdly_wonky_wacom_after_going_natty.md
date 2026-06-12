---
title: "weirdly wonky wacom after going natty"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by hamishmacd on 2011-05-01
I'm a complete beginner. After upgrading to Natty my Wacom Intuos 3 started to behave strangely.  
 

 Initially all worked well with the exception that the actions of 2 pen buttons were the wrong way round. I had encountered this before and thanks to these forums I found the answer to be editing the  usr/share/X11/xorg.conf.d/50-wacom.conf file to read as below.
 

 Finding these command not present after the upgrade, I reinstated them;-  
 

 Option "Button1" "1" 
 Option "Button2" "3" 
 Option "Button3" "2" 
 

 This didn't have the desire effect. Now, if I place my pen on the extreme left edge of the tablet, moving the pen 1cm to the right takes the cursor way off to the right hand edge of the screen. Moving the pen up and down results in the cursor moving wildly across the screen.
 

 Any suggestions welcome.  
 

 Section "InputClass" 
     Identifier "Wacom class" 
 # WALTOP needs a patched kernel driver, that isn't in mainline lk yet, 
 # so for now just let it fall through and be picked up by evdev instead. 
 #    MatchProduct "Wacom|WALTOP|WACOM" 
     MatchProduct "Wacom|WACOM" 
     MatchDevicePath "/dev/input/event*" 
     Driver "wacom" 
     Option "Button1" "1" 
     Option "Button2" "3" 
         Option "Button3" "2" 
         Option "KeepShape" "on" 
 EndSection 
  
 Section "InputClass" 
     Identifier "Wacom serial class" 
     MatchProduct "Serial Wacom Tablet" 
     Driver "wacom" 
 EndSection 
  
 Section "InputClass" 
         Identifier "Wacom serial class identifiers" 
         MatchProduct "WACf|FUJ02e5|FUJ02e7" 
         Driver "wacom" 
 EndSection 
  
  
 # N-Trig Duosense Electromagnetic Digitizer 
 Section "InputClass" 
     Identifier "Wacom N-Trig class" 
     MatchProduct "HID 1b96:0001|N-Trig Pen" 
     MatchDevicePath "/dev/input/event*" 
     Driver "wacom" 
      
  EndSection

---

### Post by Favux on 2011-05-01
Hi hamishmacd,

Welcome to Ubuntu forums!

First try removing *Option "KeepShape" "on"* or commenting (#) it out.  I'm pretty sure its functionality was removed or broken by xf86-input-wacom-0.10.11, which is the default version in Natty.  They disabled the Option with a commit a week or two after 0.10.11 came out.

Also:
```
Option "Button1" "1"
Option "Button2" "3"
Option "Button3" "2" 
```
should be the driver defaults now.  They switched the Button2 & 3 assignments quite a while ago because users requested it.  So try commenting them out or removing those lines too and restarting.

---

### Post by hamishmacd on 2011-05-02
It works! Thank you very very much.

---

### Post by Favux on 2011-05-02
Great!  :)

---

