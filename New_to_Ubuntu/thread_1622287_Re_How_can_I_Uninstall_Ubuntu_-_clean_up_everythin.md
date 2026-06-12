---
title: "Re: How can I Uninstall Ubuntu - clean up everything-"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by Syd Martin on 2010-11-15
**Re:  How can I Un-install Ubuntu - clean up everything-** 			
 			 			 		   		 		 		I am in a pickle!:(

I believe to add to my problems I have been attacked by some virus or other. 
Clam is so dreadfully slow and does not appear to be able to cope.
I have installed and uninstalled Wine but I cannot install anything I try to download from a DVD or the net.
Ubuntu is my only OS
I think my solution is to remove Ubuntu from my hard drive altogether and start afresh.
[U]
[SIZE=3]How![/SIZE][/U][SIZE=3] [SIZE=3]c[/SIZE][/SIZE]an I remove -uninstall - Ubuntu, clean my hard-drive and reinstall Ubuntu 10.04.
I don't really want to go back to Windows, but first and foremost I must remove Ubuntu and reinstall it.

I have had so much trouble with this so call OS for everyone I am beginning to think that M S Windows is not so bad. 

I am between a rock and a Very very hard place. I really want to use and understand Ubuntu / Linux and leave MS to the non thinkers ( the unethical ones).

Can someone please help me I need an OS I can use for my studies with the OU. (I am a mature student not some young quick learning geek, not that I wouldn't like too be)

Pincher,  in anticipation, Thank you:P



 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=10118338") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=10118338")

---

### Post by Rex Bouwense on 2010-11-15
If you have already downloaded 10.04 and checked the md5sum, burn the ISO to a CD.  Boot from the CD and install on your computer.  The installation process will ask you how you want to install and you can choose the option of using the whole hard drive.  That will effectively overwrite EVERYTHING on your hard drive, so make sure that you back up anything that you want to keep to some external device before you do that.  Enjoy.

---

### Post by mosaic2s on 2010-11-15
why do you need clam and wine in ubuntu?
10.04 is good. try it again.
for ms windows - install it in virtualbox.

---

### Post by toolmania1 on 2010-11-15
You can also run DBAN from the ultimate boot cd.  You would have to download the ultimate boot cd from the internet first of course, which may not help you out here.  But, DBAN ( Derik's boot and Nuke ) will wipe the hard drive at the bit level putting 0's down.  It takes a very long time ( it took my wipe 3 days last time ).  But, if you are concerned about a virus, nothing is surviving that or you have the mother of all viruses ( which is very very very unlikely ).  Then, you could install ubuntu from scratch.Are you using Wine?  Have you looked for alternative software in Linux for the programs you use?  I have found something for everything I used except FL Studio and Adobe Flash.Dreamweaver = Bluefish in Ubuntu ( there are other also )MS Word = Open Office in UbuntuCheck [http://www.osalt.com/](http://www.osalt.com/)

---

### Post by amjjawad on 2010-11-15
1) You need Ubuntu's LiveCD or LiveUSB (check [www.ubuntu.com](www.ubuntu.com) for howto). Don't forget to check MD5SUM [[https://help.ubuntu.com/community/HowToMD5SUM]](https://help.ubuntu.com/community/HowToMD5SUM])

2) Make sure your BIOS settings are set to boot from CD/USB.

3) Run the LiveCD/USB and do not install anything, just choose "try".

4) System > Administration > GParted and (if you want that) delete/remove all partitions and start from scratch

5) Either you create partition using GParted or while Installation, it's your call.


If you really want to restart your machine every now and then, handle the slowness, lags, etc ... then go for Windows
If you want something stable, fast, etc etc ... go for Linux.

[http://distrowatch.com/](http://distrowatch.com/)
Here, you could find what are you looking for!

Good luck!

---

### Post by Syd Martin on 2010-11-15
Hi there one and all,

Thanks boys I have copied and printed your suggestions and am about to check out the Internet where suggested, check my back ups are OK and dive in. It may take some time but the only person to mind will only be Billy Boy, I only hope this time the horse has bolted before the Gates are closed.
:P:P:P
Cheers, thanks a lot,

Pincher

---

### Post by ajgreeny on 2010-11-15
> I believe to add to my problems I have been attacked by some virus or other. 
Clam is so dreadfully slow and does not appear to be able to cope.
I have installed and uninstalled Wine but I cannot install anything I try to download from a DVD or the net.
Ubuntu is my only OS
I think my solution is to remove Ubuntu from my hard drive altogether and start afresh.
Actually I think you need to forget your Windows ways, and stop downloading and trying to install programs from the net or from DVDs, and just use synaptic or the software centre.

Ubuntu is not like Windows and generally we don't install anything in the way you have been used to;  we use repositories of packages from ubuntu itself.

Certainly as a new user(?) you will not find it easy to deal with anything other than those packages that are included in repositories.

---

