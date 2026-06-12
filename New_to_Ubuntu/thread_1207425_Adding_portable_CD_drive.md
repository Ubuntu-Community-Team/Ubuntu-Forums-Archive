---
title: "Adding portable CD drive"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by annie1234 on 2009-07-08
New to this. Please someone just offer me some advice before I get exasperated.  My son decided to buy Dell Inspiron Mini notebook but decided to go for Ubuntu rather than Windows.  I am totally lost with this system and only used windows and have bought a portable USB from Amazon claiming to be a Dell CD drive etc.  It has turned up but with a CD for Windows and turns out to be compatible CD drive rather than original Dell.  Can I somehow still get this portable CD Drive to work in UBUNTU and how do I do this.
Thanks

---

### Post by 3rdalbum on 2009-07-08
I'm not trying to sound patronising, but have you tried just plugging it in? CD/DVD drives should all work out-of-the-box, even on Windows.

---

### Post by nothingspecial on 2009-07-08
I agree, it should just work. I`ve got loads of those little windows disk that have come with various pieces of hardware. They are all still in the packet.
[URL="http://www.hintsandthings.co.uk/musichall/CDroms.htm"][COLOR="Magenta"]
101 things you can do with old cds[/COLOR][/URL]

---

### Post by annie1234 on 2009-07-08
please dont worry about patronising.  I am not a computer wizard and use my own desktop on a basic level.  See thats the thing.  when I plug it into my own desktop the desktop finds the hard ware straight away.  Plugging it into this Notebook I am using,  absolutely nothing.  the cd drive starts up and then stops.  nothing comes up on the screen.  dell have quoted me £25 for the ubuntu cd that should load the disc drive but i just see that as excessive and i am not sure if its necessary.  it should be as simple as you suggest. i dont know what to do.

---

### Post by lindsay7 on 2009-07-08
Try putting a disk in the drive and then plugging it in.  There should be a small hole in the front of the drive than you can push a paper clip in and open the drive.

---

### Post by halitech on 2009-07-08
shouldn't need to resort to using the paper clip to open the drive, should have a button to open it. Open it up, put a cd in, connect it to the laptop and see if you get an icon on the desktop for it. if you don't, open a terminal and post the output of
```
lsusb
```and ```
sudo fdisk -l
```

---

