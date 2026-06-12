---
title: "Does 64 Bit Ubuntu still run 32 Bit programs?"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by RealG187 on 2009-11-17
If I can't find a 64 bit package, can I use 32 bit ones? I have DEB packages for lots of 32 bit programs, are they useless in Ubuntu 64?

---

### Post by Maheriano on 2009-11-17
Not useless, if you search the forums you'll find a command to force an install of a 32 bit application on a 64 bit machine. It'll use a wrapper to pad the memory addressing and still work fine.
I wouldn't do it though, just seems like it would somehow mess up the memory mapping.......but who knows.

---

### Post by dca on 2009-11-17
'ia32-libs' I think is the wrapper/library, should be in repos.
 
You may have trouble if you use say Adobe Reader and try to open PDF in FF web browser, tweaks are required and it still won't open in browser, but will open independent Reader window...  Other stuff like that....

---

### Post by dca on 2009-11-17
...oh, one other thing if you install 64bit Ubuntu and install a package from the repos, it will be 64-bit...  Unless of course you use that library and install debs off internet or something...

---

### Post by RealG187 on 2009-11-17
So they can be installed, but not the normal way. And there might be problems?

---

### Post by aspergerian on 2009-12-21
Running some 32 bit programs on 64 bit Ubuntu remains an important concern. As of today, my Acer 1410 runs 64 bit 9.10, and the major drawback is that Adobe Reader wouldn't even permit a download into Ubuntu's install program - stating "wrong architecture" or something like that. I did lots of web searching and some of the solutions that seem to have worked several weeks or several months ago - specifically for Adobe Reader - seem to have been disabled (though could be me?). 

Evince still doesn't allow copying from within a column on a two column page, which is why I need to run Adobe Reader in Ubuntu. 

Interestingly, on my Vista 64 bit and Windows 7 64 bit machines, all the 32 bit programs I've loaded have worked. Nonetheless, I prefer my Ubuntu machines and would prefer a way to make Adobe Reader work in 64 bit 9.10.

Perhaps a newer patch that works has been posted. I haven't found it.

---

### Post by steveneddy on 2009-12-21
Here is the command for installins 32 bit .debs on a 64 bit machine:

```
## install 32 bit software on 64 bit machines

sudo dpkg --force-architecture -i PackageName.deb
```

also

```
sudo apt-get install ia32-libs
```

should get you going.

---

### Post by aspergerian on 2009-12-22
> **steveneddy said:**
> 
```
sudo apt-get install ia32-libs
```


Had to 
```
cd Downloads
```

For now, the specification is: 
```
sudo dpkg --force-architecture -i AdbeRdr9.2-1_i386linux_enu.deb
```

Adobe Reader has been installed on my Acer 1410 running 9.10 64 bit. 

Thank you!

---

