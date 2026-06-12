---
title: "No Boot Screen for Wubi?"
date: 2011-03-22
forum: New to Ubuntu
---

### Post by Swoopz on 2011-03-22
Hello, I've been looking into linux for a while, and I finally decided to try Ubuntu. I downloaded Wubi and after installing I reboot as prompted, but it just starts up as XP without asking me which OS I want. I have Ubuntu installed, the dual-boot screen thing just won't come up. Any help would be appreciated.

---

### Post by Jonners59 on 2011-03-22
Hi I switched over a year or so ago with 9.10, and whilst I have had a long learning curve and some issues, it has all been well worth it.

Wubi...  first off I suggest using this only for a short while to try it out as the set up tends to limit the size of the install.  I would suggest one of two things.
1. download and burn a CD of the Ubuntu install iso as found on the front page, probably where you got your Wubi from
2. order a copy from the same place.  It is free but does take a while to arrive.  It is a safe option if you are uncertain about downloading and burning iso CDs, as I was

I used the Wubi when I first started and then ran in to trouble with size limits after a few months, just as I was getting in to the swing of things!  So use the proper version, if I may call it that.

Once you have this you have another 3 choices.
1. Use to try Ubuntu, using the "Try Ubuntu" option to see how you get on with it (versus using Wubi for this), or
2. Use the CD in "Try out Ubuntu" mode to repair your GRUB
3. Install the Ubuntu OS and go for it....

Back to your issue.

I would suggest the problem may be that GRUB has not installed correctly or at all, or may not have configured itself correctly.  If you try 1 or 2 above and "mount", that means open the "Directories (Folders) that your Ubuntu is in and then try to fix this by going to Applications, then Accessories, then opening Terminal and typing sudo update-grub  (I suggest copy and paste in to the terminal).  It does the rest.  This may configure the GRUB for you.  It should seek out all the OS on your machine.

If not then you may need to install the GRUB manually.  As a newby I suggest that as the new install has not been used as yet, why not go into your Windows Features settings and uninstall the Wubi and start over?

PS note that HOME is where all your user accounts and info is stored and all your documents.  I managed to set mine up (when I had Windows OS) to share between the two OS
PPS I have assumed you are very, very new to this, apologies if I have come over condescending, but I recall how I was lost with different speak and jargon.

---

