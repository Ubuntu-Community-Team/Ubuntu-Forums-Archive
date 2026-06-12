---
title: "Error downloading flashplayer"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by Gulfvet91 on 2009-08-27
I am having all kinds of trouble when I try to download things to my laptop now.  I just tried to download Flash Player and I got  

 [COLOR=Red]ERROR: Dependency is not satisfiable: libnspr4-dev[/COLOR]

What da hell be going on?

---

### Post by Villiam on 2009-08-27
I found a similar problem and its solution. Install these libraries before install Adobe Flash Player 10.0.32.18.deb 
 
For install you can use for favorite package manager or download it directly and then 'dpkg -i' 
 
Etch users: 
 
[http://packages.debian.org/etch/libnss3-dev](http://packages.debian.org/etch/libnss3-dev) 
[http://packages.debian.org/etch/libnspr4-dev](http://packages.debian.org/etch/libnspr4-dev) 
 
Lenny users: 
 
[http://packages.debian.org/lenny/libnss3-dev](http://packages.debian.org/lenny/libnss3-dev) 
[http://packages.debian.org/lenny/libnspr4-dev](http://packages.debian.org/lenny/libnspr4-dev) 
 
Jaunty users: 
 
[http://packages.ubuntu.com/jaunty/libnss3-dev](http://packages.ubuntu.com/jaunty/libnss3-dev) 
[http://packages.ubuntu.com/jaunty/libnspr4-dev](http://packages.ubuntu.com/jaunty/libnspr4-dev) 
 
(Note that those libraries are availables in other tastes as well)

---

### Post by Gulfvet91 on 2009-08-27
Many thanks, Villiam!  I will try that.

---

### Post by Gulfvet91 on 2009-08-27
So I went to the first link for Jaunty and It shows me 3 files and it says whether or not I download 2 of them depends.  Depends on what?  Do I need all 3 files or do I just download the one that is sure of itself?

---

### Post by Gulfvet91 on 2009-08-27
I did click on the third one and now it says Depends.  Is this a meeting of Apathy International?

---

### Post by Gulfvet91 on 2009-08-27
And now it's telling me I need to use synaptic to download this package and I have no idea how to do that.

---

