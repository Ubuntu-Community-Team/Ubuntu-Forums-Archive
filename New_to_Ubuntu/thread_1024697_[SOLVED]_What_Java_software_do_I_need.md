---
title: "[SOLVED] What Java software do I need?"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by scotttie on 2008-12-29
Hi everyone,
my boy wants to get on to a online game called runscape but it requires Java, can anyone point me to a suitable site to download java for ubuntu 8.10?
thanks
Scottie

---

### Post by taurus on 2008-12-29
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudp apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin

```
When you get to the licensing screen, press the Tab key to highlight the <OK> and then Return to accept it.

You need to restart firefox after installing java's plugin.

---

### Post by scotttie on 2008-12-29
Thanks Taurus.

---

### Post by okey666 on 2008-12-29
[SIZE="1"]if you are using 32-bit ubuntu, simply open up synaptic (system>>admin>>synaptic) and search for:
> sun-java6

You can then select > sun-java6-jre and also something that should look like
> sun-java6-plugin

Others will confirm exact names.

Once you have ticked the boxes, hit "apply" and wait for the download etc.

Open up "runescape" (good game by the way) and see if it works. If not post back.[/SIZE]
[B][U]
On second thoughts, maybe I should read the whole thread before replying.[/U][/B]

---

### Post by scotttie on 2008-12-29
Thanks Okey666,
All up and running a treat, my boy is one happy bunny.
thanks
Scottie :D :D

---

