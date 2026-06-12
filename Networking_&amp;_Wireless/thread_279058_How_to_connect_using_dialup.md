---
title: "How to connect using dialup"
date: 2006-10-17
forum: Networking &amp; Wireless
---

### Post by xybermaster on 2006-10-17
My modem and everything is installed properly. All I need to know is the steps to connect using a dialup connection. Thats it and only that. If you can go in details that would be great. I am new to linux so please stick to the topic. Thanks in advance.

---

### Post by adwait on 2006-10-17
Open up a terminal and type gppp. The rest is GUI based and pretty easy. If it says "Command no found", you need to install it with
```
sudo apt-geti install gppp
```

This too is typed in the terminal. The terminal can be found somewhere in the menu (don't quite remember exactly where.)

---

### Post by antmenj on 2006-10-18
> **adwait said:**
> Open up a terminal and type gppp. The rest is GUI based and pretty easy. If it says "Command no found", you need to install it with
```
sudo apt-geti install gppp
```

This too is typed in the terminal. The terminal can be found somewhere in the menu (don't quite remember exactly where.)

My first post here.  I think I may have the same issue.  Almost brand new to linux so please keep that in mind.

I opened the terminal found at Applications> Accessories> Terminal and tryed:

gppp  I got
Bash: gppp: command not found

Next I tryed:

sudo apt-geti install gppp   and got
sudo apt-geti: command not found

geti looked a little like a typo so I tryed:

sudo apt-get install gppp  and got
Reading package lists... Done
E: Couldn't find package gppp

Then I thought my be I need the ubuntu cd in the drive.  I put it in and tryed:

sudo apt-get install gppp    and got
Reading package list... Done
Building dependancy tree... Done
E: Couldn't find package gppp

](*,) 
A few questions.
Where should this gppp be found? On the ubuntu disc, on the HDD ubuntu install, or on the internet?  If the internet how should I transfer it to the ubuntu machine given we are trying to establish an internet conection and don't have one on this machine as yet.  Can I burn it on a disc with windows and transfer it?

Is it a case of plug and play as far as external modems go?

What should be done next?

Am using Ubuntu 6.06 LTS and have an external modem conected to COM1.  There is nothing stoping me using com2 if preferable.

---

### Post by antmenj on 2006-10-18
Well I got conected but not that way:-D .

Open Applications> Accesories> Terminal

type sudo pppconfig

fill it all in

use pon the dial and poff to hang up8)

---

### Post by adwait on 2006-10-18
Yeah thats the CLI way to do it.....I thought you were guys to new to Linux and would want a GUI way :)

---

### Post by DougieFresh4U on 2006-10-18
I did the pppconfig thing and answered all ?? So now when I want to connect is there some thing some where I am supposed to click or do I just open firefox and it connects?

---

### Post by antmenj on 2006-10-19
> **adwait said:**
> Yeah thats the CLI way to do it.....I thought you were guys to new to Linux and would want a GUI way :)

Yes that would be nice still.

Well I did do a lot of hunting prior to posting that but never got it *quite* right](*,) but almost.  Then I thought I'd give it another go and wala8) .

If you got the pppconfig thing to work you need to open the same terminal and type pon to dial and open the terminal and type poff to hang up.  Unlike windows my modem made no sound when dialing.

Is there a way to make something like a desktop icon that runs a "pon" *batch file *or what ever the linux term for that type of file is?

---

### Post by towsonu2003 on 2006-10-19
You might wanna use wvdial if you're having any problems dialing up. see [https://help.ubuntu.com/community/DialupModemHowto#head-8f5dfcf07a408945df0dcd5a4eed9d5a8d20dacb](https://help.ubuntu.com/community/DialupModemHowto#head-8f5dfcf07a408945df0dcd5a4eed9d5a8d20dacb)

---

