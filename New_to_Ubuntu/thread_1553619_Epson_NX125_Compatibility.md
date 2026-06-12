---
title: "Epson NX125 Compatibility"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by cyberphrog on 2010-08-15
I'm considering purchasing an Epson Stylus nx125 all-in-one printer.  Does anyone know if it works with Ubuntu?  If yes, what version?  Is it fully functional?

---

### Post by joek1010 on 2010-08-23
I just bought one of these. Getting printing working was pretty easy, just use drivers from here ([http://linux.avasys.jp](http://linux.avasys.jp)). Avasys is mentioned directly on the Epson site, so it seems legit (and it works). They provide debs as well as source. Just install the package, then try installing the printer as normal.

I haven't figured out scanning yet; SANE doesn't find any scanning devices.

---

### Post by danny.woodstock on 2010-09-16
.

---

### Post by danny.woodstock on 2010-09-16
> **joek1010 said:**
> I just bought one of these. Getting printing working was pretty easy, just use drivers from here ([http://linux.avasys.jp](http://linux.avasys.jp)). Avasys is mentioned directly on the Epson site, so it seems legit (and it works). They provide debs as well as source. Just install the package, then try installing the printer as normal.

I haven't figured out scanning yet; SANE doesn't find any scanning devices.

hi...this morning i bought an EPSON Stylus TX 125, so when came home, i started to find some tutorials in the I-net to make this model work on linux,.. i dont use ubuntu, (use debian) but some things are the same in both distributions... so, the printing part, debian recongnized instantly... i configured the printer with the tx stulys 100 that come with cups... and the scanner part??? well thats a difrent story... sane dont recognized... so, i searched for de inet and i found this.
... i visited the web site that you said!  ([http://linux.avasys.jp]("http://linux.avasys.jp/")), and found the perfect driver for the printer part so i changed the tx 100 cups driver and use the one from the web site... becaus i think is better, and this is the good part... in the same web you can look for the scanner driver... look... this is the link for the driver: [http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)
  find something like this:
**Scanner Driver**

                                 **Download for Epson ME 320/330,Epson Stylus NX125/NX127/SX125/TX120/TX121/TX123/TX125/TX129 data package**

and download this pakages: iscan-data_1.3.0-2_all.deb and this  iscan_2.26.0-3_i386.deb

i installed, and have no problem! 
i hope this helps you to use the complete funtions of your epson!... :smile:

ps: your model is nx 125, mine is tx125.. the drivers are the same :smile:
sorry my english, im from chile so i dont speak well. :S
good luck!

---

### Post by nineacres on 2011-03-26
Thanks Danny - that was extremely helpful! And, by the way, don't worry about your English, it's very good. I just wish my Spanish was as good.:D

---

### Post by MyR on 2011-03-26
> **nineacres said:**
> Thanks Danny - that was extremely helpful! And, by the way, don't worry about your English, it's very good. I just wish my Spanish was as good.:D

Do all the functions work perfectly after installing drivers?

---

### Post by nineacres on 2011-03-29
I downloaded the All-In-One multi-functional inkjet driver from here:
[http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/) My SX125 worked fine first time, printing and scanning. The printer scanner output in colour is OK, but could be better ...

---

### Post by ockron on 2011-04-25
**Thank you very much!!**
I followed your instruction and it worked from the get-go!!
:)



> **danny.woodstock said:**
> hi...this morning i bought an EPSON Stylus TX 125, so when came home, i started to find some tutorials in the I-net to make this model work on linux,.. i dont use ubuntu, (use debian) but some things are the same in both distributions... so, the printing part, debian recongnized instantly... i configured the printer with the tx stulys 100 that come with cups... and the scanner part??? well thats a difrent story... sane dont recognized... so, i searched for de inet and i found this.
... i visited the web site that you said!  ([http://linux.avasys.jp]("http://linux.avasys.jp/")), and found the perfect driver for the printer part so i changed the tx 100 cups driver and use the one from the web site... becaus i think is better, and this is the good part... in the same web you can look for the scanner driver... look... this is the link for the driver: [http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)
  find something like this:
**Scanner Driver**

                                 **Download for Epson ME 320/330,Epson Stylus NX125/NX127/SX125/TX120/TX121/TX123/TX125/TX129 data package**

and download this pakages: iscan-data_1.3.0-2_all.deb and this  iscan_2.26.0-3_i386.deb

i installed, and have no problem! 
i hope this helps you to use the complete funtions of your epson!... :smile:

ps: your model is nx 125, mine is tx125.. the drivers are the same :smile:
sorry my english, im from chile so i dont speak well. :S
good luck!

---

### Post by preginald on 2011-07-11
Thanks Danny! You rock. I followed your instructions and it worked just nicely. I have the Epson Stylus NX125 and the scanner works just nicely. 


I went to this page [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do#productinfo](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do#productinfo)
and selected my printer and distribution which took me to the download page.



> **danny.woodstock said:**
> hi...this morning i bought an EPSON Stylus TX 125, so when came home, i started to find some tutorials in the I-net to make this model work on linux,.. i dont use ubuntu, (use debian) but some things are the same in both distributions... so, the printing part, debian recongnized instantly... i configured the printer with the tx stulys 100 that come with cups... and the scanner part??? well thats a difrent story... sane dont recognized... so, i searched for de inet and i found this.
... i visited the web site that you said!  ([http://linux.avasys.jp]("http://linux.avasys.jp/")), and found the perfect driver for the printer part so i changed the tx 100 cups driver and use the one from the web site... becaus i think is better, and this is the good part... in the same web you can look for the scanner driver... look... this is the link for the driver: [http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)
  find something like this:
**Scanner Driver**

                                 **Download for Epson ME 320/330,Epson Stylus NX125/NX127/SX125/TX120/TX121/TX123/TX125/TX129 data package**

and download this pakages: iscan-data_1.3.0-2_all.deb and this  iscan_2.26.0-3_i386.deb

i installed, and have no problem! 
i hope this helps you to use the complete funtions of your epson!... :smile:

ps: your model is nx 125, mine is tx125.. the drivers are the same :smile:
sorry my english, im from chile so i dont speak well. :S
good luck!

---

### Post by Alan.Brown on 2011-09-27
Hi People

I have a similar problem to the OP.   I am using **Ubuntu 11.04** and **Xubuntu 11.04** and my printer is an **Epson Stylus NX125** (as above).

I downloaded the driver file as discussed above and installed it using **Ubuntu Software Centre** - no problems.   Printing with the new driver is good.

However, the system cannot find the Scanner.  I have tried **XSane** and **Simple Scan** but they say "no scanner found".   I have tried rebooting with the printer on and off (then restarting it when the system was going.  How can I force the system to scan for a scanner?

Any suggestions??

TIA

Alan


Sorry People - I had not downloaded the correct drivers for the scanner - all is OK now!!!

---

### Post by steve on 2011-10-18
Wow. For the life of me I can't get this scanner to work. A few questions:

1) Are you guys grabbing the 'ltdl7' version of the .deb? Or are you grabbing the ltdl3 version and installing a backport of ltdl3? (I saw this recommended somewhere.)

2) Are you using the 'iscan' app which comes with the driver, or are you using the driver with something else, like xsane?

3) I'm running 11.10 64-bit with a Stylus NX125. Does anyone have an Epson Stylus NX/TX 125/127 running with this config?

Thanks!

---

### Post by steve on 2011-10-18
I followed these instructions: [http://blog.dale.id.au/archives/862](http://blog.dale.id.au/archives/862)

Modified slightly to look like this:

```

$ sudo usermod -aG scanner your_account
...log out/in...
$ sudo echo '# Epson Stylus NX125' >> /lib/udev/rules.d/40-libsane.rules
$ sudo echo 'ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="085c", ENV{libsane_matched}="yes"' >> /lib/udev/rules.d/40-libsane.rules
$ sudo restart udev

```

...then removed & purged 'iscan' and 'iscan-data'. Then reinstalled iscan/iscan-data. All is well!

So to answer my own questions:

1) Yes, I'm using ltdl7.

2) My first successful scan came from Simple Scan. I'm pretty sure the instructions in the linked blog post are required for proper SANE operation, though.

3) This is still on 11.10 64-bit with an NX125.

Cheers guys. Thanks for the pointers!

---

