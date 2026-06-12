---
title: "[SOLVED] Basic Kubuntu to Kubuntu Home Network"
date: 2007-11-25
forum: Networking &amp; Wireless
---

### Post by sabbathpriest on 2007-11-25
First: Thank you for reading my post!

I have two Kubuntu 7.10 boxes (i386 and amd64 versions respectively) connected to the web through a router. All I want is to be able to share files and printers... I Googled quite a bit but all I could find is a lot of Samba how-to's (I don't need Samba as I have only a small Windoze partition that I seldom use), a lot of Step-by-Steps on complex networks with gateways and firewall servers and so on and so forth.... is there any guide out there on how to get these two Kubuntu 7.10 boxes to see each other?
 
This is what I tried so far: In both Kubuntu boxes I have gone to "System Settings - Network Settings - Zeroconf Service Discovery" and I enabled both checkmarks "Enable Zeroconf network browsing" and "Browse local network". When I then go to "System Menu - Remote Places" (It opens in Dolphin) and click on "Network services" I find nothing: "0 Items (0 Folders, 0 Files). And (I don't think this makes any difference anyway) if I click on "Network" instead of "System" and then click on "Network Services" I still find nothing. If I click on "Samba Shares" a message pops up that reads "Unable to find any workgroups in your local network . This may be caused by an enabled firewall". I also tried all of the above with the router firewall turned off, no luck either.

I have no idea of how to proceed, I don't mind reading whatever is necessary, but I haven't had any luck finding anything other than instructions to setup complex networks with servers and gateways and different Operating Systems on them. Should I setup Samba? Like I said, I have buried in my hard drive a small windoze partition that I use ONLY to play Civ IV once every blue moon.... Should I change my router? Or maybe use a crossover cable? I will keep on reading the how-to's I find even though so far none of them seem to apply to my barebone simple home network. But if anyone has a good pointers or has gone through a similar situation, I will very much appreciate any input.
Thank you!

PS: before you (**rightfully**) ask: Yes, I tried this same post on the Kubuntu forums but all I got is a suggestion to setup NFS on both boxes. I read up [this guide]("http://nfs.sourceforge.net/nfs-howto/") and I have now more questions than before, the setup for NFS is way over my head and I don't want to experiment with what I barely understand....

PS2: As a funny side note... this is very puzzling to me, Linux has been so far very forgiving to this IT illiterate ape, and I was not expecting any trouble having two boxes (That run virtually the same OS) "seeing" each other... I was expecting a "*Duh, click there and there*" sort of solution, and instead what I got was rather "Well, first you must get your LPI certification..."

---

### Post by dmizer on 2007-11-25
to share files between linux boxes, use nfs (howto is linked in my sig)

to share printers, use cups.  howto here: [https://help.ubuntu.com/community/PrintingCupsWebInterface?](https://help.ubuntu.com/community/PrintingCupsWebInterface?)

---

### Post by sabbathpriest on 2007-11-26
THANK YOU dmizer! I'll give it a try when I come back from work tonight and I will report back on the progress.

---

### Post by sabbathpriest on 2007-11-29
I finally got NFS to work, it took a while because I had to understand some concepts that were new to me.  The guide that I found most helpful in the end is [this one]("http://nfs.sourceforge.net/nfs-howto/") but it's not too friendly to complete knuckledraggers like me. It took me a couple of days of reading and re-reading. 
Dmizer: Thank you again for setting me on the right path!

---

### Post by MSchenker on 2007-12-12
Well, this has got to be the 100th discussion I've read regarding home networking on Linux.  I've devoted at least 20 hours of reading, effort, and system tweaking to setting up a wireless network on Kubuntu.  Nothing, and I mean absolutely nothing, works.
Sorry if I sound frustrated!  I'm hoping that in the next release of Ubuntu/Kubuntu, networking is improved.  I have faith in the great people who are working on this.
But for now it's easier for me to use a thumb drive for sharing files!
PS: Please people, stop using words like "simple" and "easy" to describe Linux wireless configuration!!

---

