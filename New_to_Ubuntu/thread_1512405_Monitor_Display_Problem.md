---
title: "Monitor Display Problem"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by Nithingp on 2010-06-18
[B][SIZE=5][COLOR=Red]I am new in this community,and dont know much about linux[/COLOR][/SIZE]

I installed ubuntu 10.04 edition inside my windows XP using wubi(i dont know anything about partitions).Now ubuntu works fine and is better than i expected.[/B]:razz:
[B]
But i think my 17 inch LG (T705SH flatron CRT) monitor dont know who is ubuntu.

1)    I am not getting a full screen desktop,i think only 15 inch is now     visible.what   to do to get a full screen display.Is it necessary to install   seperate monitor drivers for ubuntu.

2)    The sound output is also not good.I think only mono sound is there.Is there any seperate drivers to solve this or is there any settings to change this?[/B]**:-({|=**
[B]
Pleaseeeeeeee help me.
please consider i am very new to linux:confused:

[/B]

---

### Post by realzippy on 2010-06-18
Welcome!
To help,we need more infos about your hardware:
What graphics card/sound card do you use?

Best info is to type in terminal:

```
lspci | grep -i audio
```

and

```
lspci | grep VGA
```


Please post the outputs...

---

### Post by Nithingp on 2010-06-20
> **realzippy said:**
> Welcome!
To help,we need more infos about your hardware:
What graphics card/sound card do you use?

Best info is to type in terminal:

```
lspci | grep -i audio
```and

```
lspci | grep VGA
```
Please post the outputs...


The outputs is as shown below
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

please help):P

---

