---
title: "Download Monitor - reset data"
date: 2014-01-26
forum: Networking &amp; Wireless
---

### Post by Jeyaprakash on 2014-01-26
Is there any way to reset the data in the download monitor, to make it start fresh? I tried removing it completely from the package manager. After installing again, it shows the old data. 

Doing a search, I came to know about the monitor in screenlets. But now, the screenlets website seems to be down and I am not able to get the screenlet for monitoring data. 

I am open to new recommendations also. I just need a monitor to track my usage and I should be able to reset the data. I am on a limited bandwidth. So, I have to monitor!

---

### Post by ibjsb4 on 2014-01-26
Have you looked in ~/.config for a file?

---

### Post by Jeyaprakash on 2014-01-26
Could not find any folder related to Download Monitor inside the .config folder which is inside the Home folder! I am not an expert!  :D How could I trace where Download Monitor is storing its data? What are the other possible locations I should check?

---

### Post by ibjsb4 on 2014-01-26
Sorry :)

The "~" represents Home in the command line.

I am not sure of what your referring to as a "download monitor"; can you post a pic?  Or could you tell me the package name.

---

### Post by Jeyaprakash on 2014-01-26
The package name is download-monitor. Through synaptic package manager, I found its location and dependencies. It is dependent on vnstat it seems!

---

### Post by ibjsb4 on 2014-01-26
Ok, give me a few minutes.  I just installed it and going to play with it.

---

### Post by Jeyaprakash on 2014-01-26
Thank you very much!!

---

### Post by ibjsb4 on 2014-01-26
I gave it a try, but this package will not properly install on my system, got a problem with child processes.

Looks like I will be of no help :(

Edit:  Have you seen this?  Maybe bitbuget is the way to go.

[https://launchpad.net/download-monitor](https://launchpad.net/download-monitor)

---

### Post by Jeyaprakash on 2014-01-26
I nearly got it... It has got something to reset the vnstat. In the command line, I got into vnstat which is inside /usr/lib. If I type vnstat, it gives the output! I also got the command for vnstat here: [http://humdi.net/vnstat/man/vnstat.html](http://humdi.net/vnstat/man/vnstat.html). My interface is ppp0. I am trying to reset it with the command  vnstat -i ppp0 --reset. But, it is not working. Still exploring! May be I am doing some mistake, in command line here!

---

### Post by ibjsb4 on 2014-01-26
If I think of anything I will post back, but at this point, I bid you good luck :)

---

### Post by Jeyaprakash on 2014-01-26
Thank you! Trying to install BitBudget! Thanks for your efforts!!

---

### Post by Jeyaprakash on 2014-01-27
I installed BitBudget. But, it did not open at all. I do not understand the problem. I figured out the way to reset the data in vnstat. The reset command did not work. So, I used 'vnstat -i ppp0 --force --delete' Then, I created the interface again using the command 'sudo vnstat -u -i ppp0'

---

