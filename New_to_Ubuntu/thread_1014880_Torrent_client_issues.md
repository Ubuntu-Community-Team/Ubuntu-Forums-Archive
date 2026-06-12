---
title: "Torrent client issues"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by Dahlia on 2008-12-18
Hello! ):P

First of all, I've had some issues regarding Transmission - it won't even start, and it doesn't matter how I try starting it up. I'm not crying over it or anything so if no one know what to do, I don't really mind =)

Second, I installed Ktorrent to use instead of Transmission, but when I try to open a torrent and are going to choose Ktorrent instead of Transmission, I can't find it anywhere and I can't find it when I search.. 

I could save the torrents and open them via Ktorrent, but seriously, I'm lazy and wanna make it simple.. So if anyone knows what to do, I'll really appreciate it!

Thanks!

---

### Post by kpkeerthi on 2008-12-18
Did you try starting transmission from command line? Might print some useful information regarding the problem.

To find out where ktorrent is, type
```
which ktorrent
```
```
whereis ktorrent
```
```
sudo updatedb && locate ktorrent
```

---

### Post by taurus on 2008-12-18
1.  Run transmission from a terminal and see what is the error message.

Applications -> Accessories -> Terminal
```
transmission
```

2.  Ktorrent should be in /usr/bin.

---

### Post by Dahlia on 2008-12-18
Well, it says that Transmission has a segmentation fault?
(And yes, I found Ktorrent, woho!)

Thank you for answering!

---

### Post by taurus on 2008-12-18
Which release are you running?  Did you install transmission from the repos?

---

### Post by Dahlia on 2008-12-18
I have 8.04 it it was there from the installation...

---

### Post by kpkeerthi on 2008-12-18
You may want to try the latest version available for hardy here: [http://www.getdeb.net/release/3199](http://www.getdeb.net/release/3199)

Download the .deb file and double-click it to start the installation.

---

### Post by Dahlia on 2008-12-18
Ok, I'll try. =)

Thanks!

edit*Transmission works now, thanks for all the help!

---

### Post by kdreimiller on 2008-12-18
while this wasnt your question, i prefer deluge.  it has some more bells and whistles so i feel like i have a little more control over it.

---

