---
title: "RaLink RT61 driver working on AMD64 3000+ (single core) dapper 6.06.1"
date: 2006-08-22
forum: Networking &amp; Wireless
---

### Post by mrfreddy on 2006-08-22
The latest rt61 beta driver from the serialmonkeys worked with my AMD X2 3800+ with dapper 6.06.1 amd-server but **_not_** for my AMD64 3000+ good ol' single core with Dapper 6.06.01 amd desktop :-k . Issuing the command
```
ifup ra0
```
would fail & any subsequent use of ifconfig or iwconfig would lock the terminal. Following that I could launch gedit or any of the graphical admin tools. Any attempt at restarting would lock at the "deconfiguring network devices" stage & I'd need to press the reset button.

I solved it finally by patching the code from the daily cvs tarball with the patch in a thread on the serialmonkey forums (Note that this patch introduces  a small memory leak, hopefully nothing serious & the code should hopefully be refined & integrated into CVS in the near future. But I was desperate to get any form of connectivity :( You have been warned.)
The thread:
[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=1663]("http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=1663")
The daily cvs build from serial monkey:
[http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz]("http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz")
(The patch itself is an attachment to this reply)

I will presume you have installed kernel headers as per instructions at the beginning of this thread:
[http://www.ubuntuforums.org/showthread.php?t=132980&highlight=rt61]("http://www.ubuntuforums.org/showthread.php?t=132980&highlight=rt61"))
open a terminal, unzip the tarball & copy the patch into the Module directory
```
cd /tmp;gunzip rt61-cvs-daily.tar.gz
cd rt61-cvs-2006XXXXXX/Module
cp /path/to/amd64_patch.txt .
patch -p2 <amd64.patch
```
Note that the directory name is dependant of the date the daily-cvs tarball was packed hence the 2006XXXXXX.
Don't worry if patch reports few errors like this:
```
patch unexpectedly ends in middle of line
patching file rtmp_data.c
patch unexpectedly ends in middle of line
Hunk #1 succeeded at 3822 with fuzz 2.
```
Now just compile & install the binaries in the directories mentioned in this thread:
```
make all
cd $(dirname $(find /lib/modules -name "rt61.ko"))
sudo mv rt61.ko rt61.ko-ORIG
sudo cp /tmp/rtrt61-cvs-2006XXXXXX/Module/rt61.ko .
sudo cp /tmp/rtrt61-cvs-2006XXXXXX/Module/*.bin /etc/Wireless/RT61STA
```

now try removing the old module, inserting the new  & issuing ifup:
```
sudo rmmod -v rt61
sudo modprobe -v rt61
sudo ifconfig ra0 up
```

and the terminal won't lock up & you can use the graphical network configuration tools (hopefully ;) )

Now just set all the other variables with iwconfig as mentioned in the text files in the driver tarball or in the ubuntu forum thread linked above.

---

### Post by Rooy on 2006-11-23
The patch doesn't merge with rt61-cvs-2006112217...
Guess what, it's already there.

Great work, mrfreddy :)

Edit: I use the guide in iwpriv_use.txt and bring ra0 up alright.
Not sure if it works properly though, as there're still WPAPSK/TKIP and DHCP on the way

---

