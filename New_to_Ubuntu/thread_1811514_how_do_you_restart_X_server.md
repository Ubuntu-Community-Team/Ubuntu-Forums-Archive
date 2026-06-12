---
title: "how do you restart X server?"
date: 2011-07-25
forum: New to Ubuntu
---

### Post by 007casper on 2011-07-25
how do you restart X server?

---

### Post by phosphide on 2011-07-25
I'm assuming you need to reset your graphic settings correct?

1. Restart your computer. 
2. When you get to the grub loading screen hit the Esc button. 
3. Arrow down to recovery mode.
4. Select "Boot into Low Graphics Mode" I believe this is the option, sorry if I got the name wrong.
5. From there, you will be prompted with a window that will allow you to restart your x server.
6. Restart your computer again.

If you are doing something else, then just ignore everything I just said. :D

By the way, I just noticed your talking about kubuntu. The options might be a little different, though I believe it's generally the same process.

---

### Post by 007casper on 2011-07-25
is it "/etc/init.d/gdm restart" ?

I am having nvidia driver issues.  The computer wont boot up with the graphics card installed.  

I removed the graphics card.  I also removed nvidia driver and reinstalled the drivers.  

I got a pop up window that stated to do nvidia-xconfig as root.  Then, restart X server. So, I did sudo nvidia-xconfig.

last time, instead of restarting X server, I turned off the computer.  Then, I installed the video graphics card, and I reboot the computer.  However, it just hangs.  So, I took out the video card again, and then reinstalled the nvidia driver.  This time instead of rebooting the computer, I just wanted to restart X server.

Please, help out.  Thank you.

---

### Post by 007casper on 2011-07-25
@phosphide - I am going to try that.  However, the 'puter doesnt even boot.  It just hangs.  I am going to hit escape and hope for the best.

by the way, etc/init.d/gdm restart doesnt work

---

### Post by 007casper on 2011-07-25
no, it doesnt work. I cant get a x server scren through escape with this monitor.  I just get a dark screen, or a screen with bunch white bars.

After the recent update I cant get the computer to boot up with the graphics card. If I take out the graphics card, and boot through on board video card, then it works but I get a low resolution.  

However, the monitor is a cinema display, and the onboard video processor doesnt work that high resolution.  So, I need it to work with video/graphic card.

And, when I install the graphics card, it just doesnt boot.

???

---

### Post by kaldor on 2011-07-25
Which NVIDIA graphics card do you have? Use the *lspci* command to find out, if you are unsure.

---

### Post by Wim Sturkenboom on 2011-07-25
Which videocard?

I suspect that the nvidia driver is not going to help at this stage as the issue might be before that driver will be loaded; not sure however.

First step might be to edit the grub entry that you use so you can see what is happening.
press 'e' on the line in the grubmenu that you want to use
[LIST=1]
[*]go to the line that contains '*quiet splash*'; it's a long line and might show as two lines on the screen
[*]remove those words so you're no longer blind
[*]press <ctrl>X (that is control plus X) to boot; it will still 'hang', but you can now see where (you can post the last line that is on the screen)
[/LIST]
You can also replace '*quiet splash*' by '*nomodeset*' (without the ticks); this will disable the nouveau video driver. It might solve the boot issue and get you to the graphical login. If it works, you can make this change permanent and after that start working on the nvidia driver.


PS, with kubuntu it's probably kdm instead of gdm, so you can try that.

---

### Post by kaldor on 2011-07-25
> **Wim Sturkenboom said:**
> You can also replace '*quiet splash*' by '*nomodeset*' (without the ticks); this will disable the nouveau video driver. It might solve the boot issue and get you to the graphical login. If it works, you can make this change permanent and after that start working on the nvidia driver.

Ah yeah, I had to do that when I was installing Fedora 15's NVIDIA drivers.

---

### Post by wildmanne39 on 2011-07-25
Hi, may also be able to boot using nomodeset, here is a link for that.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

You can restart xsever with this command.
```
sudo service gdm restart
```
or you can do this and get rid of the config file and start over, this is if you are using natty.
```
sudo rm /etc/X11/xorg.conf
```
```
 sudo dpkg-reconfigure xserver-xorg
```

---

### Post by 007casper on 2011-07-25
lspci
```

02:00.0 VGA compatible controller: nVidia Corporation GT218 [ION] (rev a2)                                                       
02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
```

thank you so much everyone.  I edit grub permanently. nomodeset didnt work for me.

at one point, I will remove quiet splash and try it again, to see last line that is on the screen

However, it works now... 
```

GRUB> echo $linux_gfx_mode
GRUB> echo $gfxmode
GRUB>  set gfxmode=2560x1600
GRUB> load_video (this line didnt work for me)
GRUB> insmod gfxterm
GRUB> vbeinfo
```

append/adding a vga=xxx, where xxx is the mode. 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vga=0x101"

---

### Post by wildmanne39 on 2011-07-25
Hi, glad you have it working would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by 007casper on 2011-07-26
Sure. Marked solved. Thank you so much everyone.

---

