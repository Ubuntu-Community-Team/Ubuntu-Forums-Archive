---
title: "Hanging at Bootup"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by JohnGalt on 2009-08-31
I installed Ubuntu 9.04 onto my HP dv6636nr laptop twice now. The first time boot up would hang first boot up. I would have to sit repeatedly pressing buttons to keep it going and boot up. I downloaded the ubuntu iso all over again and recopied it and reinstalled it. Seemed to be working fine. I had to extend the partition then run the updates. I told it to suspend and later it wouldn't come back up. Forced it to shut off holding down power button. Ever since it's been freezing up on boot up and I'll have to press a button to get it going again, several times in one boot up. What did I screw up, how do I fix it? 
Thanks

---

### Post by LowSky on 2009-09-01
resizing partitions can ultimately mess things up. don't resize a partition unless you have backed it up entirely

---

### Post by isparkes on 2009-09-01
I'm on an HP dv3000, and have experienced similar things. It still doesn't always shut down reliably (sometimes goes back into text mode and prints 6 miniature versions of the text screen).

I found that popping out the DVD drive before booting appeared to help.

I've got a feeling that there's something going on with HP kit.

---

### Post by JohnGalt on 2009-09-01
Thanks. Mine also hangs at shutdown but not like that. Goes to a blank black screen. Can press keys and weird text will pop up, but it finally shuts down.

Interesting, I haven't tried it with the dvd tray ejected. I plan to format the whole pc and start over. I had tried giving it 10 gigs for root when I installed it the first time, ended up with 2gigs for root somehow. 

I didn't back anything up because I had no personal files to back up.

Going to wipe it all with 20 gigs to vista, 20 to ubuntu and the rest to storage. Not sure how much space to put as swap.

---

### Post by LewRockwell on 2009-09-01
> **JohnGalt said:**
> Thanks. Mine also hangs at shutdown but not like that. Goes to a blank black screen. Can press keys and weird text will pop up, but it finally shuts down.

Interesting, I haven't tried it with the dvd tray ejected. I plan to format the whole pc and start over. I had tried giving it 10 gigs for root when I installed it the first time, ended up with 2gigs for root somehow. 

I didn't back anything up because I had no personal files to back up.

Going to wipe it all with 20 gigs to vista, 20 to ubuntu and the rest to storage. Not sure how much space to put as swap.

swap=1xMAXRAM

so if your unit can handle 2GB of ram max...then 2GB of swap will work fine

(as always, swap on legacy devices with limited total ram, say under 1GB, should still go with installed ram times 1.5 to 2.0)

.

---

### Post by JohnGalt on 2009-09-03
Thanks. I used gparted and wiped my drive clean. I created a 20 gig root partition, 2 gig swap, 20 gig vista, and then the rest was formatted to ntfs for storage.

I installed vista then Ubuntu. I let ubuntu update everything. Installed VLC player. I'm still having the same problem of it hanging up.

I'm wondering if it going to suspend mode could be the culprit, that or interupting the startup by rebooting during startup.

---

### Post by Dlobster on 2009-09-03
I just installed ubunto on my dell inspiron 1100 and am having similar issues.  It hangs on the boot up.  I thought it was just from the original install, but it happened again tonight.
No other OS, just ubunto 9.04 on a fresh wiped 10  gig drive.
Installing updates at the moment.
First attempt at boot I get the text and then  nothing but backlight
Hard powered down and restarted and got the password dialog.
Dan

---

### Post by Dlobster on 2009-09-04
Couldn't get anywhere after the updates until I started in safe mode and choose an option to fix graphic problem.  I was then able to resume normal boot and was able to start ok.  Any ideas for a more permanant fix?  Is there a different version which mught be better for the machine?  or am I just going to need to do a safe start every time I boot?
Dan

---

