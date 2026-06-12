---
title: "Mediatek MT7630e Wifi chipset driver for ubuntu 14.10"
date: 2014-10-29
forum: Networking &amp; Wireless
---

### Post by Lomas_Joshi on 2014-10-29
[COLOR=#3E454C][FONT=Helvetica]Hello All,[/FONT][/COLOR]
[COLOR=#3E454C][FONT=Helvetica]I got wifi problem with my ubuntu.[/FONT][/COLOR]
[COLOR=#3E454C][FONT=Helvetica]I have "ASUS vivo book K551LN" with "ubuntu 14.10". Wifi is not working and i can't get any solutions to it. [/FONT][/COLOR]
[COLOR=#3E454C][FONT=Helvetica]Wifi Chipset is Mediatek MT7630e.[/FONT][/COLOR]
[COLOR=#3E454C][FONT=Helvetica]May i expect any help on this?

Regards,
Lomas Joshi[/FONT][/COLOR]

---

### Post by jamur on 2015-03-04
Hi. I had the same problem with my new Asus N750JV. I made it working like this:
Download the file prepared by Tobias Bora you can find here [https://github.com/tobiasBora/MT7630E_3.16](https://github.com/tobiasBora/MT7630E_3.16)
This is for the kernel 3.16, the one I have in the moment I write this. To find out your kernel, open a terminal and write uname -r
If your kernel is not this one, you can update your system to that kernel.
Uncompress the file downloaded from Tobias Bora github and in a terminal, go to the uncompressed folder (i.e. cd /home/myuser/Downloads/MT7630E_3.16-master)
Then write in the terminal "make install"
You will be asked for your password. Enter it and tha's all.
It worked for me and I thank so much Tobias Bora for such a great work.
I hope this will help you

---

### Post by gmoutso on 2015-04-01
[https://github.com/kuba-moo/mt7630e](https://github.com/kuba-moo/mt7630e) solves a 100% CPU problem of Tobias' solution on my asus tp500ln

---

### Post by ehood2 on 2015-04-02
> **gmoutso said:**
> [https://github.com/kuba-moo/mt7630e](https://github.com/kuba-moo/mt7630e) solves a 100% CPU problem of Tobias' solution on my asus tp500ln

do you have 3.16 kernel?

---

### Post by gmoutso on 2015-04-03
yes 3.16-0.33. 
You may be interested in the discussion at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1220146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1220146) or raise an issue at [https://github.com/kuba-moo/mt7630e](https://github.com/kuba-moo/mt7630e) directly

---

### Post by aljaz3 on 2015-10-11
> **jamur said:**
> Hi. I had the same problem with my new Asus N750JV. I made it working like this:
Download the file prepared by Tobias Bora you can find here [https://github.com/tobiasBora/MT7630E_3.16](https://github.com/tobiasBora/MT7630E_3.16)
This is for the kernel 3.16, the one I have in the moment I write this. To find out your kernel, open a terminal and write uname -r
If your kernel is not this one, you can update your system to that kernel.
Uncompress the file downloaded from Tobias Bora github and in a terminal, go to the uncompressed folder (i.e. cd /home/myuser/Downloads/MT7630E_3.16-master)
Then write in the terminal "make install"
You will be asked for your password. Enter it and tha's all.
It worked for me and I thank so much Tobias Bora for such a great work.
I hope this will help you

Mate, i've been trying to fix my wifi for like whole 2 days, with shitload of googling, and i want to thank you for posting the solution. THANK YOU!
btw, thank you :D

---

