---
title: "Can't find home Network"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by JST-375 on 2007-07-18
Ok,  Not sure if I'm posting in the correct thread for this so If I should be in the noobie thread, someone please let me know.

Ok first of all,  I am comptia a+ certified (2002) so noone will have to babystep me through the Windows part of my question. I am however relatively new to the Linux platform and may need a little handholding with that part. 

I have 3 computers on my home network. Two Xp pro machines (one of the xp boxes is a laptop with a 2wire pcmcia card) And the other is my beloved New venture, the Ubuntu Linux machine(used to be Xp, but i killed bill, Not a dual boot). The Linux box is running feisty fawn, has a 2.4ghz celeron, and 512mb ram. I switched from Xp on this machine about 3 months ago and everything had been working just fine, Ie; 3 printers attached to this machine using cups so that the windows machines could print here,  all the hardware worked right out of the box, and I was able to network with the windows machines using samba without a hitch. Untill recently, which leads me to my question.............

I'm not sure exactly when it happened(I think it was after an update) but all of a sudden the Ubuntu box disappeared from the home network. The two xp boxes can still see each other fine I Have scoured the forums and tried a few different things and even watched this video to make sure it was setup right(and it is) [http://youtube.com/watch?v=Ad17kma8rNM](http://youtube.com/watch?v=Ad17kma8rNM) (I got the link to this video from these forums) I had already done all that stuff when I first installed Ubuntu and it worked great. 

I'm at wits end. I've read and played with stuff for probably about 10 hours trying to get this back on the home network. 

Will someone please help me out? If you don't want to do it in the forums you can pm me on yahoo or msn or call me, or I can call you(I have free long distance) I need this box to function on the network and I really don't want to have to go back to windows on it.

---

### Post by dougfractal on 2007-07-18
I can't help on the samba part (window update or ubuntu?) 
 but in the mean time you could setup an ftp server till the windows network is sorted.
```

sudo apt-get install proftpd
```

see [http://ubuntuguide.org/wiki/Ubuntu:Feisty#FTP_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#FTP_Server)  more info

---

### Post by kevdog on 2007-07-18
Can you ping the two machines from the ubuntu box?  Just want to make sure we are dealing with a samba problem rather than a network problem.  I assume static IPs are being used.

---

### Post by JST-375 on 2007-07-20
I believe it happened after an ubuntu update. And thank you,  I will try the ftp thing today. at least that will allow me to share files. I already have access to a couple outside ftp servers,  but I just hate using the bandwidth to transfer files in house.

---

### Post by JST-375 on 2007-07-20
Yes I can ping the other machines.  and I can ping this machine from them.    

Edit: actually I'm using dhcp on all 3 but that has never been a problem with the internal network before.  I can certainly set them up static if need be.

Another Edit: ok  the windows machines are now able to see the ubuntu box but cannot access it (linuxbox is not accessible you may not have permission ect......) and I still cannot see the other windows machines from the linux box. I have set up usernames and passwords in samba successfully, still no luck.

---

