---
title: "video driver borked - guidance please"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by tsco59 on 2010-02-22
I have an NVIDIA GeForce Ti200 vid card.  Highest Ubuntu resolution is 800x600.  In WinXP I could go as high as 2048x1536.  Hardware Drivers gave me no driver options so I downloaded from NVIDIA their linux driver for this legacy card.  Hardware Drivers then offered a new driver which I installed, ran nvidia-xconfig as root as directed, restarted x server and system is un-usable.  I chose to re-install Ubuntu for clean environment.  I'm guessing the driver was not a good choice.  Any suggestions?  All I really want is higher resolution such as 1024x768.  What should I have done?  Thanks in advance.

---

### Post by cariboo on 2010-02-22
It looks like the driver for you graphics adapter is the 190.53, is that the driver you tried to install?

---

### Post by JiuJitsu500 on 2010-02-22
Sometimes some video card memory isn't accepted at ALL with any new drivers (mostly the ATI 3650 I think) but I think I saw a NVidia card do it once... where it would only boot in safe mode. Sometimes 2GB of RAM is all it will recognize and I'm not sure why, but on the LaunchPad bug reports there was talk that until something new happens (possibly to ba added in Lucid amongst a whole slew of other new small things, like drivers).... The only way to solve it is by removing all but 2GB of RAM.

More than you'll ever really need, but I do know how annoying it is knowing you had 3 or 4, or more, and can only have 2 in the computer :(

I don't know if this will solve your problem, but it solved it more than a few times for me (don't tell the owners though... they still love ubuntu and don't know anything).

---

### Post by tsco59 on 2010-02-23
I installed 96.43.16 because the Ti200 was listed as supported.  Now that I re-installed the Ubuntu and did the recommended updates, my resolution dropped to 640x480.  I'm going backwards.  Will try 190.53 next.  Thanks

---

### Post by tsco59 on 2010-02-23
Ok, downloaded 190.53 filename: NVIDIA-Linux-x86-190-pkg1.run

I'm not sure how to install it.  It is in my downloads folder.  Double clicking on it yields the following error:  Could Not Open... gedit has not been able to detect the character coding.  Please check that you are not trying to open a binary file...  (I think it is a bin file).

Thanks in advance

---

