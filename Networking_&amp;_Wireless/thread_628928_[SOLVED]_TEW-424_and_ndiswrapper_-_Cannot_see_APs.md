---
title: "[SOLVED] TEW-424 and ndiswrapper - Cannot see APs"
date: 2007-12-01
forum: Networking &amp; Wireless
---

### Post by victorbrca on 2007-12-01
Hi all,


  I've spent the whole afternoon trying to get this working. I have a trendnet TEW-424 on my daughter PC. I installed Edubuntu a while ago and want to get her Internet working.

  I've installed 2 different drivers using ndiswrapper, and none of them seem to work (or I'm doing something wrong).

  I also blacklisted "bcm43xx".

  Here are some results from commands, hoping someone can lend a hand:

```
$ lsusb
Bus 002 Device 002: ID 0457:0163 Silicon Integrated Systems Corp.
```

```
$ ndiswrapper -l
sis163u : driver installed
        device (0457:0163) present
```

```
$ lshw -C network
WARNING: you should run this program as super-user.
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:18:e7:02:6c:16
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+sis163u driverversion=1.45+Silicon Integrated Systems multicast=yes wireless=IEEE 802.11g
```

```
$ sudo iwlist wlan0 scan
wlan0     No scan results
```

```
$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results
```


  Also, I don't see how to enable roaming mode on network-manager. And it only allows encruption... :-S

[IMG]http://wazem.dyndns.org/temp/ubuntu-forum/luana-wifi/Network-Settings.png[/IMG]

[IMG]http://wazem.dyndns.org/temp/ubuntu-forum/luana-wifi/wlan0-Properties.png[/IMG]


Thanks,

Vic.

---

### Post by victorbrca on 2007-12-01
I rebooted the machine into XP, my daughter was playing around for a bit. After a while I rebooted it into Edubuntu, tried to scan for APs on shell and it gave me a result. 

Went to network-manager and noticed that roaming was enabled again. Did:

```
sudo iwconfig wlan0 <ESSID>
sudo dhclient wlan0
```

And it got an IP from a open SSID. Went to network manager and changed from roaming to WPA Personal. Ran dhclient again and it worked...  :S

Not sure what happened here, but after spending almost a full day I'm happy that it's working.


Vic.

---

### Post by Kansasguy on 2007-12-11
Hi there Victor,  I just loaded Ubuntu 7.10 (think it's gutsy gibbon) on an old PC 600mgh with 256k memory.  It used to have XP and the Trendnet 424UB and tied into my network well.  I'm brand new to Linux, and don't know where to put commands, or how to load ndiswrapper.  I have the disc that came with the 424UB, does it have the drivers.  Any help would be appreciated.  Other computers on the network are a PC with XP, wired to Trendnets TEW632BRP, and a laptop, with XP, that has it's own card.  Thanks,  ht in cold Kansas

---

### Post by victorbrca on 2007-12-11
Hey Kansasguy, 

  This will require a big how to. I'll write as much as I can when I have a chance. Let me know if you have any problem.

  First you need to download the drivers SiS163u.sys and sis163u.inf. You can find them on google, or install the CD on XP, them look for sis163u.inf at "C:\Windows\inf\". You have to search the whole C:\ to find SiS163u.sys. Copy and paste them on you home folder on Ubuntu (Places => Home folder).

  Now open a terminal (Applications => Accessories => Terminal), and type the following to install ndiswrapper:

```
mkdir downloads
cd downloads
wget http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.50.tar.gz
tar -xzvf ndiswrapper-1.50.tar.gz
cd ndiswrapper-1.50
make distclean
make
sudo make install
```

  On the same terminal (install the driver with ndiswrapper):

```
cd ~/
ndiswrapper -i sis163u.inf
```

   If no error where shown run:

```
depmod -a
```

   Again If no error where shown (load ndiswrapper as a module):

```
modprobe ndiswrapper
```

  Them check if the driver is being used by device. Plug in the device and run:

```
ndiswrapper -l
```

  The result should be:

> sis163u : driver installed
        device (0457:0163) present

Let me know how far you get...


Vic.

---

### Post by Kansasguy on 2007-12-12
Thanks so much Vic,  I'm at work but have tomorrow off.  Today is so slow here in Kansas due to the ice storm that I have had an opportunity to learn about the command shell, so will try some of this tonight or tomorrow.  ht

---

### Post by Kansasguy on 2007-12-13
On the Trendnet disc, I found these in the "driver" file, in the WinXP folder

Rtl8178b.sys and Net8178b.inf

*******
On my Windows XP Home disc, version 2000, SP1, I found, in the i386 folder:

sis6306.IN_
sis3001_IN_
sis6326.IN_

but not sis163u.sys or sis163u.inf

*****

if I make a mistake in the "Terminal", do I have to go back and "clear" it?

******
Found this at 
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/)

Card: RTL8187B integrated in the laptop Gateway ML6720

    *
      Chipset: RTL8187B
    *
      USB Bus ID: 0BDA:8189
    *
      Driver: Win98
    *
      from: [ftp://202.65.194.212/cn/wlan/RTL8187B_driver_only.zip](ftp://202.65.194.212/cn/wlan/RTL8187B_driver_only.zip)
    *
      Other: Using ndiswrapper driver version 1.49, SUSE10.3 with kernel 2.6.22-9
    *
      Other: XP driver does not work - just see access points, no connect

******
I see some places  AMD64 and i386, as if I have a choice, or do I need both?

*********
got all sorts of errors first time, including the first one, can't make downloads file, already exists
****
I think the biggest problem is not having the sis163 etc,  see it talked a lot about on the net, but can't find where to download it

thanks for all the help,   ht

---

### Post by Kansasguy on 2007-12-13
(Other problem is I shouldn't have made this the very first thing I do on Linux/Ubuntu on an unwired older computer,   arrrgggghhh)

---

### Post by victorbrca on 2007-12-13
Hi Kansasguy,

  The first thing I'd have to ask is, what CD are you looking into and what card are you trying to install?

  My instructions were for Trendnet TEW-424. Let me know...


Vic.

---

### Post by Kansasguy on 2007-12-13
On the Trendnet 424 cd, there is a "driver" folder.  In it are 4 folders, Win98, WinMe, Win2000, WinXP.  The Win98 and WinMe folders each have in them:
                   net8187b.inf     12 KB Setup Information and
                   RTL8187B.sys     201 KB System file
The Win2000 and WinXP folders have the same files (with the .inf having 12 KB and the .sys having 185 KB), and also have
                   net8187B.cat      11 KB  Security Catalog

Nothing anywhere that looks like a sis......

***
I've tried to copy and paste my results in the Terminal to the word processor that I have been able to use (via a flash drive hooked up to this XP laptop that is online) but it won't paste, so I can't send you the results.  

first or second time I did it I saw an error re:  mkdir downloads that said file (or folder) already existed, and indeed there was another download folder IN the download folder.  Deleted both of them to the trash and got past that error

now the first error I see comes after .....sourceforge.... (where ndiswrapper came from I think)  "name or service not known"

Have also tried deleting both the sis..  files (inf and sys) that I down loaded, and replace them with the ones listed above in this post  (net8187 and rtl8187), but don't think I have the right ndiswrapper yet (in the home folder)   Thanks again for the help   ht

---

### Post by Kansasguy on 2007-12-13
Oh, I see a problem, I think.      In the commands you sent, there is:

wget [http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.50.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.50.tar.gz)
tar -xzvf ndiswrapper-1.50.tar.gz

does this mean that the thing goes online to http......sourceforge.....   etc.   
This computer is not online, because I am trying to hook it up by the 424UB.  I did put ndiswrapper in my home folder via a flash drive, so (if being offline is the problem) can we change the command so that it reads it from the home folder instead of looking for it online?       ht

---

### Post by victorbrca on 2007-12-13
Hi Kansasguy,


  This have to be done on the same order as I posted.

  1- First download this files on your home folder (right click, save link as):

[http://e-danek.info/shared/SiS163u.sys](http://e-danek.info/shared/SiS163u.sys)
[http://e-danek.info/shared/sis163u.inf](http://e-danek.info/shared/sis163u.inf)

  2- Create a folder called downloads inside your home folder and download this into it (right click, save link as):

[http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.50.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.50.tar.gz)


  Let me know when you get this done and I'll give the next instructions.  :)


Vic.

---

### Post by Kansasguy on 2007-12-13
That's done

---

### Post by victorbrca on 2007-12-13
Cool.... 

We are going to run some codes on your terminal now. If one of the steps doesn't work, please stop, do not proceed. I will also need the error message. 

If you save it on OpenOffice as .html you will for sure be able to open in Windows (Applications => Office => OpenOffice Word Processor).

Now open a terminal window and do the following commands.

This will decompress the ndiswrapper installer:
```
cd downloads
tar -xzvf ndiswrapper-1.50.tar.gz
```

This will install the ndiswrapper:
```
cd ndiswrapper-1.50
make distclean
make
sudo make install
```

Let me know how it goes!! 

Vic.

---

### Post by Kansasguy on 2007-12-13
When I clicked on the second of the two links in your former post, the .sys link did what it was supposed to, but the .inf one just opened up. Try it from the post and you will see what I mean.  I (who knows little) think that might be the problem

if emailing would be faster,   I'm at      htate@sunflower  dot  com

what came up after the first command follows:    


   

gzip: stdin: not in gzip format

tar: Child returned status 1

tar: Error exit delayed from previous errors

htate@htate-desktop:~/downloads$

---

### Post by victorbrca on 2007-12-13
Try right clicking on the file and select "Save link as". That should resolve it.

Paste the result of the following for me:

```
cd downloads
ls -la
```



Vic.

---

### Post by Kansasguy on 2007-12-13
that worked, I'll go try it,  be back soon
was just checking around,  is it xzvf     or zxvf       ndiswrapper?    Googled both, they are both there

---

### Post by victorbrca on 2007-12-14
They are the same. It's just different order:

- tar - Similar to winzip and winrar
  . x - extract
  . z - file is compressed
  . v - verbose - gives confirmation in the screen
  . f - indicating that it's a file


  Tar is a command. You can get more info on commands by typing "man <name of command>" in a terminal window. Type "q" to get out.

EG:

```
man tar
```

or

```
man date
```



Vic.

---

### Post by Kansasguy on 2007-12-14
Paste the result of the following for me:


Code:
---------
cd downloads
ls -la
---------
htate@htate-desktop:~$ cd downloads

htate@htate-desktop:~/downloads$ tar -xzvf ndiswrapper-1.50.tar.gz



gzip: stdin: not in gzip format

tar: Child returned status 1

tar: Error exit delayed from previous errors

htate@htate-desktop:~/downloads$ ls -la

total 32

drwxr-xr-x  2 htate htate  4096 2007-12-13 21:09 .

drwxr-xr-x 28 htate htate  4096 2007-12-13 22:49 ..

-rwx------  1 htate htate 21000 2007-12-13 20:35 ndiswrapper-1.50.tar.gz

htate@htate-desktop:~/downloads$

---

### Post by Kansasguy on 2007-12-14
found these links, and am trying to figure out the problem;

[http://www.linuxquestions.org/questions/linux-newbie-8/tar-error-child-returned-status-1-208083/](http://www.linuxquestions.org/questions/linux-newbie-8/tar-error-child-returned-status-1-208083/)

[http://www.linuxforums.org/forum/installation/11297-not-gzip-format.html](http://www.linuxforums.org/forum/installation/11297-not-gzip-format.html)

?????????????   Good night

---

### Post by victorbrca on 2007-12-14
Nice that you are doing some homework!!!  :)  That's the key to learn Linux... 

Try this one:

```
cd downloads
file ndiswrapper-1.50.tar.gz
```


Vic.

---

### Post by Kansasguy on 2007-12-14
htate@htate-desktop:~$

htate@htate-desktop:~$ cd downloads

htate@htate-desktop:~/downloads$ file ndiswrapper-1.50.tar.gz

ndiswrapper-1.50.tar.gz: HTML document text

htate@htate-desktop:~/downloads$ 


got the above, ht

---

### Post by victorbrca on 2007-12-14
Ok, try downloading it again, right click on the file (ndiswrapper-1.50.tar.gz) and select properties. It should show aprox. 193.7 KB. Once it does go to a terminal window and type:

```
cd downloads
fle ndiswrapper-1.50.tar.gz
```

The result should be:

> $ file ndiswrapper-1.50.tar.gz 
ndiswrapper-1.50.tar.gz: gzip compressed data, from Unix, last modified: Wed Nov 28 01:23:30 2007

If it shows that, them run:

```
tar -xzvf ndiswrapper-1.50.tar.gz
cd ndiswrapper-1.50
make distclean
make
sudo make install
```


Vic.

---

### Post by Kansasguy on 2007-12-14
Did exactly what you said it would this time (I made a folder in my home folder and put the other ndis... in it, instead of deleting it, figured we wouldn't need it).  The whole mess ended with:



loadndisdriver.c:515: warning: implicit declaration of function ‘strncmp’
loadndisdriver.c:517: warning: implicit declaration of function ‘printf’
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function ‘printf’
loadndisdriver.c:527: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:542: warning: implicit declaration of function ‘atof’
loadndisdriver.c:549: warning: implicit declaration of function ‘strcmp’
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:590: warning: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/htate/downloads/ndiswrapper-1.50/utils'
make: *** [install] Error 2
htate@htate-desktop:~/downloads/ndiswrapper-1.50$ 

ht

---

### Post by victorbrca on 2007-12-14
ok... Have you done any modification to your repositories? if not it would be a good thing to do as some softwares won't be available with normal repositories.

You can get more info for that [here.]("http://www.psychocats.net/ubuntu/sources")

For now, try the following (put your password when it prompts):

```
sudo apt-get install build-essentials
```

If it installs ok try again:

```
cd downloads/ndiswrapper-1.50
make distclean
make
sudo make install
```


Vic.

---

### Post by Kansasguy on 2007-12-14
will get back to it tomorrow, wife wants to watch a movie.  Will do as you said.  Was the last one successful?   Til tomorrow,  thanks   (don't think I have changed any repositories)

---

### Post by victorbrca on 2007-12-14
Download was good and unziping as well. We could no compile the program as you don't have the necessary tools in the system, hence why I asked you to install build-essentials.

More homework... ;)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

[http://monkeyblog.org/ubuntu/installing/#installing_with_terminal](http://monkeyblog.org/ubuntu/installing/#installing_with_terminal)

Have fun!!!

Vic.

---

### Post by Kansasguy on 2007-12-15
Studied a lot.  loaded a lot of packages thru Synaptics, including ndiswrapper common, and ndiswrapper utils 1.9 (both 1.43-lubuntu2) via CD     (and loaded some MP3 music, and imported it into Rythmbox music player, but found the message “Gstreamer plugins to decode MP3 files could not be found) 

then went back thru the commands you gave me and got to “make disclean”, and it said something like,  unable to find that command, or something like that.  BUT, (seeming to skip altogether the  “make distclean” and the “make”) I went thru it again, and  wherever I was, I noticed that the last thing it said was  “sudo make install”

SO, I just hit enter, and it ended up with:

install -D -m 755 loadndisdriver /sbin/loadndisdriver
install -D -m 755 ndiswrapper /usr/sbin/ndiswrapper
install -D -m 755 ndiswrapper-buginfo /usr/sbin/ndiswrapper-buginfo

NOTE: Windows driver configuration file format has changed since 1.5. You must re-install Windows drivers if they were installed before.
make[1]: Leaving directory `/home/htate/downloads/ndiswrapper-1.50/utils'
mkdir -p -m 0755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8
htate@htate-desktop:~/downloads/ndiswrapper-1.50$ 

Seems like I'm getting closer,   ht

---

### Post by victorbrca on 2007-12-16
k... what does the output of this command shows?

```
which ndiswrapper
```


Vic.

---

### Post by Kansasguy on 2007-12-16
NOTE: Windows driver configuration file format has changed since 1.5. You must re-install Windows drivers if they were installed before.
make[1]: Leaving directory `/home/htate/downloads/ndiswrapper-1.50/utils'
mkdir -p -m 0755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8
htate@htate-desktop:~/downloads/ndiswrapper-1.50$ which ndiswrapper
/usr/sbin/ndiswrapper
htate@htate-desktop:~/downloads/ndiswrapper-1.50$

---

### Post by victorbrca on 2007-12-16
Cool... now run this:

```
cd ~/
ndiswrapper -i sis163u.inf
```


Vic.

---

### Post by Kansasguy on 2007-12-17
htate@htate-desktop:~$ ndiswrapper -i sis163u.inf

couldn't create /etc/ndiswrapper/sis163u: Permission denied at /usr/sbin/ndiswrapper line 194.

htate@htate-desktop:~$

---

### Post by victorbrca on 2007-12-17
try

```
cd ~/
sudo ndiswrapper -i sis163u.inf
```

Vic.

---

### Post by Kansasguy on 2007-12-17
worked ( I think) . Would the next be

cd ~/
sudo ndiswrapper -i sis163u.sys

?
and does the "-i" mean "install"?

---

### Post by victorbrca on 2007-12-17
Good guess, but no... lol. When you ran "ndiswrapper -i sis163u.inf" it also installed the sys file.

And yes, -i in ndiswrapper means install. If you look at the man page for the ndiswrapper you'll see the option:

```
man ndiswrapper
NAME

ndiswrapper - Linux kernel module and user space tool to load and run Windows XP drivers for wireless cards
SYNOPSIS

ndiswrapper
DESCRIPTION

ndiswrapper is two parts: user space tool that is used to install Windows XP drivers and kernel module to load the Windows XP drivers. Both are called ndiswrapper.

ndiswrapper - tool

The user space tool (/usr/sbin/ndiswrapper) is used whenever a new Windows XP driver is to be installed. This program takes the following options:

OPTIONS

-i <inf file>
    installs new Windows XP driver, where <inf file> is full path to INF file for that driver. 
-l
    lists the currently installed drivers. 
-e <driver>
    removes an installed Windows XP driver named <driver>. 
-m
    writes an alias for wlan0 (default wireless device) into module configuration file so that ndiswrapper kernel module is loaded automatically when this interface is used. 
```

The next step is to check if it installed. Run (l as in LIMA):

```
ndiswrapper -l
```



Vic.

---

### Post by Kansasguy on 2007-12-17
says
sis163u : driver installed

gonna guess again,  put the wireless device in and see if it recognizes it (probably something else first)

(hmmm, certainly don't want to  run -e,   but maybe -m,  ????)

gracia otra vez por todo su ayuda

---

### Post by victorbrca on 2007-12-17
lol... no problem.... 

K, I don't want to discourage you, but the easy part is done...  :)

Next step is, put the device and run "ndiswrapper -l" again. Let me know what the 2x lines that will come up says...

Vic.

---

### Post by Kansasguy on 2007-12-17
installed device,       
entered ndiswrapper -l  (Lima)
got:

sis163u : driver installed
htate@htate-desktop:~$

---

### Post by victorbrca on 2007-12-17
K, how about this command:

```
lshw -C network
```

Vic.

---

### Post by Kansasguy on 2007-12-17
tate@htate-desktop:~$ lshw -C network

WARNING: you should run this program as super-user.

  *-network               
       description: Ethernet interface
       product: 3c905 100BaseTX [Boomerang]
       vendor: 3Com Corporation
       physical id: d
       bus info: pci@0000:01:0d.0
       logical name: eth0
       version: 00
       serial: 00:10:4b:2b:20:6e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=3c59x latency=64 maxlatency=8 mingnt=3 module=3c59x multicast=yes
htate@htate-desktop:~$

---

### Post by victorbrca on 2007-12-17
An you have the USB plugged on the PC?

How about this?

```
lsusb
```


Vic.

---

### Post by Kansasguy on 2007-12-17
Code:
---------
lsusb
---------

BUS 001 Device 007: ID obda:8189 Realtek Semiconductor Corp
BUS 001 Device 001: ID 0000:0000

(did some studying the other day and did find this)

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTrendnet](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTrendnet)
(the bottom line,  TRENDnet TEW-424UB ) if that helps

Also remember that there were other drivers on the CD (says he who hasn't even passed his first quarter freshman year exams)

---

### Post by victorbrca on 2007-12-17
k..  try putting the device in the USB port, wait for about 20 secs and type again:

```
lsusb
```

```
ndiswrapper -l
```

```
lshw -C network
```

Paste the full results if you can... 


Vic.

---

### Post by Kansasguy on 2007-12-17
I have only one USB port, so have to switch,  know how to unmount my flash drive which I am using to copy all this stuff.  But the device isn't recognized (I think) and a time or two I got a message "unsafe removal of device" but mostly with the flash drive, possibly once with the Realtek device

htate@htate-desktop:~$ lsusb
Bus 001 Device 008: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 0000:0000  
htate@htate-desktop:~$ ndiswrapper -l
sis163u : driver installed
htate@htate-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 3c905 100BaseTX [Boomerang]
       vendor: 3Com Corporation
       physical id: d
       bus info: pci@0000:01:0d.0
       logical name: eth0
       version: 00
       serial: 00:10:4b:2b:20:6e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=3c59x latency=64 maxlatency=8 mingnt=3 module=3c59x multicast=yes
htate@htate-desktop:~$

---

### Post by victorbrca on 2007-12-17
k... make sure you always right click on your usb drive and click on "unmount" before you remove it. 

Try removing the usb drive, than plug the usb wireless device and reboot the machine. Without removing it, run the same 3 codes.


Vic

---

### Post by Kansasguy on 2007-12-17
didn't cut and paste because I didn't want to "scortch" something, but it looks like the only difference  I can see in:

Bus 001 Device 008: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 0000:0000

that changed to:

Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 0000:0000

(the number after Device in the first line)

read somewhere about blacklisting?

---

### Post by Kansasguy on 2007-12-17
R

- Card: RTL8187B integrated in the laptop Gateway ML6720

    *
      Chipset: RTL8187B
    *
      USB Bus ID: 0BDA:8189
    *
      Driver: Win98
    *
      from: [ftp://202.65.194.212/cn/wlan/RTL8187B_driver_only.zip](ftp://202.65.194.212/cn/wlan/RTL8187B_driver_only.zip)
    *
      Other: Using ndiswrapper driver version 1.49, SUSE10.3 with kernel 2.6.22-9
    *
      Other: XP driver does not work - just see access points, no connect
******
Found this at:  (for what it's worth, don't know how old that is, or if there is a bug with Ubuntu Gutsy and ndiswrapper 1.5)

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/)

---

### Post by Kansasguy on 2007-12-17
There's this thread too, if that would help, especially page 2

[http://ubuntuforums.org/showthread.php?t=383504](http://ubuntuforums.org/showthread.php?t=383504)

---

### Post by victorbrca on 2007-12-17
I was just reading that too. I did not notice that your device had different chipset than mine. Man they are so stupid. Why not change the model number...  grrrrrrr

Ok... Let's remove the wrong driver:

```
ndiswrapper -i sis163u.inf
```

Now download the proper ones (.inf and .sys) from here (the ones under XP folder):

[LINK]("ftp://210.51.181.211/cn/wlan/Driver_1097_2KXP_0201.rar")

Now let's install them:

```
cd ~/
ndiswrapper -i net8185.inf
```

Them plug in the device and run:

```
ndiswrapper -l
```

Paste the result. Don't continue if one of the steps doesn't go through.


Vic.

---

### Post by Kansasguy on 2007-12-18
You'll get a break today and tomorrow,  I have to work, the link downloaded the .rar file, so I couldnt see the inf and sys, but they may be there.  Also looked them up at:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true)

and downloaded the one from:
Driver_1097_2KXP
and got the same thing.  Will try to do the rest tonight,  are the .inf and .sys  both inside the .rar

thanks again,  ht

---

### Post by Kansasguy on 2007-12-18
htate@htate-desktop:~$ ndiswrapper -i sis163u.inf
driver sis163u is already installed
htate@htate-desktop:~$ cd ~/
htate@htate-desktop:~$ ndiswrapper -i net8185.inf
couldn't open net8185.inf: No such file or directory at /usr/sbin/ndiswrapper line 219.
htate@htate-desktop:~$ ndiswrapper -i net8185.inf
couldn't open net8185.inf: No such file or directory at /usr/sbin/ndiswrapper line 219.
htate@htate-desktop:~$ 

Got this, thought something was funny when the second line above said "already installed" when we were trying to uninstall it.

There is another thread I was following:
[http://ubuntuforums.org/showthread.php?p=3974405#post3974405](http://ubuntuforums.org/showthread.php?p=3974405#post3974405)
especially page three, dawonn's post right after mine
you can see above what I tried    ht

---

### Post by victorbrca on 2007-12-18
Actually now was partially my mistake. To uninstall is -r... so

```
ndiswrapper -r sis163u.inf
```

  I copied it from my previous post and forgot to change it to -r. Sorry.  :S


  For the other one, do you remember where you saved the two new drivers? Did you unrar them? Where?


Vic.

---

### Post by Kansasguy on 2007-12-18
put them in home folder, didn't rar them, but will if you tell me how (or I can look it up)
(Its nice to know my guru messes up from time to time)

---

### Post by victorbrca on 2007-12-18
lol... I'm far from a guru... I'm a noob just like you!! ;)

Try double clicking on the rar file and see if it displays the contents. If it doesn't, open a terminal and install rar and unrar:

```
sudo apt-get install rar unrar
``` 

After that you should be able to double click and drag, or extract, just like in Windows. Save them to your home folder and try again:

```
cd ~/
ndiswrapper -i net8185.inf
```


Vic.

---

### Post by Kansasguy on 2007-12-20
aaaaarrrggggh
I got so frustrated with all the folders I had, and constantly seeing sis163etc, (and then doing an  -sis163u and it said it couldn't find it),  that I re-installed Ubuntu just to clear everything off.

Plan:  
1)     After installation of Gusty, install ndiswrapper-common and ndiswrapper-utils via the System menu -> Administration -> Synaptic Package Manager and searching for ndiswrapper. Tick the boxes next to each of these items to mark for installation and click Apply and follow the screens until finished.  (got this from:
file:///C:/Documents%20and%20Settings/Me/Desktop/TRENDnet_TEW-424UB_3.0R_(ndiswrapper).htm    (good site)

2)  I have the drivers on my flash drive, taken right from the CD that came with the 424UB
      They are: net8187b.cat        net8187b.inf    and      RTL8187B.sys    just like it says at the above site

         What should I name the folder that I put them in on home directory?

3)    I have ndiswrapper-1.50.tar.gz   194 KB  GZ file on the flash drive
       (also have driver_1097_2KXP_0201.rar      257 KB  RAR file , hoping not to need it because I have the above file, and don't want to get into rar if I don't have to.

4)   Seems like that's all I need, but don't know exactly what to do with all that stuff, what folders to put it in, etc.  Seems like good instructions at the above mentioned site, but again, need to know where to put them in my "clean slate".
            file:///C:/Documents%20and%20Settings/Me/Desktop/TRENDnet_TEW-424UB_3.0R_(ndiswrapper).htm

5)   And is it necessary to make permanent changes with  mod...... something when finished?

6)    ?????  (In other words, trying to start over)

---

### Post by victorbrca on 2007-12-20
Why would you start over? We were almost there...  



2- You can save the drivers anywhere, as long as you remember the location. 

3- You won't need this if you use step 1


Let me know once you get those done

Vic.

---

### Post by Kansasguy on 2007-12-20
Sorry, I just needed to "start over" and am learning a lot, and not willing to give up


Saved drivers and everything else I could think of both on my laptop (windows) and on my flash drive.

Re-installed the system

System > Admin > Synaptic package and installed ndiswrapper-common and ndiswrapper-utils

Made a folder called downloads

Made a folder called zstuff and put the drivers in it (wasn't sure why, but just thought they might be handy there)

Also put the drivers directly in the home folder

then:

htate@htate-desktop:~$ cd downloads

htate@htate-desktop:~/downloads$ tar -xzvf ndiswrapper-1.50.tar.gz

ndiswrapper-1.50/
ndiswrapper-1.50/AUTHORS
ndiswrapper-1.50/ChangeLog
ndiswrapper-1.50/INSTALL
ndiswrapper-1.50/Makefile
ndiswrapper-1.50/README

and a lot more stuff that ended in:

ndiswrapper-1.50/driver/wrapmem.h
ndiswrapper-1.50/driver/wrapmem.c
ndiswrapper-1.50/driver/wrapper.c
ndiswrapper-1.50/driver/wrapndis.h
ndiswrapper-1.50/driver/wrapndis.c
ndiswrapper-1.50/driver/lin2win.h
ndiswrapper-1.50/driver/win2lin_stubs.S
htate@htate-desktop:~/downloads$

then:

cd ndiswrapper-1.50

which got:

htate@htate-desktop:~/downloads/ndiswrapper-1.50$

make distclean, which yielded:

htate@htate-desktop:~/downloads/ndiswrapper-1.50$ make distclean

make -C driver clean
make[1]: Entering directory `/home/htate/downloads/ndiswrapper-1.50/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
divdi3.o workqueue.o .*.ko.cmd .*.o.cmd compat.h \
ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
make[1]: Leaving directory `/home/htate/downloads/ndiswrapper-1.50/driver'
make -C utils clean
make[1]: Entering directory `/home/htate/downloads/ndiswrapper-1.50/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/home/htate/downloads/ndiswrapper-1.50/utils'
rm -f *~
rm -fr ndiswrapper-1.50 ndiswrapper-1.50.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory `/home/htate/downloads/ndiswrapper-1.50/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
divdi3.o workqueue.o .*.ko.cmd .*.o.cmd compat.h \
ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
rm -f *_exports.h .\#* win2lin_stubs.h built-in.o
make[1]: Leaving directory `/home/htate/downloads/ndiswrapper-1.50/driver'
make -C utils distclean
make[1]: Entering directory `/home/htate/downloads/ndiswrapper-1.50/utils'
rm -f *~ *.o loadndisdriver
rm -f .\#*
make[1]: Leaving directory `/home/htate/downloads/ndiswrapper-1.50/utils'
rm -f .\#*
htate@htate-desktop:~/downloads/ndiswrapper-1.50$

Then:
make

Which yielded: a whole bunch of stuff, starting with”

htate@htate-desktop:~/downloads/ndiswrapper-1.50$ make
make -C driver
make[1]: Entering directory `/home/htate/downloads/ndiswrapper-1.50/driver'
make -C /usr/src/linux-headers-2.6.22-14-generic SUBDIRS=/home/htate/downloads/ndiswrapper-1.50/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
LD /home/htate/downloads/ndiswrapper-1.50/driver/built-in.o
CC [M] /home/htate/downloads/ndiswrapper-1.50/driver/crt.o
CC [M] /home/htate/downloads/ndiswrapper-1.50/driver/hal.o

about 10 more lines of “CC”

CC [M] /home/htate/downloads/ndiswrapper-1.50/driver/divdi3.o
LD [M] /home/htate/downloads/ndiswrapper-1.50/driver/ndiswrapper.o
Building modules, stage 2.
MODPOST 1 modules
CC /home/htate/downloads/ndiswrapper-1.50/driver/ndiswrapper.mod.o
LD [M] /home/htate/downloads/ndiswrapper-1.50/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: Leaving directory `/home/htate/downloads/ndiswrapper-1.50/driver'
make -C utils
make[1]: Entering directory `/home/htate/downloads/ndiswrapper-1.50/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory

and ending with:

(about 50 lines like the ones below)

loadndisdriver.c:517: warning: implicit declaration of function ‘printf’
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function ‘printf’
loadndisdriver.c:527: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:542: warning: implicit declaration of function ‘atof’
loadndisdriver.c:549: warning: implicit declaration of function ‘strcmp’
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:590: warning: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/htate/downloads/ndiswrapper-1.50/utils'
make: *** [all] Error 2
htate@htate-desktop:~/downloads/ndiswrapper-1.50$

and I've left it right there (maybe last time I went ahead and tried the sudo make install, but I cant remember.  Will try not to turn it off til I hear from you.  (think you might be a guru in disguise, or at least in the making).      ht

---

### Post by victorbrca on 2007-12-20
lol... fair enough... if you are learning is always good.

  You are trying to install the software again. You installed via synaptic and now you are trying to do via the tar. You don't have to do it again, actually, you should not...  :)

  All you have to do now is install the driver.

1- Open a terminal and go to the folder where the drivers are:

```
cd downloads/zstuff
```


2- Now install the driver

```
ndiswrapper -i net8185.inf
```


Let me know,


Vic.

---

### Post by Kansasguy on 2007-12-20
had the drivers both in zstuff, and in the home folder, so I tried it twice:

htate@htate-desktop:~$ cd zstuff
htate@htate-desktop:~/zstuff$ ndiswrapper -i net8185.inf
couldn't create /etc/ndiswrapper/net8185: Permission denied at /usr/sbin/ndiswrapper-1.9 line 152.
htate@htate-desktop:~/zstuff$ cd ..
htate@htate-desktop:~$ ndiswrapper -i net8185.inf
couldn't create /etc/ndiswrapper/net8185: Permission denied at /usr/sbin/ndiswrapper-1.9 line 152.
htate@htate-desktop:~$ 

oops, looking at that, I might have gone to the desktop instead of home folder, but I think the result is the same, "permission denied"          should I "sudo"?

---

### Post by victorbrca on 2007-12-20
yes sir... 

```
sudo ndiswrapper -i net8185.inf
```

---

### Post by Kansasguy on 2007-12-20
htate@htate-desktop:~$ 
htate@htate-desktop:~$ cd zstuff
htate@htate-desktop:~/zstuff$ sudo ndiswrapper -i net8185.inf
[sudo] password for htate:
installing net8185 ...
couldn't open net8185.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.
htate@htate-desktop:~/zstuff$ cd ..
htate@htate-desktop:~$ sudo ndiswrapper -i net8185.inf
driver net8185 is already installed
htate@htate-desktop:~$

---

### Post by victorbrca on 2007-12-20
Check if it's installed. Plug in the device and run

```
ndiswrapper -l
```

---

### Post by Kansasguy on 2007-12-20
interesting, both say invalid driver:
net8185
net8187b

where did the "5" come from?

?  -r  ?

---

### Post by victorbrca on 2007-12-20
yes, try to remove and them re-install:

```
ndiswrapper -r net8185
ndiswrapper -r net8187b
```

```
sudo ndiswrapper -i net8185.inf
```

---

### Post by Kansasguy on 2007-12-21
htate@htate-desktop:~$ cd downloads
htate@htate-desktop:~/downloads$ ndiswrapper -l
net8187b : invalid driver!
htate@htate-desktop:~/downloads$ sudo ndiswrapper -r net8187b
[sudo] password for htate:
htate@htate-desktop:~/downloads$ cd zstuff
bash: cd: zstuff: No such file or directory
htate@htate-desktop:~/downloads$ cd ..
htate@htate-desktop:~$ cd zstuff
htate@htate-desktop:~/zstuff$ sudo ndiswrapper -i net8187b.inf
installing net8187b ...
htate@htate-desktop:~/zstuff$ sudo ndiswrapper -l
net8187b : driver installed
htate@htate-desktop:~/zstuff$ 

I Did It,      after the above I removed the USB, put in the device, and rebooted.  As far as I can see the machine didn't show it, BUT,    in the Terminal I did the ndiswrapper -l and it gave me the long-awaited:

device (obda:8189) installed (may not be exact as I am typing it from memory)

net8187b : driver installed
        device (0BDA:8189) present     (I think)


What's next????  According to the website, it's"
**********
sudo modprobe ndiswrapper

If that returns with no errors you should be able to configure the wlan0 device under System->Administration->Networking.

To make this change permanent, do this to make the module autoload at boot up:

sudo ndiswrapper -m
***************************
and then on to:

"I however was unable to use the Networking Manager to connect to any WEP enabled networks, but was able to do it via command line without any problems."  (quoted from the website)

Gather information about the Access Point you want to connect to.

iwlist wlan0

Now make a connection to your chosen Access Point

sudo iwconfig wlan0 essid <AP NAME> ap <AP MAC ADDRESS> key <KEY IN HEX>
sudo dhclient wlan0

CategoryDocumentation CategoryHa

---

### Post by Kansasguy on 2007-12-21
Went back to page one, and found your post saying:
********************
Code:
cd ~/
ndiswrapper -i sis163u.inf
If no error where shown run:
Code:
depmod -a
Again If no error where shown (load ndiswrapper as a module):
Code:
modprobe ndiswrapper
Them check if the driver is being used by device. Plug in the device and run:
Code:
ndiswrapper -l
The result should be:
Quote:
sis163u : driver installed
device (0457:0163) present
Let me know how far you get...
*******************
Q.  should I do the depmod -a and modprobe diswrapper, before moving on, and if so, does it matter what folder I am in when I do it?

---

### Post by victorbrca on 2007-12-21
> **Kansasguy said:**
> Went back to page one, and found your post saying:
********************
Code:
cd ~/
ndiswrapper -i sis163u.inf
If no error where shown run:
Code:
depmod -a
Again If no error where shown (load ndiswrapper as a module):
Code:
modprobe ndiswrapper
Them check if the driver is being used by device. Plug in the device and run:
Code:
ndiswrapper -l
The result should be:
Quote:
sis163u : driver installed
device (0457:0163) present
Let me know how far you get...
*******************
Q.  should I do the depmod -a and modprobe diswrapper, before moving on, and if so, does it matter what folder I am in when I do it?

Almost perfect ... just don't run "ndiswrapper -i sis163u.inf" again... 

The folder location has nothing to do with those commands.. but you might need sudo..

---

### Post by Kansasguy on 2007-12-21
htate@htate-desktop:~$ depmod -a
FATAL: Could not open /lib/modules/2.6.22-14-generic/modules.dep.temp for writing: Permission denied

htate@htate-desktop:~$ cd zstuff
htate@htate-desktop:~/zstuff$ sudo ndiswrapper -l
[sudo] password for htate:
net8187b : driver installed

htate@htate-desktop:~/zstuff$ depmod -a
FATAL: Could not open /lib/modules/2.6.22-14-generic/modules.dep.temp for writing: Permission denied

htate@htate-desktop:~/zstuff$
htate@htate-desktop:~/zstuff$ cd ..
htate@htate-desktop:~$ depmod -a
FATAL: Could not open /lib/modules/2.6.22-14-generic/modules.dep.temp for writing: Permission denied
htate@htate-desktop:~$ 

(turned off the computer last night after happily getting to: 
net8187b : driver installed
device (0BDA:8189) present
so my second try above I tried to get back there, and did the 3rd try above because I saw that I had done the second one in zstuff folder, probably not the problem, but shows you what I was trying to do)

---

### Post by TheGreatSage on 2007-12-21
Where you are getting permission denied, you need to insert sudo before those commands.

---

### Post by victorbrca on 2007-12-21
> **victorbrca said:**
> ...The folder location has nothing to do with those commands.. but you might need sudo..

> **TheGreatSage said:**
> Where you are getting permission denied, you need to insert sudo before those commands.

Try...

```
sudo depmod -a
```

---

### Post by Kansasguy on 2007-12-21
htate@htate-desktop:~$ sudo depmod -a
[sudo] password for htate:
htate@htate-desktop:~$ modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko): Operation not permitted
htate@htate-desktop:~$ sudo modprobe diswrapper
FATAL: Module diswrapper not found.
htate@htate-desktop:~$ 


I think the first one worked, (depmod -a)  because it gave no error message, but also no text.  Forgot sudo on modprobe, then tried it a second time  >  FATAL

---

### Post by victorbrca on 2007-12-21
Sorry man... this where my knowledge stops... I have the exact same problem on a Fedora machine. I think it's a problem between the kernel version and ndiswrapper version...

[http://fedoraforum.org/forum/showthread.php?t=174154](http://fedoraforum.org/forum/showthread.php?t=174154)

See... no guru here...  :-S


Vic.

---

### Post by TheGreatSage on 2007-12-22
I was using most of the same commands as yourself yesterday as I was having a wireless nightmare myself.

I 'think' I got the same error message as yourself at 1 point, but was offered an alternative command to use which contained 'common' in the command.

Vague I know, but you could try and see if you get the same message as I did.

---

### Post by Kansasguy on 2007-12-22
Sage, I would sure like to know that command with the "common" in it, paste it here if you would please.  I want to get this thing up and going, but I think there may be a mismatch between the kernal and possibly the version of diswrapper.

Quote:
R

- Card: RTL8187B integrated in the laptop Gateway ML6720

    *
      Chipset: RTL8187B
    *
      USB Bus ID: 0BDA:8189
    *
      Driver: Win98
    *
      from: [ftp://202.65.194.212/cn/wlan/RTL8187B_driver_only.zip](ftp://202.65.194.212/cn/wlan/RTL8187B_driver_only.zip)
    *
      Other: Using ndiswrapper driver version 1.49, SUSE10.3 with kernel 2.6.22-9
    *
      Other: XP driver does not work - just see access points, no connect


from:  [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/)

keep going     ht

---

### Post by go_beep_yourself on 2007-12-27
HELP!!!!!!!!!!!!!!!!!!!!! No internet in Linux

I tried using Vista x86 and x64 drivers with ndiswrapper. Neither
appeared to work.I thought I had to use ndiswrapper, but as I was
browsing around the web to find the windows driver, I found a linux
driver, so I began to follow the directions, but got stuck while
running a command didn't work. I have no experience with wireless in
Linux.

```
chris@ubuntu:~/Desktop/rtl8185_linux_26.1027.0823.2007$ ls
ifcfg-wlan0  release_note    wlan0dhcp  wpa_supplicant-0.4.9.tar.gz
makedrv      rtl8185.tar.gz  wlan0down
readme       stack.tar.gz    wlan0up
chris@ubuntu:~/Desktop/rtl8185_linux_26.1027.0823.2007$ cat readme
RTL8185 Linux Driver v1027.0823.2007 for linux kernel 2.6

  - Support Client mode for either infrastructure or adhoc mode
  - Support WEP and WPAPSK/WPA2PSK connection

===============================================================================================
< Component >
The driver is composed of several parts:
    (1)source code
        rtl8185.tar.gz
        stack.tar.gz

    (2)Script ot build the modules
        makedrv

    (3)Script to load/unload modules
        wlan0up
        wlan0down

    (4)Script and configuration for DHCP
        wlan0dhcp
        ifcfg-wlan0

    (5)Supplicant source code
        wpa_supplicant-0.4.9.tar.gz

    (6)Example of supplicant configuration file
        wpa1.conf




< Installation >
Running the scripts can finish all operations of building up modules
from source code and start the nic:

        (1)Build up the driver from the source code
                ./makedrv

        (2)Load the driver module to kernel and start up nic
                ./wlan0up
           (if "insmod: error inserting 'r8180.ko': -File exists." met,
                ./wlan0rmv
                ./wlan0down
                ./wlan0up
            should be OK.
           )
        (3)Refer to < Set wireless lan MIBs > to set Wireless LAN
specific parameters.





< Set wireless lan MIBs >
This driver uses Wireless Extension as an interface allowing you to set
Wireless LAN specific parameters.

Current driver supports "iwlist" to show the device status of nic

        iwlist wlan0 [parameters]
where

        parameter explaination          [parameters]
        -----------------------         -------------
        Show available chan and freq    freq / channel
        Show and Scan BSS and IBSS      scan[ning]
        Show supported bit-rate         rate / bit[rate]
        Show Power Management mode      power

For example:

        iwlist wlan0 channel
        iwlist wlan0 scan
        iwlist wlan0 rate
        iwlist wlan0 power


Driver also supports "iwconfig", manipulate driver private ioctls, to set MIBs.

        iwconfig wlan0 [parameters] [val]
where

        parameter explaination      [parameters]                [val]
constraints
        -----------------------     -------------
------------------
        Connect to AP by address    ap                          [essid]
        Set the essid, join (I)BSS  essid                       [mac_addr]
        Set operation mode          mode                        {Managed|Ad-hoc}
        Set keys and security mode  key / enc[ryption]
{N|open|restricted|off}


For example:

        iwconfig wlan0 ap XX:XX:XX:XX:XX:XX
        iwconfig wlan0 essid "ap_name"
        iwconfig wlan0 mode Ad-hoc
        iwconfig wlan0 mode essid "name" mode Ad-hoc
        iwconfig wlan0 key 0123456789 [2] open
        iwconfig wlan0 key off
        iwconfig wlan0 key restricted [3] 0123456789

< Getting IP address >
After start up the nic, the network needs to obtain an IP address
before transmit/receive data.
This can be done by setting the static IP via "ifconfig wlan0
IP_ADDRESS" command, or using DHCP.

If using DHCP, setting steps is as below:

        (1)connect to an AP via "iwconfig" settings
                iwconfig wlan0 essid [name]     or
                iwconfig wlan0 ap XX:XX:XX:XX:XX:XX

        (2)run the script which run the dhclient
                ./wlan0dhcp
           or
                dhcpcd wlan0
                (Some network admins require that you use the
                hostname and domainname provided by the DHCP server.
                In that case, use
                dhcpcd -HD wlan0)



< WPAPSK >
WPA_SUPPLICANT help the network to communicate under the protection of
WPAPSK mechanism

        (1)Unpack source code of WPA supplicant:
                tar -zxvf wpa_supplicant-0.4.9.tar.gz
                cd wpa_supplicant-0.4.9

        (2)Create .config file:
                cp defconfig .config

        (3)Edit .config file, uncomment the following line:
                #CONFIG_DRIVER_IPW=y.

        (4)Build WPA supplicant:
                make

        If make error for lack of <include/md5.h>, install the openssl lib:
         1. Install the openssl lib from corresponding installation disc:
            Fedora Core 2/3/4/5/6/7(openssl-0.9.71x-xx),
            Mandrake10.2/Mandriva10.2(openssl-0.9.7x-xmdk),
            Debian 3.1(libssl-dev), Suse 9.3/10.0/10.1(openssl_devl),
            Gentoo(dev-libs/openssl), etc.
         2. Download the openssl open source package from
www.openssl.org, build and install it.

        (5)Edit wpa_supplicant.conf to set up SSID and its passphrase.
        For example, the following setting in "wpa1.conf" means SSID
to join is "BufAG54_Ch6"
        and its passphrase is "87654321".

                network={
                        ssid="BufAG54_Ch6"
                        proto=WPA
                        key_mgmt=WPA-PSK
                        pairwise=CCMP TKIP
                        group=CCMP TKIP WEP104 WEP40
                        psk="87654321"
                        priority=2
                }
        Note: 1. proto=WPA for WPA, proto=RSN for WPA2.
              2. If you want to connect an AP which works under WPA2
mixed mode, you'd better
                 use Realtek customed wpa_supplicant package.


        (6)Execute WPA supplicant (Assume 8185 and related modules had
been loaded):
                ./wpa_supplicant -D ipw -c wpa1.conf -i wlan0 &
chris@ubuntu:~/Desktop/rtl8185_linux_26.1027.0823.2007$   ./makedrv
./ieee80211/
./ieee80211/ieee80211_module.c
./ieee80211/ieee80211_rx.c
./ieee80211/tags
./ieee80211/Makefile
./ieee80211/ieee80211_crypt_tkip.c
./ieee80211/ieee80211_softmac.c
./ieee80211/readme
./ieee80211/ieee80211_crypt_ccmp.c
./ieee80211/ieee80211.h
./ieee80211/ieee80211_tx.c
./ieee80211/ieee80211_softmac_wx.c
./ieee80211/ieee80211_crypt.h
./ieee80211/ieee80211_wx.c
./ieee80211/license
./ieee80211/ieee80211_crypt_wep.c
./ieee80211/ieee80211_crypt.c
rtl8185/
rtl8185/README.adhoc
rtl8185/r8180_sa2400.h
rtl8185/Makefile
rtl8185/copying
rtl8185/README.master
rtl8185/r8180.h
rtl8185/install
rtl8185/r8180_max2820.h
rtl8185/r8180_max2820.c
rtl8185/r8180_rtl8225.h
rtl8185/r8180_wx.h
rtl8185/authors
rtl8185/tags
rtl8185/r8180_pm.c
rtl8185/r8180_hw.h
rtl8185/r8180_gct.c
rtl8185/r8180_gct.h
rtl8185/r8180_rtl8225.c
rtl8185/readme
rtl8185/r8180_93cx6.h
rtl8185/ieee80211.h
rtl8185/license
rtl8185/r8180_pm.h
rtl8185/changes
rtl8185/r8180_rtl8225z2.c
rtl8185/r8180_wx.c
rtl8185/r8180_rtl8255.c
rtl8185/r8180_93cx6.c
rtl8185/r8180_sa2400.c
rtl8185/r8180_core.c
rtl8185/r8180_rtl8255.h
rtl8185/ieee80211_crypt.h
rm -f *.mod.c *.mod *.o .*.cmd *.ko
rm -rf /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/tmp
make -C /lib/modules/2.6.22.9chris1/build
M=/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211 CC=gcc
modules
make[1]: Entering directory `/usr/src/linux-source-2.6.22'
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.o
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:
In function 'ieee80211_softmac_init':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2236:
warning: assignment from incompatible pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2237:
warning: assignment from incompatible pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2238:
warning: assignment from incompatible pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2239:
warning: assignment from incompatible pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2240:
warning: assignment from incompatible pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2241:
warning: assignment from incompatible pointer type
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_rx.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_tx.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_wx.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_module.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.o
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:
In function 'ieee80211_ccmp_aes_encrypt':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:88:
warning: passing argument 1 of 'crypto_cipher_encrypt_one' from
incompatible pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:
In function 'ieee80211_ccmp_init':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:110:
warning: assignment from incompatible pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:127:
warning: passing argument 1 of 'crypto_free_cipher' from incompatible
pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:
In function 'ieee80211_ccmp_deinit':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:144:
warning: passing argument 1 of 'crypto_free_cipher' from incompatible
pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:
In function 'ieee80211_ccmp_set_key':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:422:
warning: passing argument 1 of 'crypto_cipher_setkey' from
incompatible pointer type
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_wep.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211-rtl.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt-rtl.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_wep-rtl.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip-rtl.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp-rtl.o
  Building modules, stage 2.
  MODPOST 5 modules
  CC      /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211-rtl.mod.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211-rtl.ko
  CC      /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt-rtl.mod.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt-rtl.ko
  CC      /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp-rtl.mod.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp-rtl.ko
  CC      /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip-rtl.mod.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip-rtl.ko
  CC      /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_wep-rtl.mod.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_wep-rtl.ko
make[1]: Leaving directory `/usr/src/linux-source-2.6.22'
rm -f *.mod.c *.mod *.o .*.cmd *.ko *~
rm -rf /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/tmp
make -C /lib/modules/2.6.22.9chris1/build
M=/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185 CC=gcc
modules
make[1]: Entering directory `/usr/src/linux-source-2.6.22'
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.o
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:
In function 'proc_get_stats_hw':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:375:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:376:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:379:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:380:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:383:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:384:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:
In function 'check_tx_ring':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:909:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:909:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:910:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:910:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:
In function 'alloc_tx_desc_ring':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:1592:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:1592:
warning: cast to pointer from integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:
In function 'alloc_rx_desc_ring':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:1770:
warning: cast from pointer to integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:1770:
warning: cast to pointer from integer of different size
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:
In function 'rtl8180_init':
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:3159:
warning: assignment from incompatible pointer type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:3522:
warning: 'deprecated_irq_flag' is deprecated (declared at
include/linux/interrupt.h:66)
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:3522:
warning: passing argument 2 of 'request_irq' from incompatible pointer
type
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:
At top level:
/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:579:
warning: 'r8180_get_wireless_stats' defined but not used
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_sa2400.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_93cx6.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_wx.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_max2820.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_gct.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_rtl8225.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_rtl8225z2.o
  CC [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_rtl8255.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "ieee80211_softmac_stop_protocol_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "free_ieee80211_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_get_wap_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wake_queue_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_rx_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_get_mode_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_is_shortslot"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_set_freq_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_get_name_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_get_rate_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_set_rate_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_ps_tx_ack"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_get_freq_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_is_54g"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_stop_queue_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_set_scan_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_get_essid_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_get_scan_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wpa_supplicant_ioctl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_set_mode_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_get_beacon"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_set_rawtx_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_set_encode_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_stop_protocol_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_set_wap_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_get_power_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_get_encode_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_softmac_start_protocol_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wlan_frequencies_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_set_power_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "alloc_ieee80211_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_reset_queue"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_wx_set_essid_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
WARNING: "ieee80211_start_protocol_rtl"
[/home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko]
undefined!
  CC      /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.mod.o
  LD [M]  /home/chris/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180.ko
make[1]: Leaving directory `/usr/src/linux-source-2.6.22'
chris@ubuntu:~/Desktop/rtl8185_linux_26.1027.0823.2007$ ./wlan0up
insmod: error inserting 'ieee80211_crypt-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211_crypt_wep-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211_crypt_tkip-rtl.ko': -1 Operation
not permitted
insmod: error inserting 'ieee80211_crypt_ccmp-rtl.ko': -1 Operation
not permitted
insmod: error inserting 'ieee80211-rtl.ko': -1 Operation not permitted
insmod: error inserting 'r8180.ko': -1 Operation not permitted
wlan0: ERROR while getting interface flags: No such device
chris@ubuntu:~/Desktop/rtl8185_linux_26.1027.0823.2007$ sudo ./wlan0up
[sudo] password for chris:
wlan0: ERROR while getting interface flags: No such device
chris@ubuntu:~/Desktop/rtl8185_linux_26.1027.0823.2007$
```

Why does it say wlan0, no such device? I appended this to my
/etc/network/interfaces

```
iface wlan0 inet dhcp

auto wlan0


```
and I restarted the networking service.

---

