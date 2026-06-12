---
title: "Problem Installing software"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by mosaabJ on 2009-12-10
I just installed Ubuntu on my laptop and I have this problem that I cannot install software from the Ubuntu Software Centre.There is no install button. This is a screen shot from my Computer of the problem.
[[IMG]http://img22.imageshack.us/img22/6835/screenshotin.th.png[/IMG]](http://img22.imageshack.us/i/screenshotin.png/)

---

### Post by mikewhatever on 2009-12-10
That's an odd glitch. You can still install aMSN from Synaptic package manager or command line though.

---

### Post by corncob on 2009-12-10
There should be an install as well as a website button under that.  Are all your applications the same way?

---

### Post by mosaabJ on 2009-12-10
Yeah it it the same for all the applications

---

### Post by mosaabJ on 2009-12-11
Is there a solution to this problem!

---

### Post by MelDJ on 2009-12-11
did you follow the way mikewhatever told?

---

### Post by Rodemire on 2009-12-11
> **mosaabJ said:**
> I just installed Ubuntu on my laptop and I have this problem that I cannot install software from the Ubuntu Software Centre.There is no install button. This is a screen shot from my Computer of the problem. 


My software centre also does the same thing. What i do is i just get the name of the app and then search and install using Synaptic.

---

### Post by lotharmat on 2009-12-11
> **Rodemire said:**
> My software centre also does the same thing. What i do is i just get the name of the app and then search and install using Synaptic.

I installed the 'Old Style' Add/remove programs

I found it to be better than the 'new' get software

---

### Post by mikewhatever on 2009-12-11
> **lotharmat said:**
> I installed the 'Old Style' Add/remove programs

I found it to be better than the 'new' get software

Indeed, that is a good work around. The package name to install is gnome-app-install, for those interested.

---

### Post by dnairb on 2009-12-11
This may seem a silly question, but have you tried maximising the Ubuntu Software Centre window?

---

### Post by lotharmat on 2009-12-11
> **mikewhatever said:**
> Indeed, that is a good work around. The package name to install is gnome-app-install, for those interested.

I was hoping someone would post the name of that!:D

---

### Post by RosscoRossco on 2009-12-11
I have the same using ubuntu 9.10 on my desktop, not abe to download anything.  This is what I end up with when I use synaptic package manager:

  	 	 	 	 	 	  W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]  
 

 W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]  
 

 W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]  
 

 W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]  
 

 W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]  
 

 W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]  
 

 W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]  
 

 W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]  
 

 W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]  
 

 W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]  
 

 W: Some index files failed to download, they have been ignored, or old ones used instead.


Do you have the same thing?

---

### Post by 3rdalbum on 2009-12-11
> **RosscoRossco said:**
> I have the same using ubuntu 9.10 on my desktop, not abe to download anything.  This is what I end up with when I use synaptic package manager:

  	 	 	 	 	 	  W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]  
 W: Some index files failed to download, they have been ignored, or old ones used instead.


Do you have the same thing?

Try changing your mirror setting in Software Sources, or make sure that you don't have a proxy set up in Synaptic.

---

### Post by mosaabJ on 2009-12-11
Thank you every one for your help.
I tried maximizing the window but still had the problem but I played around with the system, and then updated the system and everything seems to be working fine now.

---

### Post by corncob on 2009-12-11
> **dnairb said:**
> This may seem a silly question, but have you tried maximising the Ubuntu Software Centre window?

Another silly question - did you do a hard reboot (turn the computer off for at least several minutes since you installed Karmic)?

---

### Post by Muskegman on 2009-12-11
Open a terminal and type    sudo apt-get update

this solved the problem for me now i can install from software centre

;)

---

