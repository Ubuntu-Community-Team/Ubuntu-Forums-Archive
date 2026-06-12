---
title: "Filling Screen on 22&quot; Monitor"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by R@inm@n on 2009-01-30
I have a 22" Samsung monitor and i'd like to be able to use it all. Unfortunately, Ubuntu only fills some of the monitor screen, there is a 2" black area both sides of my Ubuntu desktop picture.

How do I get Ubuntu to use the whole 22" screen?


Thanks,


 R.

---

### Post by LieToPurify3 on 2009-01-30
Sounds like you're not using the correct monitor resolution.  Try going to System > Prefs > Screen Resolution.  If your native resolution isn't there, then you'll have to try to install the drivers for your video card.

---

### Post by R@inm@n on 2009-01-31
My resolution is set at the maximum available in system prefs.
I already tried activating the ATI video drivers and they don't work correctly. I can't seem to get anywhere with this video card thing, and I have been trying for a long time.
Windows has no problem with my video card or drivers, and I can use my monitor at full res and full screen.

If anyone out there is running HH on a bigger screen at full res and using an ATI card with full screen pictures, i'd love to hear from you.

Thanks...


R.

---

### Post by paydaydaddy on 2009-01-31
You will need to set to the native resolution of your monitor. If you don't know it you can easily look it up via google search by brand name/model #. The following guide got me to the correct resolution on my system.
Question:
I Installed my graphics card driver, but I still can't get the proper screen resolution! What do I need to do?

Sometimes you will need to configure the X Server. It often can't display any larger than 1024 x 768. Here is a quick way to do so. 

   1. Open up a shell terminal session
   2. Type in the following command:
      Code:

      sudo dpkg-reconfigure -phigh xserver-xorg

   3. Enter your password at the prompt. You will notice it won't actually show up on the screen, this is normal.
   4. You will now be shown a GUI. Select your graphics chipset. If you don't know, use Everest and go to Display > GPU. Press enter to continue.
   5. Now select the resolution of your monitor. You can select as many as you need. Use the space bar to put an asterisk next to a resolution.
   6. Once you are back to the terminal, exit out of the session and reboot to restart the X Server. It should now display the correct resolution.

---

### Post by R@inm@n on 2009-01-31
Sorry, I didn't get the GUI...

I copied and pasted your command, here is what I got:

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090201124711

That's it.


R.

---

### Post by R@inm@n on 2009-01-31
Whoa!!  Hang on, I did it...:D

Thank you Sir, this is the first time I have ever been able to get this result on Ubuntu since I started.

I appreciate you help.


Rainman.

---

### Post by WillieMaysHayes on 2009-01-31
This thread has me interested in my own Ubuntu box that I'm about to upgrade my monitor on to a 22" widescreen.  By any chance are you having issues with the ATI Radeon HD 3200?

---

### Post by blackened on 2009-01-31
There was probably a setting in xorg.conf that wasn't correct. sudo dpkg-reconfigure -phigh xserver-xorg doesn't do anything but wipe clean your xorg.conf and restore it to the state it was at install. Reconfiguring hasn't allowed you to select changes in graphics settings since gutsy.

Often you only need to add your monitor's hsync and vrefresh ranges to xorg.conf to fix incorrect monitor recognition.

---

### Post by R@inm@n on 2009-02-02
Agreed, that was most likely the cause of my problems.

As a novice Linux user I make /made many mistakes.

However, I have full-screen graphics at last, and the Heron is flying along nicely...:D

To WillieMaysHayes ....  My graphics card is an old ATI 9600XT with 256 Ram, but it works ok for most things.


 R.

---

