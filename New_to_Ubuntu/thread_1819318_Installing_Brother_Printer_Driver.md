---
title: "Installing Brother Printer Driver"
date: 2011-08-05
forum: New to Ubuntu
---

### Post by rancid98 on 2011-08-05
I have a Brother HL-2070N and have downloaded the driver for 11.04 from brother (brhl2070nlpr-2.0.1-1.i386.rpm). I looked at the instructions for installing it at Brother's website and am aware it must be installed from the terminal, but my understanding end there. I know I have CUPS installed and looked at the cupswrapperdriver, but the instructions for installation may well have been in French. The pre-required procedure indicates I have to have other drivers installed, but have no idea how to check if they are installed, or even how to install the driver I have. I looked at the LPR driver, but did not have much more success either. Sorry for probably asking some very stupid questions, but I have been trying to help myself with searches on the net for over a week now and am no closer to finding an answer.  Thanks for any assistance.

---

### Post by fcorourke on 2011-08-05
Hi -- I always hate to upgrade as you always have to re-install the printer & scanner. It takes me a weekend most times just keep reading the directions & do all the test for what is installed & it will all of the sudden work!! .. I love Ubuntu & hate this aspect. Pure junk, but brother does have plenty of how too's they at least care & try.. It is finding the correct install procedure, you can not find on forum itself, you have to Google & come back into the forums for directions. Sorry I can not help more, but someone will, I have to do this weekend :-( 

    Fred

---

### Post by rancid98 on 2011-08-06
Always the way - I get it right after I ask for help.  I read the instructions at Brother slowly and carefully, putting sudo in front of all the commands and it worked.

Thanks for tolerating my stupidity.

---

### Post by BDNiner on 2011-08-06
I agree, Brother printers are such a pain. The steps from brother's site work it is just that they seem overly complex for installing a printer and scanner driver.

---

### Post by relay_man on 2011-08-06
I'm glad you got the driver to install!

Help others by using thread tools and marking this thread [COLOR="Red"]Solved[/COLOR]  :)

---

### Post by fcorourke on 2011-08-06
I just had to say I did not loose my printer when upgrading from 9.04 to 10.04 :-) :-) :-))   THE FIRST TIME IT HAS EVER HAPPENED I AM PLEASED VERY MUCH -- WAY TO GO UBUNTU

     Fred

---

### Post by cjazz on 2011-08-06
I'm glad you got your driver installed. Personally, I find the Brother instructions pretty straightforward, but for an easier solution, go to Synaptic and type "Brother HL-2070N" into the search box. If I'm not mistaken, Ubuntu has the packages "brother-cups-wrapper-laser" and "brother-lpr-driver-laser" available for automatic install.

---

### Post by rewyllys on 2011-08-06
> **fcorourke said:**
> Hi -- I always hate to upgrade as you always have to re-install the printer & scanner. . . .
You can probably avoid the necessity of reinstalling printer and scanner following an upgrade if you will move your "/home" folder to a separate partition from your "/" folder.  

FWIW, this works for me.:p

If you are unfamiliar with how to set up separate partitions, there are several threads in these forums that explain the procedures.  Good luck!

---

