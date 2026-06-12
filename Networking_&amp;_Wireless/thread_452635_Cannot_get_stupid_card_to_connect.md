---
title: "Cannot get stupid card to connect"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by jbullfrog on 2007-05-23
I have just purchased a Gigabyte GN-WP01GS wireless card from Newegg.com

[http://www.newegg.com/Product/Product.asp?item=N82E16839121008](http://www.newegg.com/Product/Product.asp?item=N82E16839121008)

and for the life of me cannot get it to work.  The card recognized my wireless home network straight out of the box, but would not connect.

By checking  the supported card list,  I saw that it would not work straight out of the box.

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsGigabyteTechnology](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsGigabyteTechnology)

So I went to the tutorial that was suggested:

[http://ubuntuforums.org/showthread.php?t=296822](http://ubuntuforums.org/showthread.php?t=296822)

I downloaded the latest driver: [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

**RT2501PCI/mPCI/CB(RT61:RT2561W/RT2561S/RT2661)**

Now what do I do?  Could someone give me the instructions for this specific driver?  I am such a n00b.  Any help would be greatly appreciated.

This is my first time doing this.  You see, I just built my first computer ever, and installed Linux as my sole operating system.  (I have been a windows user all my life, but want to change)

If you are willing to chat on AIM, that would be much more helpful.  Just PM me your username.  Mine is **militantfroggy**.

---

### Post by blazercist on 2007-05-23
youre going to need the newest CVS driver from rt2x00 serial monkey not the beta2, the hourly or dialy or nightly or whatever they are calling it there.  Also, try using their utility RutilT instead of network-manager

yeah those instructions are a bit out dated, they are for edgy btw not fiesty...  Anyway these drivers are still under heavy heavy heavy development so you shouldn't give up I have an RT61 based card and it took a while and I made some sacrafices but it works.

---

### Post by jbullfrog on 2007-05-23
thanks blazercist, but could somebody give me more details?  Thanks in advance

---

### Post by blazercist on 2007-05-23
first you need to give some more detailed information.

What kind of router you have, are you using WEP or WPA

give use the output pf the commands:

sudo iwconfig ra0

sudo ifconfig ra0

How are you trying to connect?  Using network manager?  If your router is using WEP or WPA try disabling encryption and see if you can connect.

---

### Post by jbullfrog on 2007-05-23
I have the following router: [http://computers.pricegrabber.com/wireless-networking/m/669628/details/](http://computers.pricegrabber.com/wireless-networking/m/669628/details/)

How do I know if I am using WEP or WPA?  I do know that I have to enter a WEP key that is 10 characters long.  Does that mean i am using WEP?

---

### Post by jbullfrog on 2007-05-23
ubuntu@ubuntu:~$ sudo iwconfig ra0
ra0       RT61 Wireless  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr: off   Fragment thr: off                                                                  
          Encryption key:0000-0000-00
          Link Quality=76/100  Signal level:-65 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ubuntu@ubuntu:~$ sudo ifconfig ra0
ra0       Link encap:Ethernet  HWaddr 00:1A:4D:20:B8:8D  
          inet6 addr: fe80::21a:4dff:fe20:b88d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11484 errors:66 dropped:0 overruns:0 frame:0
          TX packets:17237 errors:0 dropped:0 overruns:0 carrier:0
          collisions:3 txqueuelen:1000 
          RX bytes:965430 (942.8 KiB)  TX bytes:920 (920.0 b)
          Interrupt:21 


If anyone is wondering, I put a space between thr: and off because otherwise a smiley face would have been drawn
I hope this helps.  I have no clue what it means...

I am trying to use the following guide: [http://ubuntuforums.org/showthread.php?t=419709&highlight=rt61](http://ubuntuforums.org/showthread.php?t=419709&highlight=rt61)

any help would be much appreciated.  I just started learning ubuntu 3 days ago

---

### Post by blazercist on 2007-05-24
Ok you are having the same problem I had, It is WEP and thats your problem.

The beta driver has problems remembering WEP keys and thats why you see the router but cant get an IP, its because your comp is telling the router your WEP key is 0000-00-0000.  You need either the latest CVS  from [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads) choose the hourly tarball.  Or you can ask Spy84464 from the rt2x00 forums for the WEP key patch.  Then you need to apply the patch, compile the driver, and install the driver and it should work just fine.  If you need help applying the patch look at the bottom of this thread, its me and Spy figuring this thing out [http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=3752](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=3752) 

Essentially you just extract all the driver source to its own folder (if your patching the driver theres one command that I don't remember ask Spy)  then you just do:

make   #you may need to do "sudo" before make if it complains about access or permissions
make install  #you may need to do "sudo" before make if it complains about access or permissions

Then search for your old rt61 module its called rt61.ko
and replace it with the newly created one in the directory where you were doing all the "make" stuff.

In order to do this:

sudo cp ./rt61.ko /dir/to/old/rt61.ko

---

### Post by blazercist on 2007-05-24
If you still are having trouble or need help compiling the driver pm me.

---

