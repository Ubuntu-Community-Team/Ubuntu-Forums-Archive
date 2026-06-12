---
title: "Airport Extreme"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by balt11t on 2009-05-13
Hello, I have used Ubuntu 9.01 on my Intel desktop before and I absolutely loved it, so I thought I would salvage my old iBook G4. I got the disk and everything worked fine, but I realized wireless wasn't working. I have looked in past tutorials and topics but nothing works! Help!

---

### Post by coffeeaddict22 on 2009-05-13
Hi,
More info would be nice.  Just a comment, it's 9.04 (the .04 is the month of release).
Open a terminal, put in the following commands, and they'll spit out a whole heap of info on your system; post it back here if you want more assistance...
```
lshw -C network
iwconfig
```

---

### Post by mkvnmtr on 2009-05-13
On my I book the wifi always worked after I enabled the hardware drivers up to 8.10. When I tried that on 9.04 it wasn{t able to download the firmware. I think I read somewhere it wasn't working on 9.04. A few days I was searching in the package manager and found the firmware. O forget what it is called or where it was at. I think bf43cutter or something like that. I figured what the heck and clicked on it to download and install. I didn't pay much attention because I was really after other apps and I don't use wireless. The next day I looked and my wireless was working. Still is. I am sorry this isn't a very good tutorial but it is what happende to me. I really don't think it is supposed to work on power pc in this distro.

---

### Post by balt11t on 2009-05-13
I actually fixed the problem experimenting with some things I found across the internet. In the bar at the top (not sure what else to call it), it was telling me I needed to update the wireless card driver. The only problem was, I was getting an error about how it couldn't find a directory to get the driver from. In a random stroke of brilliance, I decided to connect it to the internet via ethernet. Lo and behold, it worked. Thank you coffeeaddict for the help and so long until I run into another problem.

---

### Post by coffeeaddict22 on 2009-05-13
No Prob.  The top thing is called a panel; if you like toys right click on it , then add to panel.. you get to a menu where there's all sorts of interesting gadgets... if you're into gadgets, that is.

---

### Post by balt11t on 2009-05-13
I like Gadgets... They are my friend...

---

