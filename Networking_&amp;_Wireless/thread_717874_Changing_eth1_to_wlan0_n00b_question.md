---
title: "Changing eth1 to wlan0? n00b question"
date: 2008-03-07
forum: Networking &amp; Wireless
---

### Post by GeordieToddy on 2008-03-07
Hi, had a look thru other threads, but can't find an answer that works. Been using ubuntu for 2 days now - everything is fine apart from the wireless networking. Got a Broadcom 4311 card on an HP530 laptop, followed all of the guide here: 

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29#head-ea76065f30b99d3b8472289cd049e2b141856b55](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29#head-ea76065f30b99d3b8472289cd049e2b141856b55) 

and got quite far - installed the driver (i think) and the LED on the card is lit up now in its normal manner, so it seems to be working ok - but I can't get ubuntu to change my wireless card to wlan0 instead of eth1 - I've read in a few guides that you can change it by editing a file with the command:

user@ubuntu:~$ cat /etc/iftab

however, i just get an error message saying that iftab doesn't exist.

Any thoughts or ideas? I'm a total n00b btw, so please be gentle :)

thanks in advance,
Toddy.

---

### Post by edm1 on 2008-03-07
why is it you want to change the name of the card? i may be missing something but it shouldnt matter what the card is called.

---

### Post by GeordieToddy on 2008-03-07
because I am so n00b, that I will never get this card working the way I want it, without following guides word for word, and the guide I am using requires it:

"(If your wireless device initially shows up as eth1, go back to step 2 and comment out the eth1 line in /etc/iftab. Then resume the rest of the instructions. If you don't comment out the eth1 entry, ndiswrapper won't be able to alias the device as wlan0.)"

Thanks again.

---

### Post by ung/xunil on 2008-03-07
/etc/iftab doesnt exist in Ubuntu since Gutsy(?). Edit the file /etc/udev/rules.d/70-persistent-net.rules

---

### Post by Snakob808 on 2008-03-07
Did you modprobe ndiswrapper... i.e.

```
sudo modprobe ndiswrapper
```

Is your wireless working?

---

### Post by GeordieToddy on 2008-03-07
Thanks ung/xunil! Thats the answer I was looking for! 

Next question:

I don't have permission to edit the file..... how do I go about setting permissions??

P.S. yes Snakob808, I've done that. Thanks for your input.

---

### Post by ittiam on 2008-03-07
Precede the command with keyword sudo and it will ask you for the administrator password, provide it and you can edit the file.

For example,
```
sudo vi filename.c
```

---

### Post by GeordieToddy on 2008-03-07
Sweet. Thanks to all involved - gonna do a restart now an hopefully all is well. As soon as I figure out how to do it, I'll give you all thanks!

Thx from the n00b. :)

---

### Post by GeordieToddy on 2008-03-07
Yep, done a restart now, and that worked fantastically!
Thanks again to all who helped, and sorry for the double post :)

---

