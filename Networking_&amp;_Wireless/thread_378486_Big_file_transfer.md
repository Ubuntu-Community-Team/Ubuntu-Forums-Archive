---
title: "Big file transfer"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by fjr0122 on 2007-03-07
Me and my friend went on a road trip, and generated 6gigs of data (between our 2 cameras).
So we had to unload files to his laptop to keep some free space on the sd cardss. He has the files and I need them (at least the ones I took).

For reasons I dont wanna explain we want to transfer them over the internet. 

I run ubuntu 6.10 and he runs windows XP. 

We need a solution thats easy for him, but I dont mind getting my hands a little dirty. 

We have been trying to use Hamachi to transfer the files (i've been running XP) but its giving us weird errors. (i dont have the details on hand).  

And yes we know its going to take a longish (8+hrs) time but its ok. 

So what would a linux guru guy do in this situation, and would it be something feasible for me to do. 

Any links to HowTo's or Guides or Tutorials would be really great. Thanks for any help and reading my thread.

Edit: We also tried gTalk it didnt like the idea of sending 3gb files.

---

### Post by christhemonkey on 2007-03-07
Personally, i would zip up all the pictures into one big .zip file (or .tar.gz or something) and then send them in an email to the other guy.

(I admit that there is a probably a better way than this. Maybe using something like flickr? Or by putting them in a torrent file for him to download?)

---

### Post by mips on 2007-03-07
Ssl Ftp

---

### Post by fjr0122 on 2007-03-07
The files are all on his side (windows) not mine. 
Our emails (gmail) wont except more than 10mb per email.....
(Putfile could work (but it would take forever) if I could get him to use it).

---

### Post by mips on 2007-03-07
> **fjr0122 said:**
> The files are all on his side (windows) not mine. 
Our emails (gmail) wont except more than 10mb per email.....
(Putfile could work (but it would take forever) if I could get him to use it).

Uhm, SSL FTP server on your pc and he uses a windows ssl ftp client with a simple drag & drop gui ? I can't really think of anything easier.

---

### Post by fjr0122 on 2007-03-07
How would I set that up?

---

### Post by christhemonkey on 2007-03-07
Follow a howto:
[https://help.ubuntu.com/community/PureFTP?highlight=%28ftp%29](https://help.ubuntu.com/community/PureFTP?highlight=%28ftp%29)

A howto similar to that.

---

### Post by mips on 2007-03-07
> **christhemonkey said:**
> Follow a howto:
[https://help.ubuntu.com/community/PureFTP?highlight=%28ftp%29](https://help.ubuntu.com/community/PureFTP?highlight=%28ftp%29)

A howto similar to that.

Just keep in mind that normal FTP is NOT secure.

---

### Post by mips on 2007-03-07
> **fjr0122 said:**
> How would I set that up?

I dunno. This is the part where you start getting *your* hands dirty, not mine :)

I suggest Google for SFTP/SSL FTP and maybe scoure the debian or gentoo documentation.

EDIT: Actually if people were'nt to lazy to do a keyword search here stuff like this can be found:
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)
[http://ubuntuforums.org/showthread.php?t=347478](http://ubuntuforums.org/showthread.php?t=347478)

---

### Post by fjr0122 on 2007-03-08
> [http://ubuntuforums.org/showthread.php?t=347478&page=2](http://ubuntuforums.org/showthread.php?t=347478&page=2)

That's a relevant thread. The thing I have had a problem with is getting around my (and his) router, does SSH facilitate that?

---

### Post by mips on 2007-03-08
You will have to open the correct tcp/udp ports.

---

