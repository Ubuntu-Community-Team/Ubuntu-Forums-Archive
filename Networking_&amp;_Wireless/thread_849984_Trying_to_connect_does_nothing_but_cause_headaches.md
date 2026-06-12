---
title: "Trying to connect does nothing but cause headaches"
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by Omicron Machine on 2008-07-05
Hi there, I´m trying to connect to the internet with my laptop. It works just fine connecting directly, but wireless doesn´t work. The PC connects just fine, the router is set up and all. But the laptop doesn´t detect any wireless networks at all. I´ve tried everything I could find or think of, and nothing has changed anything.

I´ve got Hardy, and my wireless card is Atheros 802.11, and it shows up in the Hardware drivers list, but doesn´t do anything.

Here´s the output of ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:1e:68:75:dd:3e  
          inet addr:72.141.100.160  Bcast:255.255.255.255  Mask:255.255.254.0
          inet6 addr: fe80::21e:68ff:fe75:dd3e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19770 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12507 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23142330 (22.0 MB)  TX bytes:1373756 (1.3 MB)
          Interrupt:220 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11084 (10.8 KB)  TX bytes:11084 (10.8 KB)

```

Here´s the output from iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.


```


And from iwlist scan:```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scannin
```



and the output of lshw -C network:
```
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:75:dd:3e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=72.141.100.160 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0

```


I don´t know where to go from here. Any help?

---

### Post by linuxonbute on 2008-07-05
The driver for your card is not being loaded so it will not see any networks.

If you go to [http://www.google.com/linux](http://www.google.com/linux) and search for ar22x you will find 

a number of places where this is discussed.

There seems to be an answer to your problem on the Spanish Ubuntu forum:

[http://www.mclarenx.com/2008/06/17/atheros-ar242x-ar5007eg-en-ubuntu-linux-804/](http://www.mclarenx.com/2008/06/17/atheros-ar242x-ar5007eg-en-ubuntu-linux-804/)

I do not know if you understand Spanish but from the little I know it shows 

that you need to use madwifi to load the driver for your card.

It tells you how to compile the version of madwifi you need.

All of the instructions to do this are the parts of the text with a grey 

background except for the bit which shows you where to get the source code 

for madwifi.

Just above the bit which says :

tar -xzvf madwifi-nr-r3366+ar5007.tar.gz

is :

Necesitamos los nuevos controladores para nuestra Atheros AR5007EG. Descárgalos desde aquí. Después descomprime el fichero descargado y accede a la carpeta que se crea:

If you click on the word    aquí    ( which translates to 'here' in English ) it will ask you if you want to save the file - Yes you do 

this is the file the tar bit refers to.

So if you follow the full set of instructions your card should work.

---

### Post by Omicron Machine on 2008-07-06
I followed it exactly and there's some improvement, though I still don't seem to be able to detect the network or connect.

But, ifconfig now looks like this:
```
ath0      Link encap:Ethernet  HWaddr 00:1f:e1:52:93:92  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1e:68:75:dd:3e  
          inet addr:72.141.100.160  Bcast:255.255.255.255  Mask:255.255.254.0
          inet6 addr: fe80::21e:68ff:fe75:dd3e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3077 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2059 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3628187 (3.4 MB)  TX bytes:252611 (246.6 KB)
          Interrupt:220 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:182 errors:0 dropped:0 overruns:0 frame:0
          TX packets:182 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9716 (9.4 KB)  TX bytes:9716 (9.4 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-1F-E1-52-93-92-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:419 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:195 
          RX bytes:0 (0.0 B)  TX bytes:19274 (18.8 KB)
          Interrupt:22 

```


There's similar changes on iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-148 dBm  Noise level=-148 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


And iwlist scan:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results

```



And lshw -C network:
```
 *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:75:dd:3e
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=72.141.100.160 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:1f:e1:52:93:92
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci mult
```


So now it seems like it's ready to go, and just isn't going. Any more suggestions? You've been the most helpful thing I've found so far.

---

### Post by Bucky Ball on 2008-07-06
> **Omicron Machine said:**
> 
And iwlist scan:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results

```

Yes, setting up wireless can be frustrating. Note here that ath0 appears to be up, but not finding your router. Silly question perhaps, but is the light on? If not, it is not loading the right driver. I checked mine and it is exactly the same as what you have posted, difference being I am online ...


> And lshw -C network:
```
 *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:75:dd:3e
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=72.141.100.160 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:1f:e1:52:93:92
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci mult
```

The first network is obviously enough your hardwire ethernet connection. The bit that has me slightly confused is that in the second network, the driver is wifi0 (which is not 'up') which could be an alias of ath0, the driver that is 'up'. Try 

sudo ifup ath0

or maybe

sudo ifup wifi0

... there may be a reason the system is not bringing the card up or the correct driver during boot.

This page could be of some help;

[http://www.cs.rmit.edu.au/support/pub:rmit-wpa](http://www.cs.rmit.edu.au/support/pub:rmit-wpa)

Another thing I notice is that there is essid but no wep or security number in one of your readouts. That is definitely something to do with your problem if your router is sending this and the system has no reference to it. You can see the door but you have no key to unlock it!

Good luck and if I come up with anything, let you know ...

---

### Post by Bucky Ball on 2008-07-07
> ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-148 dBm  Noise level=-148 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Hmmm, mine has the name of the access point between quotation marks and this looks a little strange. In other words, mine looks like this;

IEEE 802.11g  ESSID:"Nickname"

Not this;

IEEE 802.11g  ESSID:""  Nickname:""

'Access Point: Not-Associated'. This is not good, you should have the wep number of your access point (or the right code for whatever security method you are using).

wlan0     IEEE 802.11g  ESSID:"The Name of my Network"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:11:84:AF:26 (you don't have anything here).  
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7 (yours is off)  RTS thr:off  Fragment thr=2346 B (ditto) 
          Link Quality=68/100  Signal level=-61 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

This is from my machine which is working fine, you will note the differences and might give you a few leads ...

Good luck.

---

### Post by Bucky Ball on 2008-07-07
Ha! Don't know what happened there with all my smiley 'o's in the last post!

---

### Post by Omicron Machine on 2008-07-07
Well, hopefully, the smiles are good luck. :D

Anyways, I just realized I took those down with the ethernet cable attached to the laptop instead of the router, because I was using it to post in the first place. Should I put it back on the router, and then try those again? 

The router is still set up and on and I know it's still producing a signal because my friend was here with his Vista laptop last night, and he commented on the fact I'd named it "A Series Of Tubes", ^_^;; but we were heading out and I didn't think to check if his laptop could connect. Doh. Anyways, I just keep switching the cable back and forth to switch between testing it and researching/changing stuff. 

The last two you mentioned, btw, produced these:
```
Ignoring unknown interface ath0=ath0


Ignoring unknown interface wifi0=wifi0.

```

---

### Post by linuxonbute on 2008-07-07
Hi,

glad you have made some progress. It may be that you have the wrong driver but before we go down that route lets see if you can try some other things.

Yes unplug your ethernet cable. Maybe reboot to make sure all the old settings are fully removed from memory.

when you restart do ifconfig again. If, as i expect it will, you still have the eth0 showing then stop it by issuing this command ( as root )

sudo ifconfig eth0 down

ifconfig should not show it any more.

now do

iwconfig

it should give you the same information for ath0 as before.

again, as root

sudo iwconfig ath0 essid="put your essid here"

check it has worked :-

iwconfig

should now show ath0 with essid set to what you just said.


you can do 
sudo 1wconfig ath0 key="your wep key"

and it should be set.

As you have no ip address for it yet then

ifconfig 192.168.1.20 eth0   

You will have to put in an Ip address suitable for your setup here

My routers lan interface is on the 192.168.1.0 range and you need to set your laptop to an address in the same range.

try ifconfig and iwconfig again and post the results.

---

### Post by Bucky Ball on 2008-07-07
You got it linuxonbute.

sudo ifconfig eth0 down

... just logged on to correct the command in my last post and you got the right command for me! 

I was wondering if 'sudo ifconfig eth0 up' (or wifi0 up) may be all that's required and if that works, make it permanent (so it brings up at boot).

---

### Post by linuxonbute on 2008-07-07
> **Bucky Ball said:**
> You got it linuxonbute.

sudo ifconfig eth0 down

... just logged on to correct the command in my last post and you got the right command for me! 

I was wondering if 'sudo ifconfig eth0 up' (or wifi0 up) may be all that's required and if that works, make it permanent (so it brings up at boot).

there is a file you can put your own commands in it's /etc/rc.local

on booting up any command in it is executed after the system commands

if you add lines such as 

ifconfig eth0 down

ifconfig ath0 up

at the end BUT before the exit 0 line they will be executed.

---

### Post by Bucky Ball on 2008-07-07
[QUOTE=linuxonbute]there is a file you can put your own commands in it's /etc/rc.local[/QUOTE]

Neat, thanks for the tip, Linuxonbute. I am attempting to set up a home network so I can file share with 3 Ubuntu machines. Could I put the instructions to start it at boot here? I am about to post regarding my home network setup.

Here is a line from the file that you mention;

# In order to enable or disable this script just change the execution
# bits.

What does this mean exactly? How would I change these bits? Cheers again for the heads up.

---

### Post by linuxonbute on 2008-07-07
> **Bucky Ball said:**
> 
Here is a line from the file that you mention;

# In order to enable or disable this script just change the execution
# bits.

What does this mean exactly? How would I change these bits? Cheers again for the heads up.
if you do ls -l /etc

you will see a few files among them will be ones like these:

drwxr-xr-x  2 root     root      4096 2008-03-01 15:29 rc0.d
drwxr-xr-x  2 root     root      4096 2008-03-01 16:14 rc1.d
drwxr-xr-x  2 root     root      4096 2008-06-08 12:04 rc2.d
drwxr-xr-x  2 root     root      4096 2008-04-18 20:24 rc3.d
drwxr-xr-x  2 root     root      4096 2008-04-18 20:24 rc4.d
drwxr-xr-x  2 root     root      4096 2008-04-18 20:24 rc5.d
drwxr-xr-x  2 root     root      4096 2008-03-01 15:29 rc6.d
-rwxr-xr-x  1 root     root       360 2008-05-15 14:25 rc.local

rc0.d to rc6.d are directories, thats what the d at the start means. Each contains a bunch of files which are run or stopped as you start the system at different run levels.

rc0.d is for shutdown,  rc6.d for reboot  rc3.d for text mode startup and so on

rc.local is the file you are talking about. It's permissions are reading from left to right :
- not a directory
rwx  the owners permissions, in this case root is the owner who can

r - read  w write ( i.e change the file )  x - execute it.

r-x  the permissions for the group, in this case root 

r-x  the permissions for everyone else.

to stop it being executed you need to change it's permissions to

-rw-r--r-- as the owner.  

so in this case root is the owner and to stop it being executable you would

issue the command 
sudo -x /etc/rc.local

after which ls -l would show :

-rw-r--r--  1 root     root       360 2008-05-15 14:25 rc.local

okay:)

---

### Post by Omicron Machine on 2008-07-07
Thanks for all your help so far, guys. I followed the last set of advice you'd given me, up until the IP part. It was saying, " error fetching interface information: Device not found", I recheck the router's range, change the IP I was entering, and the message changes to "Unknown host".

Here's ifconfig now:
```
ath0      Link encap:Ethernet  HWaddr 00:1f:e1:52:93:92  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:35357 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35357 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:32468060 (30.9 MB)  TX bytes:32468060 (30.9 MB)

wifi0     Link encap:UNSPEC  HWaddr 00-1F-E1-52-93-92-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12177 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:195 
          RX bytes:0 (0.0 B)  TX bytes:660306 (644.8 KB)
          Interrupt:22 

```


And iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"A Series Of Tubes"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:1942-1942-19   Security mode:restricted
          Power Management:off
          Link Quality=0/70  Signal level=-148 dBm  Noise level=-148 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by linuxonbute on 2008-07-08
> 
ath0      IEEE 802.11g  ESSID:"A Series Of Tubes"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:1942-1942-19   Security mode:restricted
          Power Management:off
          Link Quality=0/70  Signal level=-148 dBm  Noise level=-148 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/CODE]

Your encryption key is set to 1942-1942-19
Does the encryption key you set on the router have the dashes - in it?
Is the key meant to be ascii or hex?

from man iwconfig :

   key/enc[ryption]
        Used to manipulate encryption or scrambling keys and security mode.
To  set  the  current  encryption key, just enter the key in hex digits as
XXXX-XXXX-XXXX-XXXX or XXXXXXXX.  To set a key other than the current key,
prepend  or  append  [index] to the key itself (this won&#8217;t change which is
the active key). You can also enter the key as an ASCII  string  by  using
the s: prefix. Passphrase is currently not supported.


Just looked back at one of my previous posts.
This bit was wrong :
As you have no ip address for it yet then

ifconfig 192.168.1.20 eth0

it should have been ath0  ( sorry )

---

### Post by Bucky Ball on 2008-07-08
I don't get the part after the correct name "Series of Tubes" where it says Nickname "". What is that about? Missing in my setup.

And cheers for answering my other question regarding execution digits, Linuxonbute. Now I know; became familiar over christmas last time I used Ubuntu and was trying to work out what the hell I was doing (alternate UStudio install and omitted to load a desktop!), but never knew they were called that. lol

---

### Post by linuxonbute on 2008-07-08
> **Bucky Ball said:**
> I don't get the part after the correct name "Series of Tubes" where it says Nickname "". What is that about? Missing in my setup.



man iwconfig is very helpful with this;

nick[name]
 Set  the nickname, or the station name. Some 802.11 products do define it,
but this is not used as far as the protocols (MAC, IP, TCP) are  concerned
and  completely  useless  as far as configuration goes. Only some wireless
diagnostic tools may use it.
Example :
          iwconfig eth0 nickname "My Linux Node"

so you can forget about it.

---

### Post by Omicron Machine on 2008-07-09
The key is supposed to be ASCII, but it is not supposed to have dashes. I didn't enter it with any, I'm certain, so I'm mystified as to how they got there.

---

### Post by linuxonbute on 2008-07-09
> **Omicron Machine said:**
> The key is supposed to be ASCII, but it is not supposed to have dashes. I didn't enter it with any, I'm certain, so I'm mystified as to how they got there.

well you can try setting it manually with :

sudo iwconfig ath0 key=s:thecorrectasciikey

and then see what iwconfig says.

if it seems to be correct see if you can ping anything

eg  ping 66.102.9.99   ( This is [www.l.google.com](www.l.google.com) )

You may need to set more up as well so if you do perhaps you can post the results of iwconfig,  ifconfig  and route -n

---

### Post by Omicron Machine on 2008-07-28
Sorry for the thread-necromancy, but the problem came back.

The real problem is that I'm not sure how the problem was solved in the first place. I could never get it working, untill one day, not having done anything to it prior to shutdown but listen to music, started it up and it was working.

Well, I figured, alright, whatever works. It all puttered along fine until I moved the laptop. I took it to my boyfriend's house to work on some stuff while I was over, and I was using his ethernet connection. I unplug later, pack up, head back, and the original problem had returned. I reprise all the main points in this thread, and once again, nothing helps. Everything reads out the same as it did in my last posts. The key and ESSID are right.

I'm not sure what's going on here. The only clues I have are that during shutdown, I see it deactivate eth0, ath0 and wifi0, and on starting, I see it say for each of them "error fetching device information device not found".

Also, when shutting down, it says, "starting dhpc server dhpcd3...Fail!"


EDIT: I was tinkering around some more, trying to get things up again (mostly trying to switch it to nswrapper, but I can't find the right driver. The one I got for it says it doesn't have the hardware, though now that I think of it, that could be linked to the "device not found" issue again) and it turns out that now I can't connect wired either. It does't detect an ethernet connection either now (posting from roommate's PC).

Edit again: I also just noticed a couple messages like "libhal shutdown failed connection closed" during shutdown.

---

