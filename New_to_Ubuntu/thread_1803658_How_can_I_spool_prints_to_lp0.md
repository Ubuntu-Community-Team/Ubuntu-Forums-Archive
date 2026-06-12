---
title: "How can I spool prints to lp0 ?"
date: 2011-07-13
forum: New to Ubuntu
---

### Post by s1baker on 2011-07-13
Hi,
How can I spool my plots to /dev/lp0 ?

I use Virtualbox running in Ubuntu with XP as a guest OS. I use a cad
program in XP to make plot files that I have to copy over to Ubuntu so that I can send them to my lpo printer. ( Virtualbox is not able to access the lp0, so I have to make plot files and send them to Ubuntu so that I can plot them ).

When I go into the terminal in Ubuntu to plot the files I use this command :
```
cp plotfile /dev/lp0
```
and it works just fine except I can only plot one at a time, I have to wait for the first plot to finish before the terminal will let me call for another plot.

Thanks

---

### Post by The Cog on 2011-07-13
The command **lpr plotfile** might do it. You could try variations on:
> cat plotfile1 plotfile2 > /dev/lp0
cat plotfile* > /dev/lp0
lpr plotfile1 plotfile2
lpr plotfile*


---

### Post by s1baker on 2011-07-13
thanks, I will try these.

---

