---
title: "How to update GRUB screen?"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by D1Knight on 2010-02-06
I just updated Ubuntu 8.04LTS, to the latest updated kernel. I have multiple OS on my computer. The GRUB screen does not show the latest updated kernel for Ubuntu 8.4LTS. How do I fix this? I thank you kindly.:)

---

### Post by mushwars on 2010-02-06
did you try

```
sudo update-grub
```

that should do it, if not there is something missing from your config.

---

### Post by tommynz1975 on 2010-02-06
If muchwars solution did not help

and you go to your menu

Places > search for files 

and search for 

initrd.img

look in  file system

to see if the kernel you just downloaded is their.

I just had this issue under 9.04

If you'd like to have a look at my posting

[http://ubuntuforums.org/showthread.php?t=1400254](http://ubuntuforums.org/showthread.php?t=1400254)

---

### Post by D1Knight on 2010-02-07
> **mushwars said:**
> did you try

```
sudo update-grub
```that should do it, if not there is something missing from your config.
Mushwars, thanks for your suggestion. It did not work for me, tho (It maybe something to do with the other OS's partitions?).:)

---

### Post by D1Knight on 2010-02-07
> **tommynz1975 said:**
> If muchwars solution did not help

and you go to your menu

Places > search for files 

and search for 

initrd.img

look in  file system

to see if the kernel you just downloaded is their.

I just had this issue under 9.04

If you'd like to have a look at my posting

[http://ubuntuforums.org/showthread.php?t=1400254](http://ubuntuforums.org/showthread.php?t=1400254)
Tommynz1975, thanks for your reply. :)I checked, the correct initrd.img file is there, also I looked at your posting/thread. :)I got a little cornfused (I am noobish.). :confused:I just ended up (not a solve to ?, this is just want I did in this situation-this time.) adding another partition with OS, hence a new GRUB. This is OK for now. FYI-I wanted 1 more OS.

I am still nooby. I seem to remember something GRUB editor/configuation tool (maybe wishful thinking).? Please correct me if I am wrong.

It would be great if there was a simple GUI (Yeah, I know, the dreaded GUI.:lol:) Grub editor, say on a Live Disc. Just a thought.:) Well I am set, until the next kernel update. If there are any other suggestions, please I am open to them. Cheers and Peace.

---

