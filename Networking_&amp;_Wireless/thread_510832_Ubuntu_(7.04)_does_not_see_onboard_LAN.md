---
title: "Ubuntu (7.04) does not see onboard LAN"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by dugb on 2007-07-27
I have purchased a new PC with no OS and have installed 7.04. During installation the system said it could not find any LAN hardware (my MB has onboard LAN - Asus P5GC-MX and BIOS is set to LAN enabled). I am unable to get the OS to recognise the onboard LAN (the PC is connected to a working ADSL Modem/Router but no light appears for this PC on the modem). I have followed the basic steps from Ubuntu documentation in connecting ADSL by using "sudo pppoeconf"...this failed and asked me if I wanted to run a program called "...mod..." something (sorry, I am not at home at the moment and this is from memory). I chose to run this program and it replied with "it is not installed". I have the MB's CD and it contains LAN>Linux>Drivers. How do I install these drivers if this is the problem?

:confused:

---

### Post by DC@DR on 2007-07-27
I don't have Asus Mainboard so I have no idea about your problem, but a quick search in these forums gave this link: [http://ubuntuforums.org/showthread.php?t=419727&highlight=ASUS+Lan+driver](http://ubuntuforums.org/showthread.php?t=419727&highlight=ASUS+Lan+driver), take a look and see if it helps :-)

---

### Post by PaulFr on 2007-07-27
**See [http://ubuntuforums.org/showthread.php?p=2790439](http://ubuntuforums.org/showthread.php?p=2790439) for a post regarding the same problem.**

The problem is that your Attansic L2 network card is not recognized - however, the good news is that Attansic have released the Linux version of the driver (see **[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/77725](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/77725)** and especially the last comment in that page).

But this implies you require to compile the driver and install it (if you need it now and cannot wait).

Are you up for some driver compilation ? If yes, here are the commands to execute (please copy and paste **a single line** at a time) in a terminal:```
sudo apt-get update
sudo apt-get install rar wget bzip2
sudo apt-get install kernel-devel build-essential linux-headers-`uname -r`
mkdir -p ~/dev; cd ~/dev
wget http://launchpadlibrarian.net/7382416/L2-linux-driver_new.rar
mkdir -p ~/dev/atl2; cd ~/dev/atl2
unrar x ~/dev/L2*_new.rar
cd ~/dev/atl2/src
sudo make install
sudo insmod /lib/modules/`uname -r`/kernel/drivers/net/atl2.ko
```For any confirmation question, please answer Y or y. If any error occurs, please cut and paste error messages here. If everything went well, you should now see your interface in Network Manager (and hopefully be connected if DHCP is being used).

If everything seems good, please run the following command in the terminal ```
sudo echo "atl2" >> /etc/modules
```. Please verify on reboot, that your network still works. *If it does not work, you can use the last command in the first set, ```
sudo insmod /lib/modules/`uname -r`/kernel/drivers/net/atl2.ko
``` to install the atl2 module again.*

Side question to those in the know: Do we need a /etc/modprobe.d file as well ?

---

### Post by dugb on 2007-07-27
Thanks for your reply and effort.

I tried as you said (except for 'cut & paste' since I am reading this on a different PC so it is a manual type).

Here are the errors:

sudo apt-get update - E Some index files failed to download, they have been ignored, or old ones used instead.
sudo apt-get install rar wget bzip2 - E Couldn't find package rar
sudo apt-get install kernel-devel build-essential linux-headers-`uname -r` - E Couldn't find package kernel-devel

after the above the command line had:- user@machinename:~/dev$ to which I then typed your next command

wget [http://launchpadlibrarian.net/7382416/L2-linux-driver_new.rar](http://launchpadlibrarian.net/7382416/L2-linux-driver_new.rar) - E Resolving launchpadlibrarian.net...failed: Name or service not known

Since I have had an error every command I have not gone any further. Can you still help me?

---

### Post by PaulFr on 2007-07-27
Sorry, some basics out of the way:

1. While you do not have the LAN connected, I presume you do have a connection working (wireless?). Your errors seem to indicate you do not have such a connection. If not this gets more interesting :-)

2. What version of Ubuntu are you using ? I assumed Feisty, and that you have a GUI. If not, stop and ask for help again with that version identified.:q

3. If you are writing this down and typing by hand, please make sure that the quotes around **uname -r** are back-ticks (or grave accents) not the regular quotes :-)

4. **If you do not have a network**, and cannot compile it yourself, you may consider the attachment I have added to this post - I compiled it for you (my kernel version is 2.6.20-16-generic) If you are considering this,

1. please download the 300 kb **atl2.tar** file attachment on some other machine,
2. transfer using stick or other means to your Ubuntu machine, and
3. copy it to your Desktop, and
4. run the following (this is from the Makefile other than the first line and the sudo prefixes)```
mkdir -p ~/dev
mv ~/Desktop/atl2.tar ~/dev
cd ~/dev
tar xvf ~/dev/atl2.tar
gunzip atl2.ko.gz
sudo find /lib/modules/`uname -r` -name "atl2.ko" -exec rm -f {} \;
sudo find /lib/modules/`uname -r` -name "atl2.ko.gz" -exec rm -f {} \;
sudo install -D -m 644 atl2.ko /lib/modules/`uname -r`/kernel/drivers/net/atl2/atl2.ko
sudo /sbin/depmod -a
sudo install -D -m 644 atl2.7.gz /usr/share/man/man7/atl2.7.gz
sudo insmod /lib/modules/`uname -r`/kernel/drivers/net/atl2.ko
``` The last line is the last line in the first block of my earlier instructions (see **insmod** command), now verify your network is working. If yes, continue with my previous instructions.

If you have booting problems, please boot using recovery entry in boot menu and then issue the commands ```
sudo rmmod /lib/modules/`uname -r`/kernel/drivers/net/atl2.ko
sudo find /lib/modules/`uname -r` -name "atl2.ko" -exec rm -f {} \;
sudo find /lib/modules/`uname -r` -name "atl2.ko.gz" -exec rm -f {} \;
``` and **reboot**

Good luck !

Note:
1. Once the network is working, please follow my earlier instructions - i.e. download everything and compile it yourself - that way you can be sure the driver matches your kernel version, etc.

2. To get rar (if you are following my original instructions), there is 'rar' in the archives, but for that you need to enable the multiverse repository. To do that, go to System -> Administration -> Software Sources and make sure all the options are checked (especially the restricted one) in the "Downloadable from the Internet" options. For details, see Adding Universe and Multiverse section in **[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)**.

---

### Post by dugb on 2007-07-28
Hi there and thanks for your continued assistance.

I only have a wired network, hence I need the onboard LAN to work (but I have other working PC's successfully connected to the net). Also, I confirm I have Feisty Fawn 7.04, kernel version 2.6.20-15-generic. Good point about the 'grave stroke' too...very useful for me :).

I have followed your instructions, all seemed to go well until the last commond, the "insmod command"; the response I got back is:

 insmod: can't read '/lib/modules/`uname -r`/kernel/drivers/net/atl2.ko' No such file or directory

Does this mean I didn't create a file correctly, or didn't reach the right directory?

I am prepared to keep trying as long as you are prepared to keep assisting...again thanks.

---

### Post by dugb on 2007-07-28
Hi PaulFr...:)...I rebooted a little while later and I saw the light on my modem/router light up....:)...I am now online and updating using the Update Manager.

:)...I am rather happy now...I realised with Linux there would be a learning curve and I am glad there are people like you to assist.

I noted you said I should still follow the steps from your first post...is that necessary now?...since you know my kernel version?...or is it safe to leave as is.


Ooooops...I spoke too soon...the light on the router is lit, but I now have no internet connection. My kernel version has changed to 2.6.20-16-generic. Did the updating blow away the changes we made?...do I need to run the steps again? :confused:

Edit: This is weird, the router light is still lit for this port even though the PC is now shut down. Also, the light is on, the PC says it cannot find a working Ethernet card and the router admin controller does not see this PC. I have now rebooted the router and the light for the Linux PC comes back on, but that PC is shut down.

Edit: I have turned the PC power off and the router light goes off; I turn the PC power switch back on and the router light does not come back on. I boot the PC and there is no network light or connection.

---

### Post by PaulFr on 2007-07-28
Good to hear your network finally came to life - and glad to be of help :)

1. My insmod command was erroneous - The **install** command above that was to **/lib/modules/`uname -r`/kernel/drivers/net/atl2/atl2.ko** - note the **net/atl2/atl2.ko** at the end. But the **insmod** referenced the file as **/lib/modules/`uname -r`/kernel/drivers/net/atl2.ko** - note the **net/atl2.ko** at the end. My mistake :-(

2. Unfortunately, each version of the Linux kernel has its own /lib/modules directory as you can see if you run the command ```
ls /lib/modules
```. You have to wait until this driver becomes part of the Ubuntu release, then you do not need to worry about this.

3. But the commands to install it become simpler, since you already have the module on your hard disk somewhere, and you only have to copy it to the right place (by the way the **`uname -r`** command gives you the version of the kernel you have booted).

So this is what you have to do everytime your kernel version changes AND your network goes out (i.e. your driver is not already released with the new version):

---------------

4.1 If you have already downloaded and un'rar'ed the driver source .rar file I gave a link for in the initial instructions, you could just run ```
cd ~/dev/atl2/src
sudo make install
sudo insmod /lib/modules/`uname -r`/kernel/drivers/net/atl2/atl2.ko
```

4.2 If you have not downloaded the source .rar file and only have my compiled driver file (from the tar file):```
cd ~/dev
sudo find /lib/modules/`uname -r` -name "atl2.ko" -exec rm -f {} \;
sudo find /lib/modules/`uname -r` -name "atl2.ko.gz" -exec rm -f {} \;
sudo install -D -m 644 atl2.ko /lib/modules/`uname -r`/kernel/drivers/net/atl2/atl2.ko
sudo /sbin/depmod -a
sudo insmod /lib/modules/`uname -r`/kernel/drivers/net/atl2/atl2.ko
``` I have removed the man page installation since that is not critical for you.

---------------

Even if you do not have your kernel version change, you should run the following command (as I had indicated earlier) to make sure you have your network each time you boot:```
sudo echo "atl2" >> /etc/modules
``` Of course, please do NOT do it if you have done it earlier. To see if that is the case, you could run```
grep -n atl2 /etc/modules
``` and see if you get some output like > 9:atl2 9 is the line number here and could be different for you. If such output is there (note carefully that there is not **#** at the beginning just after the colon ( : ); # is the comment character), you already have it in your /etc/modules and do not need to add it again.

---

### Post by dugb on 2007-07-29
Hi and again thanks...:)

The PC is networked and up and running now.

I appreciate your time and effort and all the trouble you went to in researching my problem and then supplying me with all those command lines. Hopefully I wont have to return here because the network connection failed again.

All the best PaulFr

---

### Post by sudiono on 2007-07-29
hi,i trying to install feisty on my computer with specification like this p5gc-mx (sound,display and lan are onboard),1 gb ram,samsung cdrw and 80gb seagate(sata),i'm using the live cd <7.04>but there is trouble when the first time computer booting from the cd,it has error like this
ata1:failed to recover some devices,retrying in 5secs, after a few minutes display come out and i click the install button  and using manual partition option ,but again there is trouble with the procces in the formatting the file sytems it shows 5 % ,i wait until  1 hour it still show 5 % :confused:
it already been 4 days i'm trying this,helppp
sorry for mybad english

---

### Post by splintercellguy on 2007-07-30
Please start a new thread. Have you tried alternate installer CD?

---

### Post by jdelcom on 2007-07-30
Sorry for the repost (in thread [http://ubuntuforums.org/showthread.php?p=2790439](http://ubuntuforums.org/showthread.php?p=2790439)), but I didn't get reply there.

Hello. I have the same problem. I have a new desktop with Asus P5GC MX.
I tried with this driver and another given in other thread, and with both I get this reply:

insmod: error inserting 'lib..../atl2.ko': -1 Invalid module format

when I try with the src given by the mother drivers CD I get

Makefile 101: ***Linux kernel source not configured - missing config.h. Alto.

What else can I try? Without lan and internet, my desktop is worthless

Thanks for any help you can give me.

More detalis: Intel E2160, mobo mentioned, Ubuntu Desktop 64, kernel 2.6.20-15-generic.

---

### Post by PaulFr on 2007-07-30
You are running a 64 bit kernel - I only have a 32 bit kernel so the drivers I compiled and attached in this post will not work for you. I checked the ASUS site for your motherboard, and they do have a download for Linux drivers ([http://support.asus.com/download/download.aspx?SLanguage=en-us](http://support.asus.com/download/download.aspx?SLanguage=en-us)) but the 26.88 MB download has only got the source for the driver. This means you have to compile the driver yourselves.

If you have access to a **64 bit Linux kernel already networked**, (_it does not need need to be the same motherboard as yours, or even the same network card as yours, any 64 bit Ubuntu Feisty system will do_), then you can follow the instructions I posted initially to compile the code:```
sudo apt-get update
sudo apt-get install rar wget bzip2
sudo apt-get install kernel-devel build-essential linux-headers-`uname -r`
mkdir -p ~/dev; cd ~/dev
wget http://launchpadlibrarian.net/7382416/L2-linux-driver_new.rar
mkdir -p ~/dev/atl2; cd ~/dev/atl2
unrar x ~/dev/L2*_new.rar
cd ~/dev/atl2/src
sudo make install
sudo insmod /lib/modules/`uname -r`/kernel/drivers/net/atl2/atl2.ko
``` Otherwise you should ask here for someone with a 64 bit system to compile it for you.
Good luck !

---

### Post by jdelcom on 2007-07-31
Thanks! I'll download the drivers and will try to compile them myself. Hope they have some kind of instructions :D

Will let you guys know how it goes.

I've read somewhere else that the Asus webpage has nothing of the sort, and that's why I didn't even bother looking there  :(

---

### Post by geertjo on 2007-08-03
I had the same problem and followed the steps, but at the insmod statement i get the problem that it is from an invalid format. Then I searched a little bit on the error and it's because it's compiled under a different kernel version. So, what do I have to do to get the insmod statement working?
At some sites they say that you have to use the 'make' function but it isn't yet installed on my server.

---

### Post by geertjo on 2007-08-03
I read the post above and I have the same problem. Can someone please post a compiled module from a 64bit system?

Thanks!

---

### Post by sudiono on 2007-08-03
about my problem,finally  i change my mobo with biostar n my cd -rw with cd -rom.n it works it works smoothly,without any problem,so thx to anyone who already been tried to solve my problem,
thx a lot

---

### Post by PaulFr on 2007-08-03
**jdelcom**, the Linux drivers are hiding under the Other tree node in the downloads for your motherboard at the Asus download site.

**geertjo**, please run ```
uname -a
``` and post your results.
1.  What version of Ubuntu are you running ? I compiled the driver for 32 bit Feisty (7.04).
2. Are you running a 64 bit kernel or a 32 bit kernel ?

---

### Post by firsttiger on 2007-08-04
> **jdelcom said:**
> Thanks! I'll download the drivers and will try to compile them myself. Hope they have some kind of instructions :D

Will let you guys know how it goes.

I've read somewhere else that the Asus webpage has nothing of the sort, and that's why I didn't even bother looking there  :(

Did you have any luck installing the drivers. I'm still struggling with a similar issue. I plugged in an old 10/100 card to get around the problem for now but would love to get my Gigabit card to work for internal transfers.

I am using an Asus P5K-V motherboard. There are apparently unix drivers for it. I found them at [http://dlsvr03.asus.com/pub/ASUS/mb/socket775/P5K/Attansic_L.rar](http://dlsvr03.asus.com/pub/ASUS/mb/socket775/P5K/Attansic_L.rar). I downloaded them and ran the make install command on them but I've got the following errors:

/home/kkang/attansic/Attansic/src/at.h:10:5: warning: "AUTO" is not defined
/home/kkang/attansic/Attansic/src/at.h:82:5: warning: "DBG" is not defined
/home/kkang/attansic/Attansic/src/at_main.c:109: warning: initialization from incompatible pointer type
/home/kkang/attansic/Attansic/src/at_main.c:352:53: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/kkang/attansic/Attansic/src/at_main.c: In function âat_probeâ:

/home/kkang/attansic/Attansic/src/at_main.c:351: error: âINIT_WORKâ undeclared (first use in this function)
/home/kkang/attansic/Attansic/src/at_main.c:351: error: (Each undeclared identifier is reported only once
/home/kkang/attansic/Attansic/src/at_main.c:351: error: for each function it appears in.)
/home/kkang/attansic/Attansic/src/at_main.c:355:51: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/kkang/attansic/Attansic/src/at_main.c:358:53: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/kkang/attansic/Attansic/src/at_main.c: In function âat_upâ:
/home/kkang/attansic/Attansic/src/at_main.c:953: warning: passing argument 2 of ârequest_irqâ from incompatible pointer type
/home/kkang/attansic/Attansic/src/at_main.c: In function âat_rx_checksumâ:
/home/kkang/attansic/Attansic/src/at_main.c:2270: error: âCHECKSUM_HWâ undeclared (first use in this function)
/home/kkang/attansic/Attansic/src/at_main.c: In function âat_tx_csumâ:
/home/kkang/attansic/Attansic/src/at_main.c:2517: error: âCHECKSUM_HWâ undeclared (first use in this function)
make[2]: *** [/home/kkang/attansic/Attansic/src/at_main.o] Error 1
make[1]: *** [_module_/home/kkang/attansic/Attansic/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [default] Error 2

I am a complete noob in Ubuntu. Any help would be greatly appreciated.

---

### Post by PaulFr on 2007-08-05
firsttiger, You are trying to compile the vendor version of Attansic L1 drivers, which is for the 2.6.18 and 2.6.19 versions of the kernel. Please see **[http://atl1.sourceforge.net/](http://atl1.sourceforge.net/)** for a version of the Attansic L1 driver that will work on more recent kernels.

---

### Post by jdelcom on 2007-08-05
I did not have any luck. I ended up installing a 10/100 PCI card just to solve the problem. Nevertheless, I'll reinstall Ubuntu, since I did have lots of small problems with this installation (the LAN driver, the VGA driver -which makes Beryl work very awful), Thunderbird 2.0 is not working, etc etc.

I'll re-install and try to compile the drivers, then will come back here to tell you guys how it went. In the meantime, if you have any new suggestion, I'd love to hear it :D

Thanks!

---

### Post by ks_work on 2007-08-07
I've had same problem with installing Attansic L2 network card driver on 2.6.21-31 kernel. Finally got it working after some fiddling with driver code. 
More details here: [http://ihatecubicle.blogspot.com/2007/08/how-to-install-attansic-l2-network.html](http://ihatecubicle.blogspot.com/2007/08/how-to-install-attansic-l2-network.html)

good luck,
ks

---

### Post by JoanSala on 2008-02-21
> **PaulFr said:**
> Sorry, some basics out of the way:

1. While you do not have the LAN connected, I presume you do have a connection working (wireless?). Your errors seem to indicate you do not have such a connection. If not this gets more interesting :-)

2. What version of Ubuntu are you using ? I assumed Feisty, and that you have a GUI. If not, stop and ask for help again with that version identified.:q

3. If you are writing this down and typing by hand, please make sure that the quotes around **uname -r** are back-ticks (or grave accents) not the regular quotes :-)

4. **If you do not have a network**, and cannot compile it yourself, you may consider the attachment I have added to this post - I compiled it for you (my kernel version is 2.6.20-16-generic) If you are considering this,

1. please download the 300 kb **atl2.tar** file attachment on some other machine,
2. transfer using stick or other means to your Ubuntu machine, and
3. copy it to your Desktop, and
4. run the following (this is from the Makefile other than the first line and the sudo prefixes)```
mkdir -p ~/dev
mv ~/Desktop/atl2.tar ~/dev
cd ~/dev
tar xvf ~/dev/atl2.tar
gunzip atl2.ko.gz
sudo find /lib/modules/`uname -r` -name "atl2.ko" -exec rm -f {} \;
sudo find /lib/modules/`uname -r` -name "atl2.ko.gz" -exec rm -f {} \;
sudo install -D -m 644 atl2.ko /lib/modules/`uname -r`/kernel/drivers/net/atl2/atl2.ko
sudo /sbin/depmod -a
sudo install -D -m 644 atl2.7.gz /usr/share/man/man7/atl2.7.gz
sudo insmod /lib/modules/`uname -r`/kernel/drivers/net/atl2.ko
``` The last line is the last line in the first block of my earlier instructions (see **insmod** command), now verify your network is working. If yes, continue with my previous instructions.

If you have booting problems, please boot using recovery entry in boot menu and then issue the commands ```
sudo rmmod /lib/modules/`uname -r`/kernel/drivers/net/atl2.ko
sudo find /lib/modules/`uname -r` -name "atl2.ko" -exec rm -f {} \;
sudo find /lib/modules/`uname -r` -name "atl2.ko.gz" -exec rm -f {} \;
``` and **reboot**

Good luck !

Note:
1. Once the network is working, please follow my earlier instructions - i.e. download everything and compile it yourself - that way you can be sure the driver matches your kernel version, etc.

2. To get rar (if you are following my original instructions), there is 'rar' in the archives, but for that you need to enable the multiverse repository. To do that, go to System -> Administration -> Software Sources and make sure all the options are checked (especially the restricted one) in the "Downloadable from the Internet" options. For details, see Adding Universe and Multiverse section in **[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)**.

Oh God, Thank You !!!!!!
I had been desperate about that, couldn't find anything, all I was trying was not worth it... but this worked man !! Thanks !! 

Thank you very much ! =D>:grin::grin::grin::biggrin:

---

### Post by dansued on 2008-05-29
> **PaulFr said:**
> Sorry, some basics out of the way:

1. While you do not have the LAN connected, I presume you do have a connection working (wireless?). Your errors seem to indicate you do not have such a connection. If not this gets more interesting :-)

2. What version of Ubuntu are you using ? I assumed Feisty, and that you have a GUI. If not, stop and ask for help again with that version identified.:q

3. If you are writing this down and typing by hand, please make sure that the quotes around **uname -r** are back-ticks (or grave accents) not the regular quotes :-)

4. **If you do not have a network**, and cannot compile it yourself, you may consider the attachment I have added to this post - I compiled it for you (my kernel version is 2.6.20-16-generic) If you are considering this,

1. please download the 300 kb **atl2.tar** file attachment on some other machine,
2. transfer using stick or other means to your Ubuntu machine, and
3. copy it to your Desktop, and
4. run the following (this is from the Makefile other than the first line and the sudo prefixes)```
mkdir -p ~/dev
mv ~/Desktop/atl2.tar ~/dev
cd ~/dev
tar xvf ~/dev/atl2.tar
gunzip atl2.ko.gz
sudo find /lib/modules/`uname -r` -name "atl2.ko" -exec rm -f {} \;
sudo find /lib/modules/`uname -r` -name "atl2.ko.gz" -exec rm -f {} \;
sudo install -D -m 644 atl2.ko /lib/modules/`uname -r`/kernel/drivers/net/atl2/atl2.ko
sudo /sbin/depmod -a
sudo install -D -m 644 atl2.7.gz /usr/share/man/man7/atl2.7.gz
sudo insmod /lib/modules/`uname -r`/kernel/drivers/net/atl2.ko
``` The last line is the last line in the first block of my earlier instructions (see **insmod** command), now verify your network is working. If yes, continue with my previous instructions.

If you have booting problems, please boot using recovery entry in boot menu and then issue the commands ```
sudo rmmod /lib/modules/`uname -r`/kernel/drivers/net/atl2.ko
sudo find /lib/modules/`uname -r` -name "atl2.ko" -exec rm -f {} \;
sudo find /lib/modules/`uname -r` -name "atl2.ko.gz" -exec rm -f {} \;
``` and **reboot**

Good luck !

Note:
1. Once the network is working, please follow my earlier instructions - i.e. download everything and compile it yourself - that way you can be sure the driver matches your kernel version, etc.

2. To get rar (if you are following my original instructions), there is 'rar' in the archives, but for that you need to enable the multiverse repository. To do that, go to System -> Administration -> Software Sources and make sure all the options are checked (especially the restricted one) in the "Downloadable from the Internet" options. For details, see Adding Universe and Multiverse section in **[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)**.
followed this exactly including fixing the last line to point to correct directory. No error messages shown. Still doesn't work.

I want to rule out the possibility of a hardware problem.

lspci shows
01:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)

also, the indicator lights don't light up when I plug in a cable and neither does the light on the router at the other end.

What do you guys think? Hardware problem? software? both?

---

### Post by PaulFr on 2008-05-30
This is how I would proceed:

1. Check that the cable works by plugging into some other system and seeing if the lights come on.
2. Check that the port is correct, by changing the cable on the router end to some other port.

If the cable and the port are good with some other known good system, then the problem is within your Linux box.

---

