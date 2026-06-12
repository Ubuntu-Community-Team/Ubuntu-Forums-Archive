---
title: "trying to do a clean install over Feisty"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by nikhil17 on 2009-01-17
Hi,

I am new to Ubuntu. Sometime back I installed Feisty (from a CD that came w/ a Ubuntu book) while keeping windows. Now I want to do a clean install of 8.10 from a live CD (which I have). I still want to keep windows till I get proficient with Ubuntu.

My question is when I do install 8.10 will it overwrite on Feisty (I want it to); i.e. I do not want to end up with both Feisty as well as Intrepid ibex. I have copied whatever little stuff I had worked on in Feisty.

I looked over on the web pages which deal with download/upgrade but they didn't talk about this situation. The upgrade seems arduous as I have such an old version.

Any help will be much appreciated.
Thanks,
Nikhil

---

### Post by adult swim on 2009-01-17
just boot the cd and select install.  when you get to step 4 choose manual.  then you will need to select the partition that you have feisty on and double click it.  as the mountpoint choose /  and select it to be formatted to ext3.  then you can continue as normal.

---

### Post by utnubuuser on 2009-01-17
Hi --  I never upgrade through the upgrade path.  I usually shrink the existing Ubuntu partition so there's enough room for a new install, install the new version, importing all settings and documents, then delete the old version/partitions.
Mind, I'm not using dual boot. so there might be other issues to consider.

---

### Post by stefangr1 on 2009-01-17
It is a good idea to use different partitions for data and for the root filesystem, such that when you do a fresh install your data will stay unaffected.

Resizing is and then install on the emptied space is a very bad idea, since it is a relatively risky operation that you should not perform without first making a backup of all important data. But then when you do in fact make such a backup, you can as well install over the old root partition.

---

### Post by earthpigg on 2009-01-17
> **adult swim said:**
> just boot the cd and select install.  when you get to step 4 choose manual.  then you will need to select the partition that you have feisty on and double click it.  as the mountpoint choose /  and select it to be formatted to ext3.  then you can continue as normal.

that.

and do not mis-click.

:guitar:

---

### Post by nikhil17 on 2009-01-17
Thanks. Think I need a little more hand holding! 

At step 4 if I click on manual the 'after' disk partition shows as if I am using entire disk. 

The Guided option shows "Guided - resize SCS|l (0,0,0), partition # 3 (sda) and use freed space. Below it shows "New partition size" with 2 rectangles with an identity sign (an '='sign with another '-'on top). The rectangeles have this written 'Ubuntu 7.04...19%(3.0 GB)' and the other has 'Ubuntu 8.10 81% (13.3 GB)' written in it. Does that mean that the guided is overwriting only 7.04 and not windows?

---

### Post by nikhil17 on 2009-01-19
Many thanks.....it worked beautifully. Exploring Ubuntu 8.10 now....

---

