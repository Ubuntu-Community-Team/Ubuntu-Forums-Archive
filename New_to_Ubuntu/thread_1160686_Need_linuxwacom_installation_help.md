---
title: "Need linuxwacom installation help"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by Turtleman on 2009-05-15
Ok so I've got a Bamboo tablet and I went to the linux wacom site and tried to follow their HOWTO for a couple hours until I got nowhere. Can someone explain to me easily how do I get my Bamboo tablet running with pressure sensitivity and all? Or at least show me where I can find a somewhat easy to understand tutorial? I am using 9.04. Also, if someone knows a way that I can undo what I did with the linuxwacom, I'd appreciate that too.

Thanks for your time

---

### Post by Turtleman on 2009-05-15
I know I should be ashamed for bumping myself, but configuring my tablet is stressing me. And I really need to use it. Someone help?

---

### Post by Favux on 2009-05-15
Hi Turtleman,

First type these two commands in a terminal:
```
sudo apt-get install wacom-tools xserver-xorg-input-wacom
sudo apt-get purge wacom-tools xserver-xorg-input-wacom
```
Then change directory into the unpacked linuxwacom tar you used.  Then change directory into the "prebuilt" folder.  Then in a terminal:
```
sudo ./uninstall
```
Then go to "/lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko" where "uname -r" is your current kernel; 2.6.28-?.  You could probably delete the wacom.ko you find there but to be sure move it somewhere safe and rename it.  If you need the 0.8.2-2 linuxwacom packages' wacom.ko you can get it by reinstalling your kernel's "linux-image" (it has the kernel modules) in Synaptics.  Go to Synaptics and reinstall the 0.8.2-2 xserver-xorg-input-wacom and wacom tools.

Now you have to replace the current 10-wacom.fdi with a modified one.  Go to post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)

That should get you set up and working.  If you read into the thread another few pages there will be info. specific to setting up the Bamboo's pad.

Good luck!

---

### Post by Turtleman on 2009-05-15
Thank you, I really appreciate your help! Gonna try right away

---

### Post by Turtleman on 2009-05-15
> **Favux said:**
> Hi Turtleman,

First type these two commands in a terminal:
```
sudo apt-get install wacom-tools xserver-xorg-input-wacom
sudo apt-get purge wacom-tools xserver-xorg-input-wacom
```
Then change directory into the unpacked linuxwacom tar you used.  Then change directory into the "prebuilt" folder.  Then in a terminal:
```
sudo ./uninstall
```
Then go to "/lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko" where "uname -r" is your current kernel; 2.6.28-?.  You could probably delete the wacom.ko you find there but to be sure move it somewhere safe and rename it.  Hopefully the 0.8.2-2 linuxwacom packages will replace it with their wacom.ko when you install them.  Go to Synaptics and reinstall the 0.8.2-2 xserver-xorg-input-wacom and wacom tools.

Now you have to replace the current 10-wacom.fdi with a modified one.  Go to post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)

That should get you set up and working.  If you read into the thread another few pages there will be info. specific to setting up the Bamboo's pad.

Good luck!

I followed your instructions and now my tablet works again just as it did when I installed Ubuntu! But I want to know how can I configure its sensitivity and buttons?

---

### Post by Favux on 2009-05-16
Hi Turtleman,

Good!  Assuming you installed the new .fdi, in the same thread go to page 19 and read shatterblast's post #188.  He has a Bamboo also.

And you know about "wacomcpl"?  To learn how to use it see Section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

---

### Post by Turtleman on 2009-05-16
> **Favux said:**
> Hi Turtleman,

Good!  Assuming you installed the new .fdi, in the same thread go to page 19 and read shatterblast's post #188.  He has a Bamboo also.

And you know about "wacomcpl"?  To learn how to use it see Section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

Perfect! Thanks again

---

### Post by Favux on 2009-05-16
Hi Turtleman,

You're welcome.

---

