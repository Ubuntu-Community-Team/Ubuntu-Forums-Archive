---
title: "Gateway laptop MX6436 no internet, Ubuntu 8.10"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by Yed Ied on 2009-01-14
This is my first laptop (stock machine) and I have no idea how to get er done.  If someone would walk me through this, I would appreciate it.
Thanks   Yed Ied

---

### Post by handydan918 on 2009-01-14
Assume you are talkiing wireless connection? 
Need the output of ```
lspci | grep -i net 
```

---

### Post by ieee488 on 2009-01-14
To help us, help you.

Report back after reading the Sticky post over at the Networking message board.

---

### Post by Yed Ied on 2009-01-14
I network this H P and a Mac off a verizon router, without difficulty, and I will be the first to say MS sucks, but it is what I know.  I can't even find the reading material you suggested, and I know nothing about writing code, not that I wouldn't like to.  The Gateway laptop worked wireless off of the verizon router, but not now.  I wiped the disk and installed Ubunto,which I like so far, however the lack of internet isn't acceptable.  I have been through several forums and I am embarassed to the point of going back to XP Pro.  I really appreciate your time and willingness to share your info with me, however I am not an idiot but I'm not getting this.

---

### Post by anewguy on 2009-01-14
> **Yed Ied said:**
> I network this H P and a Mac off a verizon router, without difficulty, and I will be the first to say MS sucks, but it is what I know.  I can't even find the reading material you suggested, and I know nothing about writing code, not that I wouldn't like to.  The Gateway laptop worked wireless off of the verizon router, but not now.  I wiped the disk and installed Ubunto,which I like so far, however the lack of internet isn't acceptable.  I have been through several forums and I am embarassed to the point of going back to XP Pro.  I really appreciate your time and willingness to share your info with me, however I am not an idiot but I'm not getting this.

Here's the deal - Ubuntu needs the driver for your wireless adapter.  In order for us to help find and install it, we need some information first:

- open a terminal window (applications/accessories/terminal)
- type:

lspci <enter> copy and paste the output from that back in a reply here.

sudo lshw -C network <enter> copy and paste the output from that back into the same reply here.

What we are trying to do above is identify the wireless adapter and hopefully its' chipset so we can try to find the driver.

We look forward to your reply!

Dave :)

---

