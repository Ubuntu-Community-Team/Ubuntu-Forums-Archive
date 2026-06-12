---
title: "HOWTO fix rt2500 in Hardy (bug #190515)"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by aykito on 2008-05-06
I installed Ubuntu 8.04 and the wireless connection was working but extremely slow.
After a lot of time looking for information and solving problems (including the deactivation of IPv6) I ended up in the [bug #190515](https://bugs.launchpad.net/bugs/190515)

I succeeded in installing working drivers and I have again fast internet.

Thanks a lot mainly to **SirYes** for his answers, it was the basis for this solution and most of the text below is coming from him.

I would suggest you to do a local copy of this procedure (and the links content at the very end), so in case you dont have internet it'll be still fixable ;-)

Here's the procedure I followed to make it work:
 
0. Open a console and enter in root mode:
```
sudo -i
```
    [enter your password if requested]
 
1. Install build-essential package
```
apt-get install build-essential
apt-get install linux-headers
apt-get install module-assistant
```
    run module assistant:
```
module-assistant
```
    select "Configure the system to compile modules" and press ok
 
NOTE: I think installing module-assistant and selectig the option "Configure the system to compile modules" all the previous steps are done as well, but its just what I did...
 
2. Go and download the "Last beta release" of the rt2500 (PCI/PCMCIA) from [serialmonkey]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads")
[COLOR="Red"]UPDATE: Is better installing the lastest CVS version of the serialmonkey drivers, instead of the latest beta version. For some people the beta version is not compiling, I don't know why.
The last version is the [serialmonkey download section]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads"), under [CVS hourly tarball: rt2500-CVS]("http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz")
[/COLOR]  
  Remember to save the file in your home directory! (see step 3.2)
 
3. 
  3.1. Create a temporary working dir:
```
mkdir /root/source
cd /root/source
```
  3.2. Unpack the downloaded source code (I will assume here that the file
       is named rt2500-1.1.0-b4.tar.gz and is placed in your home directory):
```
tar xvzf /home/yourlogin/rt2500-1.1.0-b4.tar.gz
```
4. This step has to be done only once: open the following file in editor:
  4.1. 
```
gedit /etc/modprobe.d/blacklist
```
  4.2. At the end of this file add the following lines, then save the file:
```
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2500pci
```
5. The following steps are required every time new kernel is installed, because
  the driver (module in Linux terminology) will be available only for kernels
  against which it would be compiled:
  5.1. ```
cd /root/source/rt2500-1.1.0-b4/Module
```
  5.2. ```
make clean ; make ; make install
```
  5.3. Make the kernel use your preferred modules:
       ```
dpkg-reconfigure usplash
```
       (usplash here is another story, but the above command generates initial
       ramdisk used at boot time, and puts all modules in it - as required)

  5.4. Reboot your system so the old modules will not be used, but
       instead only the freshly compiled rt2500 module.
       
6.A If the Network Monitor is not working, you'll have to configure the
  connection manually.
  Open the System > Administration > Network or left-click on the
  Network Manager icon and select 'Manual configuration'.
  Unlock the configuration window using your password.
  Open the properties window of your wireless network interface.
  First disable the roaming mode. Then provide all the details you need,
  typically it's enough to select 'Automatic configuration (DHCP)', type
  in the ESSID and a key.
  Close the properties window and make sure the connection box is
  'checked', so it's automatically started upon system boot.

6.B If your connection still doesn't work, you can also edit relevant file manually:

   6.B.0 edit the interfaces file
    ```
sudo gedit /etc/network/interfaces
```
   6.B.1 Append these lines:
```

auto ra0
 
iface ra0 inet dhcp
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid "******"
pre-up iwconfig ra0 mode Managed
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="*********"
pre-up ifconfig ra0 up

```
  6.2 Substitue the ***** by your ESSID and Pre Shared Key

  6.3 save

  6.4. Restart the networking service and hope for the best. This has

   the additional benefit that you'll be able to watch exact progress and
   see what happens:
```
sudo /etc/init.d/networking restart
```
Should something go wrong and you didn't have even the flaky and slow
old net connection, remove the lines you added in
/etc/modprobe.d/blacklist at step 4.2, regenerate initrd using the command 
from step 5.3 and reboot.

 
[B]Remember (now here's the catch) to repeat all steps from point 5 after
your Ubuntu upgrades its kernel. Otherwise the new kernel will not use
the blacklisted modules *AND* will not contain the compiled rt2500
module as well. You can guess what would be the result :-)[/B]
 
 
More information:
 
compile the latest drivers and edit the /etc/network/interfaces
    [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500")
 
edit the /etc/network/interfaces
    [http://ubuntuforums.org/showthread.php?t=241565]("http://ubuntuforums.org/showthread.php?t=241565")

---

### Post by samadhi on 2008-05-08
I followed your instructions closely, but I got this:

```
root@sushi:~/source/rt2500-1.1.0-b4/Module# make clean ; make ; make install
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /root/source/rt2500-1.1.0-b4/Module/rtmp_main.o
In file included from /root/source/rt2500-1.1.0-b4/Module/rtmp_main.c:50:
/root/source/rt2500-1.1.0-b4/Module/rt_config.h:58:40: error: linux/config.h: No such file or directory
/root/source/rt2500-1.1.0-b4/Module/rtmp_main.c: In function &#8216;RT2500_probe&#8217;:
/root/source/rt2500-1.1.0-b4/Module/rtmp_main.c:203: error: implicit declaration of function &#8216;SET_MODULE_OWNER&#8217;
/root/source/rt2500-1.1.0-b4/Module/rtmp_main.c: In function &#8216;RT2500_open&#8217;:
/root/source/rt2500-1.1.0-b4/Module/rtmp_main.c:343: error: &#8216;SA_SHIRQ&#8217; undeclared (first use in this function)
/root/source/rt2500-1.1.0-b4/Module/rtmp_main.c:343: error: (Each undeclared identifier is reported only once
/root/source/rt2500-1.1.0-b4/Module/rtmp_main.c:343: error: for each function it appears in.)
/root/source/rt2500-1.1.0-b4/Module/rtmp_main.c:343: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
/root/source/rt2500-1.1.0-b4/Module/rtmp_main.c: In function &#8216;rt2500_init_module&#8217;:
/root/source/rt2500-1.1.0-b4/Module/rtmp_main.c:1009: error: implicit declaration of function &#8216;pci_module_init&#8217;
make[2]: *** [/root/source/rt2500-1.1.0-b4/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/root/source/rt2500-1.1.0-b4/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
rt2500.ko failed to build!
make: *** [module] Error 1
echo "2.6 module install"
2.6 module install
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/root/source/rt2500-1.1.0-b4/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  DEPMOD  2.6.24-16-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
/sbin/depmod -a
grep: /etc/modprobe.conf: No such file or directory
append 'alias ra0 rt2500' to /etc/modprobe.conf

```

Edit 1: Note that even after symlinking config.h to autoconf.h, errors exist.

Edit 2: Current CVS tarball works, stay tuned for results after reboot.

---

### Post by counter-strike_Bum on 2008-05-08
> **samadhi said:**
> I followed your instructions closely, but I got this:

```
root@sushi:~/source/rt2500-1.1.0-b4/Module# make clean ; make ; make install
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /root/source/rt2500-1.1.0-b4/Module/rtmp_main.o
In file included from /root/source/rt2500-1.1.0-b4/Module/rtmp_main.c:50:
/root/source/rt2500-1.1.0-b4/Module/rt_config.h:58:40: error: linux/config.h: No such file or directory
/root/source/rt2500-1.1.0-b4/Module/rtmp_main.c: In function ‘RT2500_probe’:
/root/source/rt2500-1.1.0-b4/Module/rtmp_main.c:203: error: implicit declaration of function ‘SET_MODULE_OWNER’
/root/source/rt2500-1.1.0-b4/Module/rtmp_main.c: In function ‘RT2500_open’:
/root/source/rt2500-1.1.0-b4/Module/rtmp_main.c:343: error: ‘SA_SHIRQ’ undeclared (first use in this function)
/root/source/rt2500-1.1.0-b4/Module/rtmp_main.c:343: error: (Each undeclared identifier is reported only once
/root/source/rt2500-1.1.0-b4/Module/rtmp_main.c:343: error: for each function it appears in.)
/root/source/rt2500-1.1.0-b4/Module/rtmp_main.c:343: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/root/source/rt2500-1.1.0-b4/Module/rtmp_main.c: In function ‘rt2500_init_module’:
/root/source/rt2500-1.1.0-b4/Module/rtmp_main.c:1009: error: implicit declaration of function ‘pci_module_init’
make[2]: *** [/root/source/rt2500-1.1.0-b4/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/root/source/rt2500-1.1.0-b4/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
rt2500.ko failed to build!
make: *** [module] Error 1
echo "2.6 module install"
2.6 module install
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/root/source/rt2500-1.1.0-b4/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  DEPMOD  2.6.24-16-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
/sbin/depmod -a
grep: /etc/modprobe.conf: No such file or directory
append 'alias ra0 rt2500' to /etc/modprobe.conf

```

Edit 1: Note that even after symlinking config.h to autoconf.h, errors exist.

Edit 2: Current CVS tarball works, stay tuned for results after reboot.

I have the same error, and am having trouble making the CVS tarball to work, when i try to 'make clean ; make ; make install' (for the CVS tarball) it says 'no rule to make target". Help?

---

### Post by aykito on 2008-05-14
Hi, I would try the lastest CVS version of the serialmonkey drivers, instead of the latest beta version. For some people the beta version is not compiling, I don't know why.

The last version is the [serialmonkey download section]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads"), under [CVS hourly tarball: rt2500-CVS]("http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz")

The problems with the headers is in theory solved:
- installing the build-essential and module-assistant packages
- executing the module-assistant application (running "Configure the system to compile modules" from the GUI)
... as described in the procedure, but I know some people had anyway that problem, trying to compile the last beta relase.

Conclussion: try the CVS hourly tarball. If somehow the last CVS version is broken, I can send you the gz I used for me.

Greetings!

---

### Post by xombie on 2008-05-14
The beta version of the serialmonkey drivers more than likely only compile against the latest kernel release. The beta version is IVD's development tree. This version uses the kernel's cfg80211 and mac80211 modules which are still developing and their headers and API change from release to release. By kernel .26 release hopefully they will be stable.

The daily cvs version is the original ralink code updated with bug fixes. It should compile against any kernel as it is a self contained driver. While it functions well it does not work with network manager so manual configuration is a must.

In 8.04 with the stock driver I just do 'sudo iwconfig wlan0 rate 11M' in a terminal after a boot and this sets the uplink rate at 11M instead of the 1M that is set by default. For some setting it to 54M worked. A speed test on my machine show the same performance using this technique as using the legacy drivers.

---

### Post by SINternet on 2008-05-15
Hi All,

I had the same issue and eventually loaded up the SerialMonkey Drivers. During this I had been adding/making changes to my sysctl.conf and rc.local file. I was able to get a faster throughput but not what I was seeing in Windows. THEN I ran into a problem while loading/compiling some software to the point where I had to reload my system but I made backups of my sysctl.conf and rc.local file. After reloading Ubuntu I installed my backup files and VIOLA, my Internet Speed was the same as how it was under Windows. I will post the contents of my files tonight.

---

### Post by aykito on 2008-05-16
Well I have to say I was very disappointed with Ubuntu because of this WLAN isue (and some other I had to address).
Nevertheless once it is solved, I have to admit (after 4 years running windows in the same hardware) it has NEVER been so fast and stable as now, with Ubuntu and the serialmonkey drivers.
I did a internet speed test right after the problem was fixed and it was the first time I had slighly more speed than the contracted (6000 mbps) with my ISP.

---

### Post by SINternet on 2008-05-16
I have the dreaded rt2500 card WMP54G. 

After a fresh install I applied these files only and got the Internet Speed out of my system I was used to seeing with Windows.

Paste applicable contents from each file.

My additions to the sysctl.conf

To open for editing "sudo gedit /etc/sysctl.conf"

#increase TCP maximum buffer size
net.core.rmem_max = 16777216
net.core.wmem_max = 16777216

# increase linux autotuning TCP buffer limits
net.ipv4.tcp_rmem = 4096 87380 16777216
net.ipv4.tcp_wmem = 4096 65536 16777216

# don't cache ssthresh from previous connection
net.ipv4.tcp_no_metrics_save = 1

# recommended to increase this for 1000 BT or higher
net.core.netdev_max_backlog = 2500
net.ipv4.tcp_timestamps=0
net.ipv4.tcp_moderate_rcvbuf=0
net.ipv4.tcp_window_scaling=0

to apply immediately after editing "sudo sysctl -p"

Good source of info here. [http://www-didc.lbl.gov/TCP-tuning/TCP-tuning.html](http://www-didc.lbl.gov/TCP-tuning/TCP-tuning.html)


Nice Info here.......[http://www.extremetech.com/article2/...2114124,00.asp](http://www.extremetech.com/article2/...2114124,00.asp)

Info on sysctl.conf parameters..[http://frankmash.blogspot.com/2005/1...imization.html](http://frankmash.blogspot.com/2005/1...imization.html)

check your parameters by dumping the sysctl info to a file.
sudo sysctl -A > ~/Desktop/sysctl_settings

rc.local has some redundancy to syctl.conf

paste before the exit 0 at the bottom

/sbin/iwconfig wlan0 rate 11M

echo 256960 > /proc/sys/net/core/rmem_default
echo 256960 > /proc/sys/net/core/rmem_max
echo 256960 > /proc/sys/net/core/wmem_default
echo 256960 > /proc/sys/net/core/wmem_max

echo 0 > /proc/sys/net/ipv4/tcp_timestamps 
echo 1 > /proc/sys/net/ipv4/tcp_sack 
echo 1 > /proc/sys/net/ipv4/tcp_window_scaling

"11M" worked fine for my connection. Play with that rate till you find your sweet spot (because not every place has the same basic speed nor does everyone pay for more speed like Business Class)

Most people say make a backup of the original but I say make a backup of your edited file as well!

SIN

---

### Post by Hayesio on 2008-05-18
Thanks aykito.  I have the rt2500 chip set and the card was broken when i upgraded to Hardy.  I followed your instructions step 1 to 5.4.  Problem solved:)

Cheers!

---

### Post by pjman on 2008-05-19
My network speed is back to normal now.

Thank you!

---

### Post by HoellP on 2008-05-31
Hi
I followed the tutorial, but I still got problems with the cvs driver.
It installed in the wrong directory, but after I copied it over manually it loads correctly. I can even scan for my ap. But when I try to establish a connection, I only get 
```
Listening on LPF/wlan0/00:0d:f0:1b:8a:35
Sending on   LPF/wlan0/00:0d:f0:1b:8a:35
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]

```
No connection at all.
```
lsmod |grep rt
rt2500                180704  1 
exportfs                6016  1 nfsd
parport_pc             36260  0 

dmesg
<nothing>

modinfo rt2500
filename:       /lib/modules/2.6.24-17-generic/extra/rt2500.ko
license:        GPL
description:    Ralink RT2500 802.11g WLAN driver 1.1.0 CVS 2008053108
author:         http://rt2x00.serialmonkey.com
srcversion:     DBA270178059CA932E313AE
alias:          pci:v00001814d00000201sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.24.3 SMP mod_unload 586 
parm:           debug:Debug mask: n selects filter, 0 for none (int)
parm:           ifname:Network device name (default ra%d) (charp)


```

Any ideas what I could try?

Thanks

PS: I tried static IP as well, but no change.

---

### Post by LostAndFound on 2008-06-05
Hi and thanks for your instructions which solved the problem for me. I did have one glitch which I thought I'd point out in case it helps someone else out:

With Kernel 2.6.24-18-generic (on AMD64) I had to manually copy the module from:

/root/source/rt2500-cvs-2008060501/
to:
/lib/modules/2.6.24-18-generic/kernel/drivers/net/wireless/

I don't know why the built module didn't get placed here - it contained a version of rt2500.ko from an unsucessfully attempt to install the module the night before using method to install from [https://bugs.launchpad.net/ubuntu/+source/rt2500/+bug/183818](https://bugs.launchpad.net/ubuntu/+source/rt2500/+bug/183818), which gave a message to the tune of: invalid module format.

I also had problems when I first tried copying rt2500.ko to:
/lib/modules/2.6.24-18-generic/kernel/net/wireless
which was not the correct location.

Good luck! - and thanks again for the help provided in this post.

---

### Post by wyley.r on 2008-06-18
I have been using the Serialmonkey driver for the RaLink RT2500 card (lspci output: "00:09.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)") for about six months with no problems.  Since upgrading to Hardy, however, the driver has behaved strangely.  The rt2500 module apparently is deleted, or otherwise disappears, so that 
```

$ sudo modprobe rt2500

``` 
reports that it can no longer find the module.  This typically happens after a reboot -- but not predictably.

After re-installing via
```

$ sudo make install

```
the card works fine.

Does anyone know what changes there have been in Hardy that could produce this behavior?  Why would my locally-compiled version disappear at random?

Thanks!

---

### Post by Mikecore on 2008-06-22
First I would like to thank you for providing me the solution to fix my rt2500pci "slow connection". As I was looking into the problem I found I was able to manually set the rate for my Linksys 802.11g card. And my slow connection went away. I guess I have a little different take on how to fix the issue. Instead of compiling a new driver just have the rate set before the card comes up. that does three things 1) you don't have to compile a new driver. 2) you don't have to compile the driver after every kernel upgrade. 3) its much faster to just add the lines   

```

nano /etc/network/interfaces
and then add

pre-up ifconfig wlan1 down
pre-up iwconfig wlan1 essid "******" channel 11 rate 54M
pre-up ifconfig wlan1 up


```

worked really nice again thanks

---

### Post by sixgun on 2008-07-15
When trying to run make, if you receive erros, such as "**no rule to make target**" or "**make: *** /lib/modules/2.6.24-19-generic/build: No such file or directory.  Stop**", you may need to create a symlink pointing to the appropriate header files. Paste and run the following code, and then try to run make.
```
ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build
```

---

### Post by jackcy on 2008-07-25
I had the same problem. I could manually change the wireless speed to 54M but after a reboot the connection only had 1M.

Thanks to SINternet I only added one line to the file /etc/rc.local before the exit 0:

/sbin/iwconfig wlan0 rate 54M

After a reboot the connection speed automatically was set to 54M.

---

### Post by Drengur on 2008-07-26
This does not seem to work for me. I had a flaky connection with the original driver. Now I do not seem to be able to receive DHCP offers from the router.

iwconfig seems to sometimes show me connected to the right router. However I receive no DHCP offers.

Most of the times the ESSID in iwconfig is just empty. 

iwlist ra0 scanning provides me with two cells. One of which is the correct one. This tells me the wireless card works in some way.

And following these instructions I have had no luck reverting to the old driver.

I hope for a reply soon.

With regards,
Drengur

---

### Post by Drengur on 2008-07-26
Strike my last. I fiddled around with rmmod and modprobe and managed to get the old driver to work again. I followed jackcy's instructions and the connection is great and the applet works.

In my case the solution presented by parent is unnecessary, and does more harm than good, though this might not be the case with others.

Thanks jackcy

---

### Post by Bert Mariën on 2008-08-19
Have the same problem since Hardy. 
I didn't try this solution  (yet).

But in the mean time I can fix the bug till the next reboot with:

iwconfig wlan0 rate 54M fixed 

Pity it just last till reboot.

---

### Post by noname4444 on 2008-09-09
> **jackcy said:**
> I had the same problem. I could manually change the wireless speed to 54M but after a reboot the connection only had 1M.

Thanks to SINternet I only added one line to the file /etc/rc.local before the exit 0:

/sbin/iwconfig wlan0 rate 54M

After a reboot the connection speed automatically was set to 54M.

Thank you so much.   A single line added to that file fixed my internet speed!!!

I was afraid I was going to have to put windows back on there for a little bit...

---

### Post by cpbotha on 2009-08-29
On my setup, the iwconfig wlan0 54M (or 11M) only works temporarily.  I'm not talking about rebooting (I integrated the necessary invocation with my /etc/network/interfaces), but purely as a function of time spent connected.  After a while, speed drops back down to a miserable 70kbytes/s.  No amount of iwconfig wlan0 54M (or 11M) can then fix it.

I've now built and installed the legacy rt2500 drivers from the last daily CVS tarball: [http://sourceforge.net/projects/rt2400/files/Final%20software%20release/rt2500-legacy-final-cvs/rt2500-cvs-daily.tar.gz/download](http://sourceforge.net/projects/rt2400/files/Final%20software%20release/rt2500-legacy-final-cvs/rt2500-cvs-daily.tar.gz/download) following the instructions in the initial post.

Things seem to be stable, I'll report back if I find otherwise.

---

### Post by mrblonde1369 on 2009-10-06
many thanks aykito, i've followed your very simple steps and now my ralink card works like a charm!!

---

### Post by foxy123 on 2009-10-06
I am trying to follow it on Karmic and got this:
```
:~/Downloads/rt2500-cvs-2009041204/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-12-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-12-generic'
rt2500.ko failed to build!
make: *** [module] Error 1

```

---

### Post by aykito on 2009-10-08
Hi Foxy123,
this bug is supposedly repaired in linux-backports-modules-2.6.28 so in theory you dont need to recompile the drivers again, check the [bug documentation]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190515?comments=all")

---

### Post by foxy123 on 2009-10-08
It is still a problem in Karmic. I will reopen the bug.

---

### Post by moulsonp on 2009-10-13
I also see poor performance with the rt2500pci drivers, and no better after installing the backports package:

```
paul@locke:~/downloads/rt2500-cvs-2009041204/Module$ dpkg -l |grep backport
ii  linux-backports-modules-2.6.31-13-generic  2.6.31-13.15                                                Ubuntu supplied Linux modules for version 2.6.
ii  linux-backports-modules-karmic             2.6.31.13.24                                                Generic Linux backported drivers.
ii  linux-backports-modules-karmic-generic     2.6.31.13.24                                                Backported drivers for generic kernel image

```

More importantly, I'm also struggling to build the rt2500 module:

```
paul@locke:~/downloads/rt2500-cvs-2009041204/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-13-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-13-generic'
rt2500.ko failed to build!
make: *** [module] Error 1
paul@locke:~/downloads/rt2500-cvs-2009041204/Module$ 

```

Has anyone got the old rt2500 module to build on a 2.6.31 kernel?

---

### Post by foxy123 on 2009-10-14
> **moulsonp said:**
> I also see poor performance with the rt2500pci drivers, and no better after installing the backports package:

```
paul@locke:~/downloads/rt2500-cvs-2009041204/Module$ dpkg -l |grep backport
ii  linux-backports-modules-2.6.31-13-generic  2.6.31-13.15                                                Ubuntu supplied Linux modules for version 2.6.
ii  linux-backports-modules-karmic             2.6.31.13.24                                                Generic Linux backported drivers.
ii  linux-backports-modules-karmic-generic     2.6.31.13.24                                                Backported drivers for generic kernel image

```

More importantly, I'm also struggling to build the rt2500 module:

```
paul@locke:~/downloads/rt2500-cvs-2009041204/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-13-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-13-generic'
rt2500.ko failed to build!
make: *** [module] Error 1
paul@locke:~/downloads/rt2500-cvs-2009041204/Module$ 

```

Has anyone got the old rt2500 module to build on a 2.6.31 kernel?

no, I cannot.

---

### Post by foxy123 on 2009-10-15
I wonder if anyone tried to compile 2.6.32 kernel as the fix is supposed to be there?

---

