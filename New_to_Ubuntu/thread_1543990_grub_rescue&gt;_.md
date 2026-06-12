---
title: "grub rescue&gt;_"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by montalier on 2010-08-01
HELP!  My computer reads:
 
GRUB loading.
error: no such partition
grub rescue>_ 
 
I have tried all the commands I have have found in this forum, including 'boot', but the only response I get is:
 
Unknown command 'boot'   (or whatever other commands I try).
 
I also tried to boot from my Windows XP CD but I end up with the same 'grub error'. I am not able to enter set up (F12) during boot.
 
This is the background:  
 
I started up Ubuntu 9.10 from CD and chose 'Install Ubuntu' after it had fully loaded.  The insallation ran well until Partition.  I chose a clean intallation, ie. to replace everything on the drive.  During the insallation, I got an error message stating that some file being used and I had to abort the installation.  When rebooting, I got stuck at the above grub message. 
 
In other words, my computer has become uselss and I desperately need help.
 
Thank you in advance!

---

### Post by oldfred on 2010-08-01
This will tell us about your system configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by tiansenrui on 2010-08-02
i met this problem this week and finally i fixed it.

insert a winxp or vista cd and follow the installation steps, delete the ubuntu partition, then recreate the partition, then you can install the ubuntu again from cd.

---

### Post by montalier on 2010-08-02
Thank you for help.  What I don't understand is how that will work when my computer no longer can access the internet and seeems unable to read CD's. At least it seem unable to read the Ubuntu CD as well as the Windows XP CD.  
 
Please excuse my ignorance.  I am new at this.

---

### Post by montalier on 2010-08-02
tianseruni, 
 
I appreciate your help, but have already tried that.  The computer is unable to read th Windows XP CD.

---

### Post by oldfred on 2010-08-02
Even if the hard drive is totally not working you should be able to directly boot a CD from the BIOS. Nothing you install from Windows nor Ubuntu will modify BIOS. 

Have you reset BIOS to boot CD first. Or do you have a f key that lets you choose boot device (mine is f12  but if varies). Usually the BIOS has brief instructions at the bottom that say choose boot with f12 or whatever.

---

### Post by warfacegod on 2010-08-03
> **oldfred said:**
> Nothing you install from Windows nor Ubuntu will modify BIOS.

Not entirely accurate anymore but certainly close enough for the situation here.

Windows 7 will now make some changes to a BIOS when Bluetooth is disabled from within the OS. Apparently this cannot be undone from within the actual BIOS. Folks that have done this and then wiped 7 in favor of another OS have had serious problems getting their Bluetooth working again. I've only seen this reported with a few Acer Netbook models so far.

---

### Post by montalier on 2010-08-04
Hi oldfriend,
 
Thank you for insisting that I should be able to directly boot a CD from the BIOS. Since F12 no longer worked, I googled and found a list of BIOS manufacturers and the keys they were using. I tried probably 2/3 of them before it finally did the trick. 

Issue resolved!

---

