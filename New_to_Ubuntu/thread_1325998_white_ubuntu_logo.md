---
title: "white ubuntu logo"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by MrKlean on 2009-11-14
When my system boots up.. the Ubuntu logo in white stays up for about 10 seconds.  Is there a way to shorten this time.  Windows boots in about 7 seconds less..and I think this is the problem.
Thanks !!

---

### Post by lavinog on 2009-11-14
Is this a WUBI install?
did you do a clean install or upgrade?

There is a application called bootchart in the universe repository.
It will generate a chart showing what happens during your boot.
It will extend your boot some, so when you don't need it, remove it.

Another thing you can do is disable the splash, and watch the messages.
I have only upgraded to karmic, so I am not familiar with grub2 yet for enabling verbose messages.

---

### Post by MrKlean on 2009-11-14
WOW>. I shoulda been more detailed LOL!!!  It is a fresh install of Karmic 32 bit ; ) It uses grub 2.  Thanks, I'll give that boot thing a try ; )
Thanks again !

---

### Post by cabrey on 2009-11-14
First run: ```
sudo add-apt-repository ppa:ubuntu-boot
```

Next: ```
sudo aptitude update && sudo aptitude full-upgrade -y
```

Then reboot. The first bootup after installing the new kernel and readahead daemon will be longer, but the next time should knock about 10 seconds off your boot sequence.

---

### Post by lavinog on 2009-11-14
> **cabrey said:**
> First run: ```
sudo add-apt-repository ppa:ubuntu-boot
```


I would hold off on doing this.
I have read a couple of users saying that this made things worse.
Also I would avoid using the -y switch on any upgrade as it will not let the user review the update first...this is how some users accidentally remove critical packages.

There was a kernel update recently, sreadahead should have been updated too.

---

