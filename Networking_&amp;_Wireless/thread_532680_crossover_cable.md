---
title: "crossover cable"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by NULL712 on 2007-08-23
OK your thinking wow another guy trying to share files with a crossover cable. woohoo what a dumb a** he should look at all the other threads on this subject. Well I have and I still can't share file between my desktop and my laptop. I have installed NFS on both computers and like the noob that I am to networking I expected every thing to work the way I wanted it to. Boy was I wrong!!

What I am working with:

emachine desktop all intel with a celeron d CPU and 512MB of RAM

dell inspiron 6000 centrino and 1 GB of RAM

a crossover cable

and no internet connection, i literally have to walk down my street to leach of a wireless signal.

simply put I want to connect my computers with a crossover cable using NFS or SMB so i can back up data from my laptop to my desktop. and eventually want to do this wirelessly.

keep in mind i can't install programs on my desktop because i don't currently have an internet connection.

any help/ideas are greatly appreciated

Thanx

---

### Post by will71110 on 2007-08-23
What OS are each using?

---

### Post by HermanAB on 2007-08-23
Whatever system you have running on the desktop, it should have a ftp client, so you should install a ftp server on the laptop - proftpd or vsftpd are both good and the default install should work without modification.

Then, all you need to do is set the two machines to the same net:
desktop: 192.168.1.1
laptop: 192.168.1.2
255.255.255.0

You don't need to set anything else, start proftpd on the laptop, go to the desktop and type:
ftp 192.168.1.2

Cheers,

Herman

---

### Post by NULL712 on 2007-08-23
WOW thanx for the quick reply....both computers are running ubuntu 7.04

ok so this is a question only a noob would ask....how do i get both computers on the same net?

Thanx for all your help!:)

---

