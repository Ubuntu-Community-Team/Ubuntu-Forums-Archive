---
title: "i have no idea what im doing"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by skilgannon82 on 2011-05-15
i installed wubi last night and it wouldnt work so i followed the instructions to run ubuntu from usb and that works most of the time it goes through all this writing on screen then has menu and i choose to run it from usb and sometimes it will go through more writing on screen that goes way over my head and it will freeze but if i hard reset and try again it does all the same thing but it will work so i decided it might run better if i actually install it properly but i want to keep windows 7 aswell and when i chose to install it from usb it says all 4 of my partitions are being used and i dont want to mess with them because i have no idea what im doing 

i have an i5 hp pavillion g6 laptop with 64 bit windows 7 and a 1gb radeon graphics card i hope someone can help me please ubuntu looks pretty cool

---

### Post by williejones on 2011-05-15
First you need to shrink windows 7 from within windows:
[http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html](http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html)

Then you need to boot from Ubuntu, start the install, select advanced, and pick the free space you selected above to install.

Make sure Grub (the boot loader) is installed to sda so you can boot either system.

---

### Post by ndex477 on 2011-05-15
Join the club. don't feel bad I'm a newbie also but i do remember that when I installed 11.04 I installed it using the wubi installer. I opened the wubi installer and chose the option to run Ubuntu inside Windows, then the download began. It took about an hour and a half.
 
Eventhough I partitioned my HD i still haven't used the partition. Running Ubuntu inside Windows seems to work fine for now.
 
Hope this helps and that some more experienced gurus come to your rescue by the time I post this
 
Good Luck :)

---

### Post by snowpine on 2011-05-15
Here is a totally safe and risk-free way to run Ubuntu inside of Windows: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by skilgannon82 on 2011-05-15
thank you for your help but when i create a new volume just as im about to finish it says it will be a dynamic drive and from everything ive read ive heard this is bad or i will not be able to run ubuntu from it is this true?

---

### Post by ndex477 on 2011-05-15
I designated my partition as dynamic because I couldn't proceed otherwise. Don't know how it will affect my partition but I'm now running Ubuntu and I have a designated 50GB to work with when I need it.

---

### Post by skilgannon82 on 2011-05-15
thats exactly what i did designated 50 gb to it 
does yours runs fine?

---

### Post by ndex477 on 2011-05-15
Runs o.k. Linux is a very good OS. It's taking some getting used to from using Windows. Works fine though. BTW I dual boot w/ Windows 7

---

### Post by skilgannon82 on 2011-05-15
cool thanks so much for your help everything you are describing you do is exactly what i want to do going to try it now hopefully i wont have to be back here with similar questions again 

cheers again

---

### Post by skilgannon82 on 2011-05-15
im in ubuntu now from the usb but when i went to install it the 50 gb partition i created is not showing up

---

