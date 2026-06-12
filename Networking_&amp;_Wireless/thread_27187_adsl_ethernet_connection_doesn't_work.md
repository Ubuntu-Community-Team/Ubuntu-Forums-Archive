---
title: "adsl ethernet connection doesn't work"
date: 2005-04-15
forum: Networking &amp; Wireless
---

### Post by mila80 on 2005-04-15
Hi,
   I have an ethernet Adsl modem, but since I had upgrade from wortly to horay my connection doesn't work well.
It sometimes work for some seconds then it stops.
I thought that was a modem problem, but with windows it works well.
I see that there are some thread of person who had the same problem, but I'm not able to solve mine.
Someone can help me step by step???
Marco

---

### Post by vtrac on 2005-04-15
[QUOTE=mila80]Hi,
   I have an ethernet Adsl modem, but since I had upgrade from wortly to horay my connection doesn't work well.
It sometimes work for some seconds then it stops.
I thought that was a modem problem, but with windows it works well.
I see that there are some thread of person who had the same problem, but I'm not able to solve mine.
Someone can help me step by step???
Marco[/QUOTE]
 [http://www.ubuntuguide.org/#rp-pppoe](http://www.ubuntuguide.org/#rp-pppoe)

Have you tried that?

---

### Post by mila80 on 2005-04-15
I tryed with pppoeconf and pon dsl-provider.
All seams work but I can't surf.

---

### Post by mila80 on 2005-04-15
Now I tried with rp-pppoe, but I don't fint editor menu in my System tools.

Way can I surf for 10 seconds and then it stops by itself?

Someone can help me???
 Sorry if I'm boring, but a pc without an internet connection is an notthing.

Marco

---

### Post by oracledarren on 2005-04-15
[QUOTE=mila80]Hi,
   I have an ethernet Adsl modem, but since I had upgrade from wortly to horay my connection doesn't work well.
It sometimes work for some seconds then it stops.
I thought that was a modem problem, but with windows it works well.
I see that there are some thread of person who had the same problem, but I'm not able to solve mine.
Someone can help me step by step???
Marco[/QUOTE]

You might want to try the eciadsl drivers from [http://www.flashtux.org](http://www.flashtux.org)

I originally was using a BT voyager 105 modem which didnt have any drivers compatible within the open source world at the time.  These people support alot of the odd modems out there so yours maybe one of them.

Certainly worth a try anyway.

---

### Post by mila80 on 2005-04-15
I'm sorry, but i don't think it is a driver problem... 
My ethenet card is ok. 
My modem is connected by ethetrnet card.

Marco

---

### Post by mila80 on 2005-04-15
Hi,
  I post what happened when I'm trying to connect to internet.


marco@ubuntu:~$ sudo pon dsl-provider
Password:
Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.3 compiled against pppd 2.4.2
marco@ubuntu:~$ plog
Apr 16 01:25:40 localhost pppd[7628]: RP-PPPoE plugin version 3.3 compiled against pppd 2.4.2
Apr 16 01:25:40 localhost pppd[7681]: pppd 2.4.2 started by root, uid 0
Apr 16 01:25:40 localhost pppd[7681]: PPP session is 33322
Apr 16 01:25:40 localhost pppd[7681]: Using interface ppp0
Apr 16 01:25:40 localhost pppd[7681]: Connect: ppp0 <--> eth0
Apr 16 01:25:40 localhost pppd[7681]: Couldn't increase MTU to 1500
Apr 16 01:25:40 localhost pppd[7681]: Couldn't increase MRU to 1500
marco@ubuntu:~$ plog
Apr 16 01:26:00 localhost pppd[7681]: Cannot determine ethernet address for proxy ARP
Apr 16 01:26:00 localhost pppd[7681]: local  IP address 82.51.25.17
Apr 16 01:26:00 localhost pppd[7681]: remote IP address 192.168.100.1
Apr 16 01:26:00 localhost pppd[7681]: primary   DNS address 85.37.17.15
Apr 16 01:26:00 localhost pppd[7681]: secondary DNS address 151.99.125.1
marco@ubuntu:~$ plog
Apr 16 01:26:00 localhost pppd[7681]: primary   DNS address 85.37.17.15
Apr 16 01:26:00 localhost pppd[7681]: secondary DNS address 151.99.125.1

marco@ubuntu:~$ sudo pon dsl-provider
Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.3 compiled against pppd 2.4.2
marco@ubuntu:~$ plog
Apr 16 01:28:53 localhost pppd[8020]: Using interface ppp1
Apr 16 01:28:53 localhost pppd[8020]: Connect: ppp1 <--> eth0
Apr 16 01:28:53 localhost pppd[8020]: Couldn't increase MTU to 1500
Apr 16 01:28:53 localhost pppd[8020]: Couldn't increase MRU to 1500
Apr 16 01:28:53 localhost pppd[8020]: Couldn't increase MRU to 1500
Apr 16 01:28:53 localhost pppd[8020]: Remote message: Request Denied
Apr 16 01:28:53 localhost pppd[8020]: PAP authentication failed
Apr 16 01:28:53 localhost pppd[8020]: Couldn't increase MTU to 1500
Apr 16 01:28:53 localhost pppd[8020]: Couldn't increase MRU to 1500
Apr 16 01:28:53 localhost pppd[8020]: Connection terminated.
marco@ubuntu:~$


I'm crazying....

Someone help me, please... 


MArco 

](*,)  ](*,)  ](*,)  ](*,)  :confused:  :confused:

---

### Post by alastair on 2005-04-16
You get these :

Couldn't increase MRU to 1500

Which might be the problem. You can set the MTU (max. transmission unit) using PPP - the "mtu" option. Some people /do/ have trouble with ISP's and MTU and this might cause a problem like yours. See if you can find any help on your ISP's web site about MTU - else, try setting it to something like 1480, or 1460 etc.

---

### Post by mila80 on 2005-04-16
[QUOTE=alastair]You get these :

Couldn't increase MRU to 1500

Which might be the problem. You can set the MTU (max. transmission unit) using PPP - the "mtu" option. Some people /do/ have trouble with ISP's and MTU and this might cause a problem like yours. See if you can find any help on your ISP's web site about MTU - else, try setting it to something like 1480, or 1460 etc.[/QUOTE]

How can I do it?

And more, what means 

Apr 16 01:26:00 localhost pppd[7681]: Cannot determine ethernet address for proxy ARP????

I don't understand why It works well with Worty and now It make all this problem.

MArco

---

### Post by alastair on 2005-04-16
If this is /just/ a PPP issue, then the pppd daemon has an options file - see :

man pppd

The options file is :

/etc/ppp/options

If you change this file - make a BACKUP.

Try uncommenting the line :

#mtu <n>

and change to e.g.

mtu 1460

There is also a "proxyarp" config option - but I would leave this for the moment, until you see if the MTU change helps at all. You might need to experiment with a few values, or see if your ISP has any FAQ's or docs about this.

---

### Post by alastair on 2005-04-16
Perhaps :

mtu 1492

Also, this might not be something for the /etc/ppp/options file anyway.

If that does not work, try adding "mtu 1492" in your ethernet device section in /etc/network/interfaces (see : man interfaces) - then ifdown eth0 && ifup eth0. Check using : ifconfig eth0.

---

### Post by mila80 on 2005-04-17
Hi alastair,
   I made all change You sugested me, but nothing canghe for me connection.
Here are the log...


marco@ubuntu:~$ sudo pon dsl-provider
Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.3 compiled against pppd 2.4.2
marco@ubuntu:~$ plog
Apr 17 12:08:14 localhost pppd[9473]: Using interface ppp1
Apr 17 12:08:14 localhost pppd[9473]: Connect: ppp1 <--> eth0
Apr 17 12:08:14 localhost pppd[9473]: Couldn't increase MTU to 1500
Apr 17 12:08:14 localhost pppd[9473]: Couldn't increase MRU to 1500
Apr 17 12:08:14 localhost pppd[9473]: Couldn't increase MRU to 1500
Apr 17 12:08:14 localhost pppd[9473]: Remote message: Request Denied
Apr 17 12:08:14 localhost pppd[9473]: PAP authentication failed
Apr 17 12:08:14 localhost pppd[9473]: Couldn't increase MTU to 1500
Apr 17 12:08:14 localhost pppd[9473]: Couldn't increase MRU 

Marco

---

### Post by xbaez on 2005-05-27
I had the excact same problems, run pppconfig, edited some files at /etc/ppp
and the only solution was to run kppp as a non-privileged user (root), that is in the 'dialout' group

So now I use root, and I am able to connect to the internet

Hopefully that will be your case too

---

### Post by mila80 on 2005-05-27
Hi all,
   i find it with a my friends. It solves our problem... 
Try with it... ok???


[http://ubuntuforums.org/showpost.php?p=181316&postcount=2](http://ubuntuforums.org/showpost.php?p=181316&postcount=2)

bye, Marco

---

