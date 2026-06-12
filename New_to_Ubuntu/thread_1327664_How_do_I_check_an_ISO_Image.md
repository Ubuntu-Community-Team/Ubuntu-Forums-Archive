---
title: "How do I check an ISO Image?"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by dooglo on 2009-11-15
To start with, I'm a complete and utter noob at Linux.  I installed 9.1 32 bit on a spare box at home from a CD that I requested.  Ok, no problem.  But, I'd like to taste some other versions of Linux.  So, I've downloaded and seeded OpenSuSE 11.2 32 bit Live CD.  I can't for the life of me burn it to a CD.  I thought that maybe it's corrupted, so how do I check to see if the image is?

I can't make heads nor tails of how to.

Thanks,

D.

---

### Post by coffeecat on 2009-11-15
What are you using to burn the ISO?

Have a look at this link:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

It's for Ubuntu, but the principle is the same for any distro's ISO. It also links you to how to md5sum. You can get the md5sum for your Suse ISO from the Suse website.

---

### Post by mprince on 2009-11-15
One way is to open a terminal and type:

```
md5sum /path/to/your.iso
```

Then compare the md5 it generates with the md5 listed for that iso.

---

### Post by gordintoronto on 2009-11-15
What happens when you try to burn the image to a CD?  What program are you using?

---

### Post by ranch hand on 2009-11-15
A little more detailed instruction on md5sum;
```

https://help.ubuntu.com/community/HowToMD5SUM

```
Between that and the how to burn link from coffeecat you should do OK.

Make sure you are burning as an image and as slow as you can get your burner to go.

---

