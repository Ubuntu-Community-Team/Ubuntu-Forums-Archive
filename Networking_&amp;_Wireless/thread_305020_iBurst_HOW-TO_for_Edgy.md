---
title: "iBurst HOW-TO for Edgy"
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by Skrewdriver on 2006-11-22
[B][I]Currently this HOW-TO is for the PCMCIA modem only. I haven't upgraded my desktop (with iBurst USB) to Edgy yet.


[/I][/B]#1 Rule - don't plug the card in until I tell you to. Thanks.

[LIST=1]
[*]First thing is you need to download the iBurst drivers from our good friends at sourceforge:
[http://sourceforge.net/projects/ibdriver/]("http://sourceforge.net/projects/ibdriver/")
Make sure you download the version for 2.6.17 kernels (at time of writing the file is ibdriver-1.3.1-linux-2.6.17.tar.gz )

[*]Open up a terminal and make sure the tarball  you just downloaded is in the directory you want to work in. Extract the tar file:
```
tar -xf ibdriver*
```

[*]You need to have installed the build-essentials package, plus the linux kernel headers. *These packages do not come on the standard desktop install CD - if you do not have a network connection then you need to download the **alternate** install CD.*
```
sudo aptitude install build-essential linux-headers-generic
```

[*]Now cd to the directory with the ibdriver source, then make and install the drivers.
```
make
sudo make install
```
If all goes well you will get no error messages, the output of the **make** command should look something like this:
```
* will do this later *

```
... and you have successfully compiled and installed the driver modules. Now we gots to change a few configuration files.
EDIT: For USB (desktop) modems, skip the PCMCIA steps and go straight to configuring the dialer
[*]Change this file:
```
sudo gedit /etc/default/pcmcia
```
Look for a line that says **CORE_OPTS**. Change it to the following:
```
CORE_OPTS="unreset_check=20 unreset_delay=100 unreset_limit=100"
```
Save the file and exit
[*]Next file:
```
sudo gedit /etc/modprobe.d/iburst
```
The only text in this file should be:
```
options ib-net ifname="ib%d"
```
**EDIT (2006-11-27) : I forgot the %d on the above line of code**
Save the file and exit
[*]Okay, that is the PCMCIA stuff configured. Restart your laptop
Then **plug your card in.** :KS  If sound is enabled, you should hear two beeps, and eventually the status light goes from [COLOR="Magenta"]purple[/COLOR] to [COLOR="Blue"]blue[/COLOR]. That means your card is plugged in and happy. You can check this by listing the loaded modules:
```
lsmod | grep ib_
```
.. if all is well you will see **ib_net** and **ib_pcmcia** listed.
[*]Now we configure the dialer.
```
sudo pppoeconf
```
**EDIT (2006-11-27): corrected typo in above code.**
.. answer all the questions. If in doubt, say yes or go with the defaults.
[*] Now we will test the connection. Make sure you are somewhere with good reception, so the reception quality light on your card should be [COLOR="Green"]green[/COLOR]. Run the command to initialise a pppoe connection:
```
sudo ifup ib
```
... and (fingers crossed) you should get a connection!
To stop the connection use the command:
```
sudo ifdown ib
```
[/LIST]

And that is it. Give yourself a pat on the back.

---

### Post by ellisdee on 2007-01-05
Thanks for this mate!

Works a treat!

I found using the roaring penguin pppoe client is much better for ease of use but everything in this walk through is accurate and works well  ;)

Thanks again!

---

### Post by coco3004 on 2007-01-24
Hi all,  ok im a bit of a n00b at linux so sorry if this is a dumb problem.

Im installing iBurst on my ubuntu edgy build, I get to step 4 (make) and I get the following errors.

***
frank@frank-laptop:~/Software Folder/iBurst /ibdriver-1.3.1-linux-2.6.17$ make
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/frank/Software Folder/iBurst /ibdriver-1.3.1-linux-2.6.17 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** No rule to make target `Folder/iBurst'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [default] Error 2
frank@frank-laptop:~/Software Folder/iBurst /ibdriver-1.3.1-linux-2.6.17$ 
***
What gives ??.  Now I've installed all the pre-reqs I'm pretty sure, got the sym link to the buld env ok, so what am I doing wrong. ??

I've included some info in case it may help and speed up the process here;

ls -l /lib/modules/$(uname -r)

lrwxrwxrwx  1 root root     40 2007-01-25 03:52 build -> /usr/src/linux-headers-2.6.17-10-generic
drwxr-xr-x  2 root root   4096 2007-01-24 17:33 initrd
drwxr-xr-x 11 root root   4096 2006-10-25 23:30 kernel
drwxr-xr-x  2 root root   4096 2007-01-24 17:33 madwifi
-rw-r--r--  1 root root 326086 2007-01-24 17:35 modules.alias
-rw-r--r--  1 root root     69 2007-01-24 17:35 modules.ccwmap
-rw-r--r--  1 root root 358970 2007-01-24 17:35 modules.dep
-rw-r--r--  1 root root    813 2007-01-24 17:35 modules.ieee1394map
-rw-r--r--  1 root root    806 2007-01-24 17:35 modules.inputmap
-rw-r--r--  1 root root  22378 2007-01-24 17:35 modules.isapnpmap
-rw-r--r--  1 root root     74 2007-01-24 17:35 modules.ofmap
-rw-r--r--  1 root root 258448 2007-01-24 17:35 modules.pcimap
-rw-r--r--  1 root root   1135 2007-01-24 17:35 modules.seriomap
-rw-r--r--  1 root root 142787 2007-01-24 17:35 modules.symbols
-rw-r--r--  1 root root 388977 2007-01-24 17:35 modules.usbmap
drwxr-xr-x  2 root root    340 2007-01-25 22:18 volatile
frank@frank-laptop:~$ 

ls /lib/modules/$(uname -r)/build  

frank@frank-laptop:~$ ls /lib/modules/$(uname -r)/build
arch      fs       lib                              Module.symvers  usr
block     include  linux-headers-2.6.17-10-generic  net
crypto    init     Makefile                         scripts
drivers   ipc      mm                               security
firmware  kernel   modules                          sound
frank@frank-laptop:~$ 

ls /usr/src/linux-headers-$(uname -r)

frank@frank-laptop:~$ ls /usr/src/linux-headers-$(uname -r)
arch      fs       lib                              Module.symvers  usr
block     include  linux-headers-2.6.17-10-generic  net
crypto    init     Makefile                         scripts
drivers   ipc      mm                               security
firmware  kernel   modules                          sound
frank@frank-laptop:~$ 

hope this helps

COCO!

---

### Post by coco3004 on 2007-01-25
Ok after a lot of stuffing around, I managed to fix the make issue.  So now I got to this step and there is noting in the pcmcia file, i that normal ??  I added the OPT.... line and went through the whole process fine but now I get this...

sudo ifup ib

Ignoring unknown interface ib=ib.

Now I am really stuck guys, any help would be appreciated.  

BTW when I plugged in the pcmcia card I did not get any beeps and the Audio is Configured and working.. Blue LED is on also.

Thanks in Advance.

COCO!

ps
lsmod | grep ib_

ib_pcmcia              12300  1 
ib_net                  8324  1 ib_pcmcia
pcmcia                 40380  1 ib_pcmcia
pcmcia_core            43924  4 ib_pcmcia,pcmcia,yenta_socket,rsrc_nonstatic

---

### Post by MoHamm on 2007-02-03
Hey All

 I am on day 3 of trying to get the iburst pcmcia running;
i finally found your how to and thank God for that, and you!!

I am now stuck at step 5;

> sudo gedit /etc/default/pcmcia

I cant seem to locate the pcmcia anywhere.

Help Please!

---

### Post by MoHamm on 2007-02-05
DONE :guitar: 
Screwdriver thanks so much for your efforts, your instructions are very articulate and easy to follow,
my difficulty with the HowTo instructions was due to my inexperience with Linux... Things are changing though!!!

Peace Out!!

EDIT: 

[B][COLOR="Red"]I forgot to note though that I had a bit of difficulty with the following;
[/COLOR][/B]
> Step 5 Change this file:
Code:

sudo gedit /etc/default/pcmcia

[COLOR="Red"]Look for a line that says CORE_OPTS. Change it to the following:[/COLOR]
Code:

CORE_OPTS="unreset_check=20 unreset_delay=100 unreset_limit=100"

Save the file and exit

**I could not find the line, it was actually an empty page, I added it  after seeing in the [B][COLOR="Red"]ibdriver README[/COLOR] **following;
[/B]
> [COLOR="Red"]**Add**[/COLOR]/modify the following line:

CORE_OPTS="unreset_check=20 unreset_delay=100 unreset_limit=100"

Key word being ADD; I think it would make a difference with us noobies..

Thanks a million!

---

### Post by coco3004 on 2007-02-06
Thanks MoHamm

Although this walkthru is great there are a number of omissions and errors that I have found and being a noob its very difficult to piece things together, although I think that I may have done it.  The readme.txt in the ib driver tarball was a great help I found also.

Thanks

COCO!

---

### Post by DavidBarkhuizen on 2007-05-18
Thanks bro.

---

### Post by Cirrocco on 2007-06-12
I'm having quite a bit of trouble with this how-to.
does anyone have access to a 7.04 fiesty how-to for this?

I'm getting stuck on step 6 - this file doesn't exist... am I supposed to create it?

---

### Post by damies on 2007-10-19
Hi All,

I'm having trouble getting the ibdriver to compile on Ubuntu 7.10 (Gusty Gibbon), 

I am using ibdriver-1.2.9 (latest from sf website) Has anyone else had any success?

Here is my terminal output (real hostname replaced with hostname):

root@hostname:/Data/Downloads/ibdriver-1.2.9# aptitude install build-essential linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
root@hostname:/Data/Downloads/ibdriver-1.2.9# make
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/Data/Downloads/ibdriver-1.2.9 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /Data/Downloads/ibdriver-1.2.9/ib-net.o
/Data/Downloads/ibdriver-1.2.9/ib-net.c: In function ‘ib_net_setup’:
/Data/Downloads/ibdriver-1.2.9/ib-net.c:303: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
/Data/Downloads/ibdriver-1.2.9/ib-net.c:342:50: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/Data/Downloads/ibdriver-1.2.9/ib-net.c: In function ‘ib_net_register’:
/Data/Downloads/ibdriver-1.2.9/ib-net.c:342: error: ‘INIT_WORK’ undeclared (first use in this function)
/Data/Downloads/ibdriver-1.2.9/ib-net.c:342: error: (Each undeclared identifier is reported only once
/Data/Downloads/ibdriver-1.2.9/ib-net.c:342: error: for each function it appears in.)
make[2]: *** [/Data/Downloads/ibdriver-1.2.9/ib-net.o] Error 1
make[1]: *** [_module_/Data/Downloads/ibdriver-1.2.9] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2
root@hostname:/Data/Downloads/ibdriver-1.2.9# 

I realise that this is a new OS release and I may have to wait for a solution.

Cheers,

Dave.

---

### Post by damies on 2007-10-19
Hi Again,

my mistake, it works as documented in this thread when i use the  	ibdriver-1.3.2-linux-2.6.20.tar.gz  driver.

All working, Thanks Skrewdriver, this thread has helped me twice (7.04 & 7.10) awesome work!

NB. I am using the portable USB modem not the desktop or PCMCIA modem.

Dave.

---

### Post by Skrewdriver on 2007-10-20
Hi Dave,

I've compiled the drivers on Gutsy with no problems. Tested on PCMCIA, not USB.
It appears you have downloaded the wrong version of the driver. Go back to Sourceforge and download the file called "ibdriver-1.3.2-linux-2.6.20.tar.gz", extract it then have a crack at compiling. This should work for you.

---

### Post by Skrewdriver on 2007-10-20
oops. I must learn to read to the end of the thread before posting! Good to see you sorted it out, thanks for the pat on the back.

---

### Post by damies on 2007-10-20
Great to hear you had success with the PCMCIA model.

For the sake of other readers, has anyone had success with the desktop model as this is the only model not tested under Ubuntu 7.10 now.

Dave.

---

