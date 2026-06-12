---
title: "Ubuntu 9.04 networking laptop esprimo v5535"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by Biosteel on 2009-12-13
hello i newly installed Ubuntu on my laptop. But neither my wired network nor my wireless wont work.  After some researsch time on the google i found out that there are no compatible drivers for this computer. I also had problem with the graphics but that i solved myself trough xorg.conf 


But back to the problem. is it true that there arent any compatible drivers for this model Fujitsu siemens esprimo V5535 ?

---

### Post by mikewhatever on 2009-12-13
If you found the info form reliable sources, then it must be true. Fujitsu siemens esprimo V5535 doesn't tell tell me much, can you provide some info about its networking hardware, or a link where that info can be found.

---

### Post by Biosteel on 2009-12-13
> **mikewhatever said:**
> If you found the info form reliable sources, then it must be true. Fujitsu siemens esprimo V5535 doesn't tell tell me much, can you provide some info about its networking hardware, or a link where that info can be found.


acctully really hard to find. but heres a link [http://www.electronic-repair.co.uk/shop/notebooks/fujitsu-siemens-v5535-15-4-w-celeron-m-570-/-2-26ghz/prod_77.html](http://www.electronic-repair.co.uk/shop/notebooks/fujitsu-siemens-v5535-15-4-w-celeron-m-570-/-2-26ghz/prod_77.html)


i really hope someone can help me cause im ripping my hair off. and my wired network dont even work. If just that one had worked i would be satisfied. men icke sa nicke.:(

---

### Post by mikewhatever on 2009-12-14
Thanks for the link. According to that, you have an Atheros wireless, a notoriously linux unfriendly chip maker, but there is no model. 
You can get all the info about your computer's hardware by typing the following command into Applications-Accessories->Terminal:
```
sudo lshw > ~/Desktop/hardware.txt
```

When it's done, you'll have a text file on the Desktop named hardware.txt. Please attach it to one of the following posts.
The fact that ethernet doesn't work too is rather strange. Can you plug in the cable and post the output of <ifconfig> (without brackets).

---

