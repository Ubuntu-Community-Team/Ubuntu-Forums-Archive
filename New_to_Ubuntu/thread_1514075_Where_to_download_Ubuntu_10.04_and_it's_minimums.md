---
title: "Where to download Ubuntu 10.04 and it's minimums"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by Kharlo on 2010-06-20
Hi, i have several days trying to download ubuntu fro its home page but the download ends with only 20 or 30mb,

does somebody knows a link where i can download the full ubuntu 10.04 original cd image without problem?

can i burn that image in a dvd+rw?

and about the minimums (i still have the problems with the missing gnome panels at startup) isn't 5gb too much? can i prove it in 4gb? has somebody installed in a lower than 5gb space?

greetings

---

### Post by -humanaut- on 2010-06-20
Search google for the minimums or ubuntus site also You may have alot better luck using a torrent its always worked better for me.

---

### Post by Pollox on 2010-06-20
To add to that, you can find all the alternate download options (torrent, alternate cd, etc) on the "Alernative downloads tab" on [the page where you download Ubuntu]("http://www.ubuntu.com/desktop/get-ubuntu/download").

---

### Post by mk1w86 on 2010-06-20
I also recommend using a torrent if you are having problems with the main download.  Out of interest have you tried a different mirror?

If you need a smaller install footprint you might want to take a look at the alternate CD which will give you a greater range of options regarding what packages you install.

Also you should be able to burn the CD image to a DVD. ;)

---

### Post by Kharlo on 2010-06-20
different mirrors mmm.... (je je je i thought that  was downloading it form a different page than ubuntu) wich one is the mos reliable?, should i choose the one nearest to my location?

torrents.... i dont know how to use it, is that like p2p? (i have that pending to learn to use it)

and what u means with alternate cd?
xubuntu, kubuntu....?

---

### Post by mk1w86 on 2010-06-20
There are details on the Alternate CD here:

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

There is also the complete list of mirrors on the same page, usually you would choose the mirror nearest to you but if you are having problems with it choose somewhere else. ;)

---

### Post by Kharlo on 2010-06-20
ok

but has somebody installed ubuntu 10.04 on a smaller than 5gb partition?

---

### Post by mk1w86 on 2010-06-20
I think you could probably manage a normal Ubuntu install on a 5GB partition but you would have very little space left over for further package installation or your files (I have experience of this running Eeebuntu 3.0 on my 4GB Eeepc) so this would not be ideal.

As I said in my earlier post, using the Alternate CD you could do a minimal command line install of Ubuntu (which should be less than 1GB) and then install the individual packages you want.

Is there a particular reason you are limited to 5GB?  You may want to consider a lighter distro.

---

### Post by gmargo on 2010-06-20
> **Kharlo said:**
> but has somebody installed ubuntu 10.04 on a smaller than 5gb partition?

I've only used 3.8GB in my root partition so far.  (Gnome and basic stuff, no KDE yet.)  Don't expect to do a lot of web hosting with 5GB.

If in doubt, you can install in a virtual machine for testing purposes.

For the smallest possible initial install, try the server version.

---

### Post by wojox on 2010-06-20
Try this [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

then you can install anything from there. It is the CLI.

---

### Post by Kharlo on 2010-06-20
i just wanted to install the full ubuntu 10.04 to give it a try untill became stable.
that means, no add software install, and maybe only web browsing.
 
i use (new user,  i have little experience with linux) 8.04 because it's stable, and i wanted to upgrade to 10.04 but because the missing panels issue,  i dont, so i just want to keep a the 10.04 in a s[COLOR=black][FONT=Verdana]eparated [/FONT][/COLOR]small partition just to use it a little.

---

### Post by wojox on 2010-06-20
> **Kharlo said:**
> i just wanted to install the full ubuntu 10.04 to give it a try untill became stable.
that means, no add software install, and maybe only web browsing.
 
i use (new user,  i have little experience with linux) 8.04 because it's stable, and i wanted to upgrade to 10.04 but because the missing panels issue,  i dont, so i just want to keep a the 10.04 in a s[COLOR=black][FONT=Verdana]eparated [/FONT][/COLOR]small partition just to use it a little.


After you install the mini,iso you reboot and run:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by Kharlo on 2010-06-20
sorry....
 
what is minimal!?
i see a 13mb cd image! that is smaller than my puppy linux!

---

