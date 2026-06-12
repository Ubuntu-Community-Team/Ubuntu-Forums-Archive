---
title: "Gettin ADSL BIPAC 7000 modem working"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by santam on 2006-12-30
Hi everybody,
I installed Ubuntu Linux today and while everything else is working fine I am unable to connect to the net using my ADSL BIPAC 7000 USB modem. I went through the forum and went through the links provided in google. I have understood a bit about the process - 
1. I have to get a source code cxacru-fw.c from the net - which I have downloaded from the URL  [http://revu.tauware.de/details.py?upid=2426](http://revu.tauware.de/details.py?upid=2426) . 
2. Step 2 is where I am stuck - how to compile the source code - I am a complete noob at this and would like to have some one help me with the code I will have to type for the process.  In this respect I would like to add that since this is the only connection to the net I have, I have to keep logging in and out of Ubuntu to enter Win XP where I can access the net. 

I have copied the files provided at the site including the cxacru-fw.c in a new folder in the desktop which I named as "new". I have also obtained the firmware from the windows installation CD. 

While the site where I got the information mentions that the details of how to compile this source code are in the URL - but the URL given no longer works. 
I would be very grateful for any help at all.

---

### Post by Monkey Tennis on 2007-01-19
If your still having problems with the Bipac 7000 let me know.  I can help out.  Its straight forward.

Thanks

---

### Post by santam on 2007-01-19
Hi thanks for the reply. I finally got my modem's working but still cant connect to the net so I am still lost. I dont know I may have done something wrong so it would be great if you could help me through the steps. However I have only one computer so it is really bugging when you have to boot in and out just to access the net. 
:)

---

### Post by Monkey Tennis on 2007-01-21
Hi, this is quite simple but first of all can you confirm that you have put CnxE2Fw.bin in your drivers folder.  Basicly I'm asking if you if your modem syncs when you disconnect it and re-connect it after ubuntu has loaded?  This will tell me if you have installed the driver properly.  once I know this is done the next stage is as easy as.

---

### Post by Monkey Tennis on 2007-01-21
I'm in work at the moment so I thought I would quickly knock the next bit up for you.

1.  Download and install this package.  Once you have downloaded it from the link, burn it to a cd and boot up Ubuntu.

[http://dir.filewatcher.com/d/Debian/arm/net/br2684ctl_20040226-1_arm.deb.7332.html](http://dir.filewatcher.com/d/Debian/arm/net/br2684ctl_20040226-1_arm.deb.7332.html).

2.  In ubuntu open a terminal and switch to root (type "su" and enter password).  Then type "dsl-setup".  follow the instructions very carefully as changing this later is a pain.  it will ask you for user name and password for your isp provder.  It will also ask you for the device you use to connect.  I think it defaults to eth0 make sure you type nas0 (very important.

3.  Still in terminal issue this command "br2684ctl -b -c 0 -a 0.35".  This will tell you that a device "nas0" has been configured.

4.  Issue this command in teminal "pon dsl-provider"

Like I said this is off the top of my head as I'm in work but it should work. Let me know how you do.

---

### Post by santam on 2007-01-30
Sorry for not replying earlier but I had to go for a conference. I tried out your solution as soon as I came back to find to my horror that my modem was no longer working. Undaunted I went through a full format and reinstall of the OS and again tried to install the modem driver. Sadly this time even that was not possible. :confused: 
Here is what I did:
I had already downloaded the tar.gz file (cxacrufw_1.2.orig.tar.gz) from the Sourceforge repository and burned it on a CD.
After booting into Ubuntu I first copied the tar.gz file into my desktop and then opened the terminal window. In it I went to desktop using the cd command and displayed the tar.gz file using the ls command.
Then I unpacked the tarball with the tar xvjf command and another folder appeared in the desktop named cxacrufw-1.2.orig.
Using the cd command I went into the newly created directory where 4 files were listed:
1. COPYING
2. README
3. Makefile
4. cxacru-fw.8.gz
While in the same directory I typed  ./configure command. It immediately stated no such command. I tried combinations like .\configure , configure etc but none worked.
Undaunted I went to the next step thinking since the makefile exists probably the make command will work. When I issued the make command (typed make) no cxacru-fw.8.bin appeared as it should have. I have the entire output of the error that the command generated with me and I will be appending it towards the end of the letter.
I really appreciate the interest you have shown in my problem and I would be really thankful for some help on this one.
------------------------------
Error that appeared after the make command was issued

[email]santam@santam:~/Desktop/cxacrufw-1.2.orig[/email]$ sudo make
cc     cxacru-fw.c   -o cxacru-fw
cxacru-fw.c:24:19: error: stdio.h: No such file or directory
cxacru-fw.c:25:19: error: fcntl.h: No such file or directory
cxacru-fw.c:26:20: error: unistd.h: No such file or directory
cxacru-fw.c:27:19: error: error.h: No such file or directory
cxacru-fw.c:28:18: error: argp.h: No such file or directory
cxacru-fw.c:29:20: error: stdint.h: No such file or directory
cxacru-fw.c:30:22: error: sys/stat.h: No such file or directory
cxacru-fw.c:31:22: error: sys/mman.h: No such file or directory
cxacru-fw.c:32:20: error: endian.h: No such file or directory
cxacru-fw.c:33:22: error: byteswap.h: No such file or directory
cxacru-fw.c:36: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘le16_to_cpup’
cxacru-fw.c:37: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘le32_to_cpup’
cxacru-fw.c:43: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
cxacru-fw.c:140: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘parse_opts’
cxacru-fw.c:168: error: variable ‘argp’ has initializer but incomplete type
cxacru-fw.c:168: warning: excess elements in struct initializer
cxacru-fw.c:168: warning: (near initialization for ‘argp’)
cxacru-fw.c:168: error: ‘parse_opts’ undeclared here (not in a function)
cxacru-fw.c:168: warning: excess elements in struct initializer
cxacru-fw.c:168: warning: (near initialization for ‘argp’)
cxacru-fw.c:168: warning: excess elements in struct initializer
cxacru-fw.c:168: warning: (near initialization for ‘argp’)
cxacru-fw.c:168: warning: excess elements in struct initializer
cxacru-fw.c:168: warning: (near initialization for ‘argp’)
cxacru-fw.c: In function ‘main’:
cxacru-fw.c:174: error: storage size of ‘instat’ isn’t known
cxacru-fw.c:175: error: ‘uint8_t’ undeclared (first use in this function)
cxacru-fw.c:175: error: (Each undeclared identifier is reported only once
cxacru-fw.c:175: error: for each function it appears in.)
cxacru-fw.c:175: error: ‘buf’ undeclared (first use in this function)
cxacru-fw.c:175: error: ‘fw’ undeclared (first use in this function)
cxacru-fw.c:178: error: ‘NULL’ undeclared (first use in this function)
cxacru-fw.c:180: error: ‘O_RDONLY’ undeclared (first use in this function)
cxacru-fw.c:182: error: ‘errno’ undeclared (first use in this function)
cxacru-fw.c:189: error: ‘PROT_READ’ undeclared (first use in this function)
cxacru-fw.c:189: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
cxacru-fw.c:198: error: ‘O_WRONLY’ undeclared (first use in this function)
cxacru-fw.c:198: error: ‘O_CREAT’ undeclared (first use in this function)
cxacru-fw.c:198: error: ‘O_EXCL’ undeclared (first use in this function)
cxacru-fw.c:199: error: ‘S_IRUSR’ undeclared (first use in this function)
cxacru-fw.c:199: error: ‘S_IWUSR’ undeclared (first use in this function)
cxacru-fw.c:199: error: ‘S_IRGRP’ undeclared (first use in this function)
cxacru-fw.c:199: error: ‘S_IWGRP’ undeclared (first use in this function)
cxacru-fw.c:199: error: ‘S_IROTH’ undeclared (first use in this function)
cxacru-fw.c:199: error: ‘S_IWOTH’ undeclared (first use in this function)
cxacru-fw.c:208: warning: incompatible implicit declaration of built-in function ‘printf’

---

### Post by Monkey Tennis on 2007-01-30
Hi mate.

The easiest thing to do is to download the modem driver that has already been compiled so you don’t have to mess around trying to extract the windows one.  

[http://www.rsw.sk/linux/adsl/cxacru-fw-2.099.063.000.tar.gz](http://www.rsw.sk/linux/adsl/cxacru-fw-2.099.063.000.tar.gz)

Extract the file to your desktop and then issue this command in terminal

sudo cp /Desktop/cxacru-fw.bin /lib/firmware/cxacru-fw.bin

This will copy the driver into your driver folder.

To test it has worked all you need to do is disconnect the modem and re-connect it.  It should sync.  It does sometimes take about 30secs to start the process so if it doesn’t happen straight away don’t panic.

You should never have to re-install the os it’s very stable and also it’s quite hard to mess it up.  I dual boot and have found if you boot windows first and then re-start and boot UBUNTU the modem appears to still be syncronised, this is not the case as the windows driver is still loaded in the modem and will not work in Linux.

See how you go.

---

### Post by santam on 2007-01-31
Thanks that worked almost immediately. :D 
Now I am trying to get on the net using the instructions you have already given - lets see how that works out
Thanks for the help
Santam

---

### Post by Monkey Tennis on 2007-01-31
Thats good to hear.  Let me know if you it all works.

Thanks

---

