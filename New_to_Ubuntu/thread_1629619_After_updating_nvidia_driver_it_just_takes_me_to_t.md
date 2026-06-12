---
title: "After updating nvidia driver it just takes me to tty1"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by Wurzberger on 2010-11-23
I just installed Ubuntu 10.10 and did a complete update with the Update Manager. After downloading the nvidia drivers and doing a restart it takes me to tty1 where I can log in. ctrl + alt + 7 just brings up a black screen with a flashing _ in the upper left. Im completely new to ubuntu and searched high and low for an answer. Yesterday it was turning off my monitor when it would auto log in, I did something and now I have to type in my log in and password on a normal boot. Your help is much appreciated, I would love to have this computer up and running.

---

### Post by sikander3786 on 2010-11-24
Welcome to the forums :-)

Press and hold down Shift key at Bios screen. Grub menu should pop up. Highlighting the first entry, press 'e' to edit it. Navigate to "quiet & splash", delete them and type "nomodeset" in their place. Press Ctrl + X to continue boot. Can you see the desktop now? If yes, go to System > Administration > Additional Drivers and install/reinstall the Nvidia drivers.

If that doesn't work, try these commands from tty.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

```
sudo rm /etc/X11/xorg.conf
```

No problem if these commands return an error saying xorg.conf doesn't exit. Proceed to the next one.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot

```
sudo shutdown -r now
```

And see if it takes you to the desktop now. If it still doesn't, try reconfiguring your graphics using the nvidia tool (if the Nvidia drivers were installed successfully).

```
sudo nvidia-xconfig
```

Again reboot to see if it worked.

If none of them works, try starting gdm manually and post any errors listed there.

```
sudo service gdm stop
```

```
sudo service gdm start
```

Which graphics card is there?

Good Luck!

---

### Post by Wurzberger on 2010-11-24
None of that worked, still cant see the desktop unless I start it in failsafe graphic mode. Nothing has seemed to change except for after running nvidia-xconfig I saw a "**open /dev/null failed: no such file or directory" **before the log in. The processor is an AMD Athlon 64 X2 Dual-Core 4400+, and the video card is GeForce 6250 SE. 
At some point yesterday I was able to see an error about no display or no monitor when I was typing in about the nvidia settings. Sorry I dont remember what I typed, I have tried a lot of different things lately.

---

### Post by mrnelson1986 on 2010-11-24
If you have an nvidia card it is entirely possible (in fact, likely) that you need to blacklist nouveau and enter "nomodeset" to the boot line (press "e" or "shift" or "tab" based on what version of grub you are using, and add it to the last two lines)

edit: I realize that the poster above said to do the nomodeset option, it is very important, otherwise you will get no GUI under about half of the nvidia cards out here.  My laptop has issues because it is a sony and if I don't blacklist the nouveau and purge it from my system, it will not show a GUI ever.  You can do this by editing files via a terminal on a live CD after you mount your hard drive, if that helps.

---

### Post by Wurzberger on 2010-11-25
After I type in "nomodeset" should it stay there? Its changing back to "quiet splash" every time I restart.
I installed Ubuntu 10.10, would it be easier if I back down to 10.4 or something?

---

### Post by sikander3786 on 2010-11-25
No, you can't de-grade your release to 10.04. It would need a clean install.

If nomodeset fixes that, boot into Ubuntu using that and remove your existing Nvidia drivers, Reboot and put that nomodeset parameter once again. Now install the current/recommended Nvidia drivers. Reboot again and don't use nomodeset parameter this time.

Installing the Nvidia drivers fixes that problem most of the time.

---

### Post by Wurzberger on 2010-11-26
What about for the times that doesn't work? 
While searching through the treads I tried something and got this error doing something.

"(EE) Screen(s) found, but none have a usable configuration.

Fatel server error:
no screens found"

---

