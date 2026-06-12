---
title: "Configuring screen resolution and refresh rate"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by ffifield on 2009-02-08
I am having trouble changing the resolution and refresh rate on a Viewsonic P225 monitor powered by an nVidia GTX280 video card. I installed the nVidia driver and restarted my box. I went into System > Administration and saw something called "nVidia X Server Settings", but the maximum resolution it will allow me to choose is 1152 x 864 and the only refresh rate available is 60Hz. The same is true if I go to System > Preferences > Screen Resolution.

What do I need to do to be able to choose a higher resolution and refresh rate? Thank you for your help!

---

### Post by ffifield on 2009-02-08
Bump.

Can somebody please help me?

---

### Post by Declanthedork on 2009-02-08
It's possible that that's the highest resolution that the monitor can go. That's what happened on my other computer. Have you used it with a different OS and been able to go to a higher res?

---

### Post by paydaydaddy on 2009-02-08
Try this guide. It worked for me.

I Installed my graphics card driver, but I still can't get the proper screen resolution! What do I need to do?

Sometimes you will need to configure the X Server. It often can't display any larger than 1024 x 768. Here is a quick way to do so. Note: You will need to be logged in as a root user.

   1. Open up a shell terminal session
   2. Type in the following command:
      Code:

      sudo dpkg-reconfigure -phigh xserver-xorg

   3. Enter your password at the prompt. You will notice it won't actually show up on the screen, this is normal.
   4. You will now be shown a GUI. Select your graphics chipset. If you don't know, use Everest and go to Display > GPU. Press enter to continue.
   5. Now select the resolution of your monitor. You can select as many as you need. Use the space bar to put an asterisk next to a resolution.
   6. Once you are back to the terminal, exit out of the session and reboot to restart the X Server. It should now display the correct resolution.

---

### Post by ffifield on 2009-02-08
> **Declanthedork said:**
> It's possible that that's the highest resolution that the monitor can go. That's what happened on my other computer. Have you used it with a different OS and been able to go to a higher res?

Yes. In other OS's I use 1600x1200 with a refresh rate of 75Hz.

---

### Post by ffifield on 2009-02-08
> **paydaydaddy said:**
> Try this guide. It worked for me.

I Installed my graphics card driver, but I still can't get the proper screen resolution! What do I need to do?

Sometimes you will need to configure the X Server. It often can't display any larger than 1024 x 768. Here is a quick way to do so. Note: You will need to be logged in as a root user.

   1. Open up a shell terminal session
   2. Type in the following command:
      Code:

      sudo dpkg-reconfigure -phigh xserver-xorg

   3. Enter your password at the prompt. You will notice it won't actually show up on the screen, this is normal.
   4. You will now be shown a GUI. Select your graphics chipset. If you don't know, use Everest and go to Display > GPU. Press enter to continue.
   5. Now select the resolution of your monitor. You can select as many as you need. Use the space bar to put an asterisk next to a resolution.
   6. Once you are back to the terminal, exit out of the session and reboot to restart the X Server. It should now display the correct resolution.

In step 4 I am not shown a GUI. After I enter my password I get this message:
 "xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20090208180244"
The terminal then reverts to the prompt.

And thank you all for your replies!

---

### Post by paydaydaddy on 2009-02-08
Go to system > preferences > Screen resolution and see if you have additional options in the drop down list. You may need to restart x.

---

