---
title: "Deleted driver files off of desktop after installing, now wireless card dissapears?"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by Sidneyaks on 2009-01-31
Ok, so I have the madwifi drivers on my desktop, and I installed them and everything works fine. So after that i delete the folder the install files were in, and my wifi stops working the next time I boot. I restore the folder, and bam, my wifi works again. How can I get this folder off of my desktop without killing my wifi?

Thanks for the help, here are my system specs if they're needed

Toshiba Satellite Laptop
Atheros Wifi internal card using mad-wifi drivers
Ubuntu (of course) 8.04

I suppose I should mention that I did boot into windows between the time I first delete the folder and when I booted in linux again. Might that have something to do with it?

---

### Post by yeats on 2009-02-01
Some programs you install end up living wherever you've un-tarred them (sounds like this is the case here).  You can use the /opt directory for those sorts of programs.  When you download the program to your desktop, you can unpack the tarball into /opt.  Alternatively, if you're comfortable in the terminal (and this is a good task to learn to do anyway), you can

```
cd /opt
wget http://url.for/program.tar.gz
tar xzf program.tar.gz

```

Then your program's directory will live in /opt - an out-of-the-way locations for optional programs.

---

### Post by Sidneyaks on 2009-02-01
Cool, thank you, didn't know about that folder. I didn't download the driver tar again, but I moved it in the terminal

sudo mv location/file location/destination

I supposed if i move it in the terminal it's not like moving it in windows, I'm telling linux exactly where I'm moving it, aren't I? Does it change all the file routings?

---

