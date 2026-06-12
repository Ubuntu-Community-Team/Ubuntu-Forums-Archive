---
title: "Modem Driver Installation Problems"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by blanky on 2006-11-18
Hey guys, I recently received Ubuntu 6.10 from a friend who was nice enough to download it for me. I have used Ubuntu before but back then I had DSL (*Yes, I went backwards :'(*). I lost my DSL due to certain problems, so I went ahead and got 56k Temporarily. I have AOL for now (*Yep, even worse*). But that's not really the problem. You see, I have a modem, **HUMMINGBIRD Fax Modem 56k/V.92**, PCI/Internal. Anyways, I got it because I saw that it 'supported' Linux; it was the first thing I ever bought which said actually said it supported Linux right on the box.

I went ahead and copied the drivers from the CD to my home directory. The 'drivers' were in a folder called **Linux** on the CD, and the folder contained two files; a **.patch** file and a **.tar** file which contained the actual source and make files for the modem drivers. I ignored the patch because I didn't really understand it or how to use it (*I opened it in a text editor, it doesn't seem like anything important, but I could be wrong*). I **tar**'d up those files and they are available [here]("http://www.jorgepena.be/downloads/linux/modem.tar").

I went ahead and extracted the archive and tried to **make** the drivers, it didn't work, after about 30 minutes of fiddling around with compiler flags I did the obvious and added **CC:=gcc-3.4** in all of the Makefiles in each folder, so that each Makefile would use that version, and all seemed to work. However, when I went ahead and tried **sudo make install**, I got errors. For (*hopefully*) ease of reading, I pasted the output [here]("http://paste.jorgepena.be/34"), from both the make/compilation process (*Which supposedly worked*) and the make install process (*Which is where my problem is at*).

I was just wondering if you guys would be kind enough to help me out, because otherwise it's pretty pointless for me to use without any form of connection to the internet.

**Note**: The archive contains a README file which I read, and unless I missed something, I did everything correctly, (*I did the gcc-3.4 on my own account however, because I read about it at [this]("https://wiki.ubuntu.com/DialupModemHowto") ubuntu wiki page*). It says that some distributions require the **KERNEL_DIR** value to be modified, but I left mine at the default, **/lib/modules/$(shell uname -r)/build**.

Sorry for the long post, I just tried to show as much information as I could so that it could hopefully be easier to diagnose this problem. I've already spent a lot of time trying to figure it out myself, but I'm not much of a Linux expert myself.

Thanks for any help, I really appreciate it.

---

### Post by blanky on 2006-11-18
It seems like this forum gets many threads and not as many replies heh, I hope someone can please help me, sorry for the bump.

---

### Post by blanky on 2006-11-19
Did I do something wrong? Did I give too much information? Haha.

---

