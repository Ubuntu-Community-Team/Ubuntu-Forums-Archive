---
title: "routine file check stalls at 70%, forcing me to hard boot and and escape"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by w.g.hanna on 2009-04-10
I run hardy - generally default, but i also installed kubuntu with synaptic just to see what it was like.  after doing that, the load up screen said kubuntu instead of ubuntu - but alsways figured it was insignificant.  i start my computer up, and it does a routine drive check.  in the bottom corner it has a percentage, and a ration (eg 0/1890 or something).  when the first number of the ration quals the last  - presumable meaning it should be done - the percentage reads 70% and then everything stops.  

i mean, i sat here looking at it for 10 minuites and nothing happened.  i pressed escape, and nothing.  this happened twice - and the second time i took a nice long dump only to come back to it saying 70%.  so i hard booted, pressed escape, and everything's fine.

i did a search, and i know that the drive check is routine every 30 boots.  i've sat through it before and everything was fine.  

is it kde?  either way, what should i do?

---

### Post by keplerspeed on 2009-04-10
Make sure your system is up to date, by either going to the update manager or using the terminal, ie 'sudo aptitude update'.

Its hard to tell why the system would hang at 70%, and if everything is fine now I dont think its worth the effort to try to work out why it did it, especially if it doesnt do it again.

Good Luck!

---

### Post by mikechant on 2009-04-10
I guess I would try booting from a Ubuntu live cd and using the the following command (assuming this is an ext2/3 filesystem)

```
sudo e2fsck -v /dev/sdxn
```

where sdxn is the relevant device such as /dev/sda3 and -v is 'verbose' mode - so you might get more info.

If you're not sure which device the problem filesystem is on, just start up gparted (system>admin>partition editor on the live CD) and it should be obvious

---

