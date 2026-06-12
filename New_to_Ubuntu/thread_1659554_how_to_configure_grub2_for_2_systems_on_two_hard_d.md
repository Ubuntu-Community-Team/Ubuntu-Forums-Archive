---
title: "how to configure grub2 for 2 systems on two hard drives?"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by Unewbeginner on 2011-01-04
Hello everyone, I just installed ubuntu 10.10 server on one of my hard drives, and I have another hard drive with windows 7 installed. How could I configure grub2 to get the startup menu that I could select which system I will get in? 

I searched in the forum and got the information that I should write something in /etc/grub.d/40_custom. But what exactly I should do? 

Sorry for the question, but I'm really new to Ubuntu.Thanks.

---

### Post by Unewbeginner on 2011-01-04
I found the answer somewhere.

adding the scripts below to /etc/grub.d/40_custom

```
menuentry "Microsoft Windows XP" {
	insmod chain
	set root=(hd1,1)
	drivemap -s hd0 hd1
	chainloader +1
}
```

and then run 

```
sudo update-grub
```

---

