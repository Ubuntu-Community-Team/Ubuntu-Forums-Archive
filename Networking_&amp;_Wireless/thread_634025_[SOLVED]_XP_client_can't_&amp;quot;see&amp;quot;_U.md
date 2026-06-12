---
title: "[SOLVED] XP client can't &amp;quot;see&amp;quot; Ubuntu"
date: 2007-12-07
forum: Networking &amp; Wireless
---

### Post by Purplecatty on 2007-12-07
in past week,  I reinstalled Ubuntu Gusty Gibbon on one of my system because I installed SuSE 10.3 and didn't like it.  I had it networked with my wireless laptop including file and print sharing without any problem.  After reinstalling Ubuntu,  I forgot to set up file and print sharing for week.  Then yesterday, I finally did and set up according to what I did in past.  Ubuntu can "see" XP client (my laptop) just fine.  I also set hp psc 2175 printer to share ( set as print server).  I went upstair to reconfigure my laptop to use networked printer.  It can't see Ubuntu, neither Ubuntu's printer.  XP client have basic firewall running.  I clicked Window's firewall to allow file and print sharing.  It still won't "see" it.  I even reconfigured Network setup (chose Router as a "hub" like I did before).  It still don't work.  It struck me odd that Ubuntu "see" and able to manuplate XP's file.  

MY other system which is a Gigabyte XP client did have same problem ( it have not been touched ).  It did have same problem.  I wonder is Ubuntu's Samba crashed or corrupted?

Can you give me suggestion?

Thanks
Catty

---

### Post by jonandrews on 2007-12-07
I've done a step-by-step illustrated guide showing how to network Ubuntu & Windows PC's, biased towards people more familiar with Windows.

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

Let me know if it works for you..

---

### Post by Purplecatty on 2007-12-07
THanks for the info!! I finally got SAMBA fixed.   Right after I posted forum and It popped in my mind that SAMBA must be corrupted.  I decided to go to Synapic Manager and find "SAMBA" and on SAMBA's radio button which was selected,  I clicked right mouse and choose "Mark for Reinstallation".  I re-installed SAMBA and related files (I added SAMBA GUI for pleasure).  After re-installing,  it finally worked!!!!  On "Places---Network",  I saw "Acer" and "XXXX-Desktop", ("Acer showed but not "XXXX-desktop" prieviously) finally showed..  I realized that SAMBA was corrupted  which I was struggling over nothing.  I wish I should have not posted it first place when I had option to reinstall SAMBA.  But gladly you provided good information that I could bookmark!!

Next time if SAMBA got corrupted.  I would do re-installation.

It would be good idea for Forum community to learn something new on SAMBA problems. Hope this will help everyone on their last nerve.

Ubuntu Rocks!!! :guitar: :lolflag: 

Catty

---

