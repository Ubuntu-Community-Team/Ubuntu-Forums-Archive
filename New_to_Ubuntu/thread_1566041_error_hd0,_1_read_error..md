---
title: "error: hd0, 1 read error."
date: 2010-09-01
forum: New to Ubuntu
---

### Post by Jodiju on 2010-09-01
I'll preface this message by saying that I am a complete and utter noob with Ubuntu. I've been using it for less than two months. Anyway, here goes;

Two months ago the HDD that came with my laptop died on me so I went out and bought a brand new WD HDD. I had problems re-installing Windows as the licence key (handily printed on the bootom of my laptop) had worn almost completely away. Because I'd heard people saying how good it was (and because it was free if I'm honest) I downloaded and installed Ubuntu. Loved it from the get-go. 

Fast forward to the present and I've been trying to boot up my laptop for the last two hours but keep getting the message;

error: hd0, 1 read error
grub rescue>

I've looked around a few places and the only thread I could find with this error message wasn't applicable (it was a dodgy connection to the HDD). I've also looked at the manual on GRUB Wiki but, frankly, I couldn't make much sense of it. I did try entering 'help' as the Wiki suggests but I got back 

Unknown command 'help'

So my questions;

Does this mean that my  two-month-old HDD has gone to silicon heaven?

If not, how do I fix this?

As I said above, I'm a total noob at Ubuntu so if you can help, explain it to me like I'm a six year old. 

Thanking you in advance for any and all help offered.

PS. I think I read that GRUB has something to do with dual-boot systems, which confused me even more as I'm not running another OS alongside Ubuntu.

---

### Post by Jodiju on 2010-09-01
After reading undecim's very helpful post about asking support questions I should mention that I am unsure which version of Ubuntu I have installed. I just downloaded it straight from the website.

---

### Post by Cypress421 on 2010-09-01
That could mean your HDD is on its last legs. Can you try and download an HDD checker to see:

[http://www.hitachigst.com/support/downloads/#DFT](http://www.hitachigst.com/support/downloads/#DFT)

You'll need another PC to create the bootable disc.

---

### Post by Jodiju on 2010-09-01
Ok, I downloaded DFT, does the boot disk have to be created in Ubuntu? Because all the other PC's in the house run Windows.

---

### Post by Cypress421 on 2010-09-01
No, use ImgBurn in WIndows, burning as .ISO, verifying, then reboot with the disc to check if the HDD is dying. You might need to set your BIOS to boot from CD. I would also read the info about the application on HItachi's website so you know what you are looking for.

---

### Post by Jodiju on 2010-09-01
Ok thanks. I'll report back.

---

### Post by Jodiju on 2010-09-01
I got 

Problem with non Hitachi drive 
Disposition Code 0x70.

I googled that error message and found a forum that says most times it can be fixed by using Sector Repair or Erase Disk. Would you recommend doing that?

Is there any way I can get files currently on the HDD onto a USB external drive before wiping them?

---

### Post by Cypress421 on 2010-09-01
Before you try that, reboot into an Ubuntu live cd, and see if you files can be copied across onto an external hard drive. Then try to reformat as suggested.

---

### Post by Jodiju on 2010-09-01
Well thanks for your help Cypress421 but it seems that it is indeed my HDD that has bought it. 

I couldn't use DFT to repair the sector so I downloaded and ran the Western Digital diagnostic tool. Less than twenty minutes into a test it said would take over two hours I got

Error Code 0025 - Error count reached a threshold value. There are too many errors detected on this drive to be repaired. Replace the drive.

Do I change this to [solved] now then?

---

### Post by Cypress421 on 2010-09-02
Looks like it should be "solved". I would choose Seagate for another HDD, I've always built with them, never had issues.

---

