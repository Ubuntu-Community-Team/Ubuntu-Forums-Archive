---
title: "wine trouble.  Please help"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by Sheneron on 2009-05-10
Hi,
I have been trying to get a game going in Wine or Cedega, neither of which will work for me.  I installed the game fine; however, when I go play it keeps saying "Please insert the Play disk."  Well, the play disk is inserted and mounted.  So it doesn't see the disk even if I physically put the disk into the cdrom drive.  Can anyone help please?  Thanks

---

### Post by MontelEdwards on 2009-05-10
What is the name of the game?
Have you looked at wineHQ to see if it is supported or not?

---

### Post by lovinglinux on 2009-05-10
First insert the disc, then open Nautilus and check if the disk is mounted and that you can browse the content. Then start the game. If it doesn't work, then open Wine configuration and check in the "Driver" tab if you have an entry for "D: /media/cdrom0". If you don't have it or if the disk is listed with another letter, then try to add it by hitting the "ADD" button, then select it and hit the "Browse" button and select "/media/cdrom0".

---

### Post by Sheneron on 2009-05-10
The game is supported yes.  And all the drives are set up in wine config.  The mount drive and the cdrom drive are both listed.  It still won't work for me though.  Any other ideas?  Thanks for the input so far.

---

### Post by krzysz00 on 2009-05-10
nocd crack

---

### Post by Torgas Prim on 2009-05-10
It would really help if you told us the game you are having trouble with........

---

### Post by Sheneron on 2009-05-10
Sorry.  Neverwinter Nights 1 is the game.

---

### Post by Sheneron on 2009-05-10
But for the record, this happens with just about every game I try.

---

### Post by Bios Element on 2009-05-11
Neverwinter Nights has a native Linux client...Check the CD and it should have the installers on it if I recall correctly.

---

### Post by Sheneron on 2009-05-11
I only see the Setup.exe to install.  Also, I would like to figure out this problem for future games if possible. Thanks!

---

### Post by nhasian on 2009-05-11
you may also want to make sure you have the latest version of wine from the winhq repository:

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by ashmew2 on 2009-05-11
Dunno if this will help but I remember i had similar problems running a game with wine..All i did was merged both the CDs into a single ISO (it had two CDs) , and mounted it in Nautilus using gmount-iso.
I just CD'd to the Mounted directory and did wine setup.exe
After the game installed , i just used a NO CD crack and BAm it worked like a charm after that.

---

### Post by yaknowwat on 2009-05-11
[http://www.linuxquestions.org/questions/linux-games-33/starcraft-in-wine-disc-not-found-440490/](http://www.linuxquestions.org/questions/linux-games-33/starcraft-in-wine-disc-not-found-440490/)

Should be of help.  Sounds to be the same thing. Also leaves multiple solutions.

---

### Post by Bios Element on 2009-05-11
Erm, Like I said you don't need wine for this. [http://nwn.bioware.com/downloads/linuxclient.html](http://nwn.bioware.com/downloads/linuxclient.html)

---

### Post by Sheneron on 2009-05-11
Thanks Bios Element for the link.  I will try that later this evening and let you know how it goes.

---

### Post by Bios Element on 2009-05-11
> **Sheneron said:**
> Thanks Bios Element for the link.  I will try that later this evening and let you know how it goes.
Great. It'll take ages to install though so go get a pizza or something while you wait.

---

### Post by Torgas Prim on 2009-05-11
Go to the Bioware site and they have the linux install there for download after registering your cd key.

[http://nwn.bioware.com/downloads/linuxclient.html](http://nwn.bioware.com/downloads/linuxclient.html)

---

### Post by Sheneron on 2009-05-11
Eh, I have had a little trouble with the linux install.  I am going to try again tomorrow.  I will keep you posted.  Thanks again so far!

---

### Post by Sheneron on 2009-05-12
Yeah, I give up.  I can't get it to work following the instructions presented on the website.  Thanks for the help though.

---

### Post by Torgas Prim on 2009-05-14
Actually I just run NWN from my other drive I have it installed on. Works fine with full effects even on this ATI card I have

---

