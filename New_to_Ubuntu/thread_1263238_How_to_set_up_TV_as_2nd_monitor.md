---
title: "How to set up TV as 2nd monitor"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by dominican_dutchboy on 2009-09-10
I'm trying to hook my laptop (Dell Inspiron 2200) up to my TV to use my TV to watch movies on mostly.  I have the VGA out cord that hooks up to the S-video, but when I plug it in all I get is fuzz on the TV.  I went into my "display" settings and still only one monitor appeared.  How do I get it to show up on my TV?

---

### Post by neurostu on 2009-09-10
check out this:
[http://brainstorm.ubuntu.com/idea/204/](http://brainstorm.ubuntu.com/idea/204/)

---

### Post by tgalati4 on 2009-09-10
Did you turn on TV in the advanced BIOS settings?  Using Windows drivers, you can normally turn on the TV-out connection using the software driver, as well as make adjustments--color, overscan, etc.

You can do the same in linux, you just have to find the right switches and put them in your xorg.conf.  This is a severe pain in the butt.

Normally you will set your laptop display to 800x600 or 1024x786 (max).  Don't get your hopes up.  NTSC is something like 425 lines of resolution on a good day.

Then hit the FN-F7 key a few times to mode-cycle the laptop.  Your key combo may be different.

Works almost out-of-the-box on my thinkpad t43p with an ati graphics chip using the open drivers, so I'm pretty sure it's possible on your Dell Inspiron.

Picture is not great.  It's really a novelty than a practical display.

---

### Post by dominican_dutchboy on 2009-09-15
I'm sure that advice is helpful, however on Ubuntu I have no idea how to find/change any of that.  Step by step directions would be great. 
Thanks

---

### Post by neurostu on 2009-09-15
Step by step instructions really aren't possible unless you find someone who has the exact same hardware you have.   So like tgalati4 said above you're going to have to figure this out on your own.

Welcome to the wonderfully fun (and sometime aggrevating) world of linux

---

