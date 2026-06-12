---
title: "No wireless reception on laptop"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by pappy50+ on 2010-03-05
[SIZE=4]Please help! Running Hp Pavilion dv5 -1125nr laptop. Originally it had Vista installed, but with corrupted files (would not boot up.) With little knowledge of Linux decided to run Ubuntu. Started with Intripid Ibex and upgraded to Karmic Koala. With a lot of help on line, resolved all problems except wireless capabilities (which did work at one time, then mysteriously disappeared.) I am confident this is a configuration problem. Please walk me through this step by step.[/SIZE]

---

### Post by Greenwidth on 2010-03-05
Type (or paste) the following into a terminal to determine what card/chipset you have:
```
lspci | grep 802
```
and post the output here.

---

