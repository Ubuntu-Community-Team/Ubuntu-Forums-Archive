---
title: "how to undo &amp; redo setup"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by acoluthus on 2008-09-25
hello- still looking for assist on getting hard-modem up  & going, or how to read error messages(see last month of my posts) 
anywhoo, if I did a terminal sequence of the "Wv.." instructions on manually setting up a modem; how do I "undo" a line or series of text-instruction in the Terminal so I can _re-do_ it without fubar'ing the whole thing?
Basically, I'd like to undo & redo a function that was done in Terminal so an external modem can run.
I tried to follow/use: [http://alumnit.ca/wiki/index.php?page=WvDialFAQ](http://alumnit.ca/wiki/index.php?page=WvDialFAQ)
and need to undo/redo.
I've also tried the little red-phone logo'd GnomePPP and that has errors too; ultimately, not connecting. 
help? (please instruct as basic as possible since I -really- don't "get" ubuntu and am still timid to run anything in Terminal)
Thank you,

AC

---

### Post by willca on 2008-09-25
If you are referring to wvdial.conf file that you did all these commands...then all you have to do is delete everything in there or rename it.

If you want to just delete the contents.

sudo >/path/wvdial.conf

Or just rename it
sudo mv /path/wvdial.conf /path/wvdial.conf.old

I assume your /path is actually /etc. Hence the sudo.

---

### Post by acoluthus on 2008-10-14
I tried exactly what you had (with without "sudo" whatever that is)
and it says file not found.

---

### Post by acoluthus on 2008-11-02
I've since reloaded Heron and now have no internet access.
any assistance would be appreciated whether to setup the Trendnet 560 linux-friendly external modem or to get understanding on setting up and even switching between the RJ45 cable-from-router-from-cable-internet modem and an external dialup modem.
links, suggestions, etc would be greatly appreciated

---

### Post by acoluthus on 2008-11-08
bump..?
-is it ok to leave a message for the last person who recommended something and if it didn't turn out quite as they'd anticipated?
I'll check the courtesy info...?

---

