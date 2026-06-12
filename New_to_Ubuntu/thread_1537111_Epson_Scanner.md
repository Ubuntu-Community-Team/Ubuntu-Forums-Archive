---
title: "Epson Scanner"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by bigal1932flying on 2010-07-23
Had no luck trying to get my HP scanner to work, so took the plunge and purchased an Epson Perfection V300 Photo Scanner.
Now have the same result as before every program I try says "No device found".
What the hell do I do now?

---

### Post by robert shearer on 2010-07-23
Can you run in the terminal..
```
lsusb
```
with the scanner plugged in and post the output here.

here is the epson propriety driver page that supports your scanner..
[http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)
here are links that may be worth checking...
[https://wiki.ubuntu.com/HardwareSupportComponentsScannersEpson](https://wiki.ubuntu.com/HardwareSupportComponentsScannersEpson)
[http://tuxi.ripabe.net/?p=100](http://tuxi.ripabe.net/?p=100)
[http://ubuntuforums.org/showthread.php?t=1000341](http://ubuntuforums.org/showthread.php?t=1000341)
[http://avasys.jp/eng/linux_driver/](http://avasys.jp/eng/linux_driver/)
[http://avasys.jp/eng/](http://avasys.jp/eng/)

---

### Post by sisco311 on 2010-07-23
It should work with iscan:
[http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)

After installing iscan my Epson all-in-one (dx7400) works with xsane too.

---

### Post by bigal1932flying on 2010-07-23
Response from lusb:
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 04b8:0131 Seiko Epson Corp. 
Bus 001 Device 005: ID 046d:0805 Logitech, Inc. 
Bus 001 Device 004: ID 056a:0011 Wacom Co., Ltd Graphire 2
Bus 001 Device 002: ID 050d:0234 Belkin Components F5U234 USB 2.0 4-Port Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Scanner is plugged into 4-Port Hub.
Thanks.

---

### Post by robert shearer on 2010-07-24
There is the scanner... 	

Bus 001 Device 006: ID 04b8:0131 Seiko Epson Corp.

and there is the hub...
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

so all good.

Now go to..
[http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)

scroll down and select your scanner, then fill out the Questionnaire  and hit next.

in the next window go to "iscan-data_1.0.1-1_all.deb" and download.

if you are using **32 bit** Ubuntu.
then scroll to..
DEB 32bit package [libltdl7] (for Ubuntu 8.10 or later)  	
iscan_2.25.0-1.ltdl7_i386.deb 	
esci-interpreter-gt-f720_0.0.1-2_i386.deb


If using **64 bit** scroll further to 
DEB 64bit package [libltdl7] (for Ubuntu 8.10 or later)  	
iscan_2.25.0-1.ltdl7_amd64.deb 	
esci-interpreter-gt-f720_0.0.1-2_amd64.deb

and download the files for the appropriate one.

now go to your Downloads folder... Places=>Downloads

and find the first file you downloaded and double-click on it.
It should install. If so then in the same folder find the next two files and double click on them one at a time and they will install.

When it is all done then go to Applications=>Graphics=>Image scan! for Linux and you should be good to go.

---

### Post by bigal1932flying on 2010-07-25
Tried to download and install the packages mentioned. After the 2nd. one I receive the message: 
"Error: Dependency is not satisfiable. libltd3(>=1.5.2-2)"
After the 3rd package:
"Error: Dependency is not satisfiable. :isac(>=2.16.1)"
Hope this gives you some clue to what is going on.
Thanks.

---

### Post by robert shearer on 2010-07-26
Just did a bit of googling about those packages as dependencies.
It would appear they refer to Hardy 8.04.
You, presumably, are running a later version of Ubuntu ?

Please check that you downloaded the correct files.
(the first one appears to have installed ok. good !)

you now want **this pair** ..
DEB 32bit package [COLOR="Red"][libltdl7] (for Ubuntu 8.10 or later)[/COLOR]  	
iscan_2.25.0-1.ltdl7_i386.deb 	349,476 bytes
esci-interpreter-gt-f720_0.0.1-2_i386.deb

**not** these....
DEB 32bit package  	
iscan_2.25.0-1_i386.deb 	352,782 bytes
esci-interpreter-gt-f720_0.0.1-2_i386.deb

(They are both on the same page one below the other)

or get the 64bit versions if that is what you are using.

---

### Post by bigal1932flying on 2010-07-26
Tried going through the procedure again and for some crazy reason this time it seems to have worked.
I now have Image Scan and it seems to work, albeit slowly but slow is better than nothing.
Thanks a lot Robert for your assistance.

---

### Post by robert shearer on 2010-07-26
Good to hear. :D

After a reboot try using 'simple scan' or xsane.

sisco311, in post #3 here, said that the install of iscan gave functionality for xsane.

I can't comment as I already had xsane working before installing iscan.

Would be interested to know if either works for you now.

cheers, Bob.

---

