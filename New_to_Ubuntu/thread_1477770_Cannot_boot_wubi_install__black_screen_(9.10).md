---
title: "Cannot boot wubi install / black screen (9.10)"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by lmaolmao on 2010-05-09
hi,

i'm sorry if this is a common thing.  But i'm at a loss as i'm not sure what error message i'm getting, so i can't even google it :confused:

I've installed either kubuntu or ubuntu 9.10 using the wubi thingy.  I also tried with unetbootin.

When i tried 10.04 it worked fine, and 9.04 live cd works (except hdmi audio which is why i'm going to 9.10).  all my iso's and disks pass md5 check.

So, after the install in windows i reboot and select k/ubuntu it loads up the splash screen then the screen goes blank for a few seconds and the monitor turns off.

i press ctrl+alt+F1 and i get the following screen -[[IMG]http://img708.imageshack.us/img708/5466/dsc0109nj.th.jpg[/IMG]](http://img708.imageshack.us/i/dsc0109nj.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)

any ideas? i'm assuming its something to do with my graphics card, as my old one (a 7950gt) worked fine.


Any help will be very appreciated!

Computer:

q6600 @ stock
zotac nvidia gt240 1gb ddr3
4gb 1066mhz ram
windows 7 32bit + wubi installed ubuntu OR kubuntu
single 320gb sata hdd
monitor connect via dvi,
projector via hdmi (unplugged and currently disconnected)

---

### Post by Ozymandias_117 on 2010-05-09
If it's already installed you can try typing ```
startx
```

But, it almost looks like that screen is part of an installation?

---

### Post by lmaolmao on 2010-05-09
i have tried "startx" it gives some more errors and goes back to the command line.

When this used to work on my 7950gt it was about to launch the installation, but it's getting stuck somewhere (i think).

I just redownloaded/reburnt 9.10 32bit as a live cd.  and get the same error.  I wonder why 9.04 works and 10.04 work, but not 9.10

oops, i just realized i'm not on my main computer (lol!!)

proper spec is:
amd x2 4200+ skt939
2gb 400mhz ram

but otherwise identical.

---

### Post by lmaolmao on 2010-05-09
i just tried the live cd with "safe graphics mode" and it worked.  So it's got to be a driver issue.

Unfortunately trying safe graphics with the wubi installation, doesn't work :(

---

