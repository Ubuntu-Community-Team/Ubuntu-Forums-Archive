---
title: "location of xorg.conf (live environment)"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by Phlex_de on 2010-03-23
I was trying to copy the xorg.conf file but it is not located at etc. 

Since Ubuntu is up and running (live) there must be some working configuration, but where can I find or save these settings?
Both find / xorg.conf and "Search for Files" in the menu couldn't locate it.

Or could someone give me a working xorg.conf who happens to have a Asus 1005PE?

(I am testing Arch on my netbook but I am stuck at configuring X.)

---

### Post by halitech on 2010-03-23
since 9.04 there is no default xorg.conf file as everything is supposed to be handled automagically. Sorry, but I can't help with a working copy of xorg.conf for that machine as I don't have one.

---

### Post by Phlex_de on 2010-03-23
Thanks for the fast reply.

If there is no file, is there any way access the automated settings in a different way? 

I guess if that's not possible it is worth a try with an older version..

---

### Post by halitech on 2010-03-23
not that I know of but trying a copy of 8.04 or 8.10 should work

---

### Post by bodhi.zazen on 2010-03-23
> **Phlex_de said:**
> If there is no file, is there any way access the automated settings in a different way?

In general, there are not great tools to edit xorg.conf. Most people do it manually and sometimes the old options works and sometimes they do not, so trial and error.

What are you wanting to do ?

---

### Post by Phlex_de on 2010-03-23
I was following the install guide: [http://wiki.archlinux.org/index.php/Beginners%27_Guide#A:_The_xorg.conf_file](http://wiki.archlinux.org/index.php/Beginners%27_Guide#A:_The_xorg.conf_file)

Xorg -configure creates a file which I copied to /etc/X11/xorg.conf. 
startx presents me a black screen with two terminals and a clock on the top right. Then nothing responds and I need to hold the power button to shutdown. 

I am just stuck at this point and I thought it is related to the config file..

---

### Post by wojox on 2010-03-23
Did you install hal and start it?

---

### Post by Phlex_de on 2010-03-23
No, I did not. ](*,)

I just read through the HAL part and realized that this is not optional. The warning describes exactly my problem. 

Thank you very much for pointing that out, this was a stupid mistake on my part.

---

### Post by wojox on 2010-03-24
Welcome. Remember just read their wiki real good. It's very well written. ;)

---

