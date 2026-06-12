---
title: "No dialup networking"
date: 2005-12-03
forum: Networking &amp; Wireless
---

### Post by sasafrazzz on 2005-12-03
Hi all, hoping someone can point me in the right direction, did clean install from cd, but i cant seem to connect to internet. I belive i may have a modem driver issue. Currently using conextant HCF soft-v92 modem (as windows xp *shudder* sees it). Any help would be much appreciated, thanks. Oh, btw, am complete newbie with linnux, maybe thats my problem,
Thanks,:D

---

### Post by towsonu2003 on 2005-12-04
first, welcome :)
second, bad start :) u seem to have a winmodem. this is a piece of hardware that looks like a modem but lacks the hardware pieces to be a modem by itself. it uses computer's cpu&memory resources to work correctly, and it is hard to make it work with linux. 

you will need to read, read, read... the best place to start reading is linmodems.org. after reading, download scanModem tool and gunzip and run it on your linux system following the instructions. basically: download and put it in a floppy, flash pen drive, or a cd; transfer it to your linux system, do ```
cp /path/to/your/scanModem.gz ~/Desktop
gunzip scanModem.gz
chmod u+x scanModem
./scanModem
``` gunzip will 'unzip' the file, chmod will make it an executable (an exe file in windows terms), and ./scanModem will run it. scanModem will scan your modem and tell you what it is and how to configure it. It will NOT configure it for you... After running, you will se a number of new folders on your desktop. I think you will find 'read1st.txt' and 'modemdata.txt' in a folder named Modem... start with reading those two very carefully. If you got stuck, look for emailing instructions in scanModem.txt... You will be emailing output to linmodems.org's mailing list. 
good luck.

PS. you now have the opportunity to learn linux while trying to make that thing work. :) be patient and try not to kick your computer :P

---

### Post by sasafrazzz on 2005-12-04
Morning all, and thanks for the info Towsonu2003. Will give it a go. If i get too lost will buy real modem hahaha. Dont worry, never kick my puter (only with windows) thanks again and have a great day :)

---

### Post by az on 2005-12-04
Most software modems have linux drivers that work. Most of them are not open source software, but free as in no charge.

Except your's.


Sorry.  You nave to pay fifteen bucks for a linux driver.

See the gory details at linuxant.com

---

