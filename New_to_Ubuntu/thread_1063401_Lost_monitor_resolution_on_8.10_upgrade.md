---
title: "Lost monitor resolution on 8.10 upgrade"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by skootar on 2009-02-07
My monitor was working fine at 1600x1200 on 7.xx.
After going through all the upgrade steps to get to 8.10 I no longer have that resolution, only lower ones. My monitor is shown as Unknown in the screen resolution program. Need advice here thanks.

---

### Post by paydaydaddy on 2009-02-07
First make sure that you are using the best drivers for your graphics card, then follow this guide. 

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

### Post by skootar on 2009-02-07
I cycled the power on the computer and the monitor is recognized and I have the 1600 x 1200 again.

---

