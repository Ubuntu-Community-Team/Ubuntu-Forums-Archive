---
title: "i followed wifidocs!  got a problem"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by christophdanger on 2007-10-01
I followed this howto 

[https://help.ubuntu.com/community/WifiDocs/Driver/1390]("https://help.ubuntu.com/community/WifiDocs/Driver/1390")

i got through most of it, then I got to the line

[FONT="Lucida Console"]$sudo ndiswrapper -i ~/.driver/wifi/DRIVER/bcmwl5.inf[/FONT]

console says tells me that ndiswrapper is not found so I backed up to the beginning again and tried to install ndiswrapper again.

once I get to this line in the howto (note: this is near the top of the howto)

[FONT="Lucida Console"]$sudo apt-get install build-essential linux-headers-`uname -r`[/FONT]

console says 

[FONT="Lucida Console"]E: Couldn't find package linux-headers-uname -r[/FONT]

I have no clue what the heck is going on and why that it just can't recognize the damn card......arghhhhhhh

any help?

---

### Post by kevdog on 2007-10-01
Make sure you either type or cut and paste the exact syntax of this command, that's were you are going wrong:

sudo aptitude install linux-headers-`uname -r`

Notice those are backticks and not quotes.

---

### Post by spd106 on 2007-10-01
uname -r is a command line program that prints the current kernel version. If you use backticks rather than quotes, it runs the command inline. The idea is that uname -r will substitute for the current kernel version, e.g. 2.6.20-16-generic
```

user@hostname:~$ uname -a
Linux ubuntu 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux
user@hostname:~$ uname -r
2.6.20-16-generic
user@hostname:~$ echo "my kernel is `uname -r`"
my kernel is 2.6.20-16-generic

```

You can install this package via Synaptic, just search for linux-headers and pick the one with the highest number. 

Getting back to the WifiDocs guide, it's probably a better idea to copy + paste those commands, except for the preceding $.

---

