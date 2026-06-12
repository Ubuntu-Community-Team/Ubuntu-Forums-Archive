---
title: "Wifi won't connect on startup"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by beou on 2007-10-27
Hello,
First, I would like to say that I'm new to this forum, so please excuse me if I miss providing some crucial information.
Also, I'm not very experienced in Linux, though I'm not an absolute beginner.

Here's my issue:
When i log in my computer, my wireless connection is active but doesn't find any network in range. Network manager doesn't show any network, and iwlist doesn't return anything.
In order to connect to my network, I need to click on "Connect to Other Wireless Network.." on network manager and enter all info for my connection. But I have to do that every time I log in.
Another method is to open a terminal and run "sudo iwconfig wlan0 essid <myessid>". Even though I am getting an error "Invalid argument", my link led on my card starts blinking, iwlist returns all network in range and network manager connects me to my wireless after a couple of seconds (and shows all network in range).

I run Ubuntu Gutsy with Gnome, my wireless card is a PCMCIA Linksys WPC54G v4. I use ndiswrapper and have no entries besides the "lo" one in my interfaces file. My network is WPA protected.

If anybody has some thoughts to help me that would be great!

Thank you
Beou

---

### Post by kevdog on 2007-10-27
What driver are you using?

---

### Post by beou on 2007-10-27
Here it is:
~$ ndiswrapper -l
wlipnds : driver installed
        device (17FE:2220) present

---

### Post by kevdog on 2007-10-27
Inside the /etc/modules file, is there a line toward the bottom that states ndiswrapper?

---

### Post by beou on 2007-10-27
yes, here's what's in the file:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper

---

### Post by kevdog on 2007-10-27
Ok everything looks good so far.  

So if iwlist scan doesnt return any networks,  have you tried issuing the command
sudo /etc/init.d/networking restart (after you boot and the network isnt working).

Can you connect after you type this command??

---

### Post by beou on 2007-10-27
I just rebooted and tried but it doesn't change anything,
Here's the copy-paste:
didier@didier-laptop:~$ sudo /etc/init.d/networking restart
[sudo] password for didier:
 * Reconfiguring network interfaces...                                   [ OK ] 
didier@didier-laptop:~$ iwlist wlan0 scan
wlan0     No scan results

---

### Post by jamesey on 2007-10-27
I have the same issue. It wasn't resolved in this thread
[http://ubuntuforums.org/showthread.php?t=587971](http://ubuntuforums.org/showthread.php?t=587971)

---

### Post by kevdog on 2007-10-27
Just to make sure of something, can you post
lshw -C network
route -n

---

### Post by beou on 2007-10-27
Here it is:

didier@didier-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:08:02:66:7b:75
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
       vendor: Linksys, A Division of Cisco Systems
       physical id: 3
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:0f:66:bb:64:88
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wlipnds driverversion=1.45+Cisco-Linksys, LLC.,01/05/2 latency=64 link=no maxlatency=32 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
didier@didier-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
didier@didier-laptop:~$ 

If I plug my wire, I got this for the route command:
didier@didier-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

---

### Post by kevdog on 2007-10-27
No problem with what you typed

When you installed ndiwrapper, did you issue the command
sudo ndiswrapper -m

It creates an alias file.

---

### Post by beou on 2007-10-27
Yes, I did that.
When I do it now, here is the output:
didier@didier-laptop:~$ sudo ndiswrapper -m
module configuration already contains alias directive

Here's the ls -l of the /etc/modprobe.d:
didier@didier-laptop:/etc/modprobe.d$ ll
total 80
-rw-r--r-- 1 root root 4624 2007-10-05 11:41 aliases
-rw-r--r-- 1 root root 2184 2007-10-05 09:06 alsa-base
drwxr-xr-x 2 root root 4096 2007-10-15 18:17 arch
lrwxrwxrwx 1 root root    9 2007-10-21 20:15 arch-aliases -> arch/i386
-rw-r--r-- 1 root root  760 2007-10-27 08:39 blacklist
-rw-r--r-- 1 root root  628 2007-10-05 11:41 blacklist-framebuffer
-rw-r--r-- 1 root root  156 2007-10-05 09:06 blacklist-modem
lrwxrwxrwx 1 root root   41 2007-10-21 20:15 blacklist-oss -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r-- 1 root root   38 2007-10-05 10:26 blacklist-scanner
-rw-r--r-- 1 root root  838 2007-10-05 11:41 blacklist-watchdog
-rw-r--r-- 1 root root  484 2007-10-03 03:55 bluez
-rw-r--r-- 1 root root  343 2007-09-18 19:01 fuse
-rw-r--r-- 1 root root  205 2007-10-15 06:41 ipw3945
-rw-r--r-- 1 root root  299 2007-10-05 11:41 isapnp
-rw-r--r-- 1 root root   16 2007-09-07 03:04 libpisock9
-rw-r--r-- 1 root root  294 2007-10-15 06:41 lrm-video
-rw-r--r-- 1 root root   24 2007-10-21 22:47 ndiswrapper
-rw-r--r-- 1 root root   29 2006-10-09 08:33 nvidia-kernel-nkc
-rw-r--r-- 1 root root  173 2007-10-05 11:41 options
-rw-r--r-- 1 root root   60 2007-09-19 04:50 thinkpad_acpi.modprobe
-rw-r--r-- 1 root root   41 2007-09-19 04:50 toshiba_acpi.modprobe

and the file ndiswrapper only contains:
alias wlan0 ndiswrapper

---

### Post by kevdog on 2007-10-27
Just one last suggestion and then Im out of ideas.  I you type 
sudo /etc/init.d/dbus after rebooting, does this bring up the network at all??

---

### Post by beou on 2007-10-27
Here's the output:

didier@didier-laptop:/etc/modprobe.d$ sudo /etc/init.d/dbus
[sudo] password for didier:
Usage: /etc/init.d/dbus {start|stop|reload|restart|force-reload}
didier@didier-laptop:/etc/modprobe.d$ sudo /etc/init.d/dbus start
 * system message bus already started; not starting.
didier@didier-laptop:/etc/modprobe.d$ sudo /etc/init.d/dbus restart
 * Stopping DHCP D-Bus daemon dhcdbd                                                                  [ OK ] 
 * Stopping Avahi mDNS/DNS-SD Daemon avahi-daemon                                                     [ OK ] 
 * Stopping ConsoleKit daemon console-kit-daemon                                                      [ OK ] 
 * Stopping Hardware abstraction layer hald                                                           [ OK ] 
 * Stopping System Tools Backends system-tools-backends                                               [ OK ] 
 * Stopping network events dispatcher NetworkManagerDispatcher                                        [ OK ] 
 * Stopping network connection manager NetworkManager                                                 [ OK ] 
 * Stopping system message bus dbus                                                                   [ OK ] 
 * Starting system message bus dbus                                                                   [ OK ] 
 * Starting network connection manager NetworkManager                                                 [ OK ] 
 * Starting network events dispatcher NetworkManagerDispatcher                                        [ OK ] 
 * Starting System Tools Backends system-tools-backends                                               [ OK ] 
 * Starting Hardware abstraction layer hald                                                           [ OK ] 
 * Starting ConsoleKit daemon console-kit-daemon                                                      [ OK ] 
 * Starting Avahi mDNS/DNS-SD Daemon avahi-daemon                                                     [ OK ] 
 * Starting DHCP D-Bus daemon dhcdbd                                                                  [ OK ] 


Not much luck here either I guess.

I would say that the nework is already started b/c I can plug my wire and it automatically picks it up. Also, when I go in the network manager and I use "Connect to Other Wireless Network" it works fine and I can connect. It looks like something is missing when the wireless starts, something that the command iwconfig triggers b/c when i run the command the led on my card starts blinking and a couple of seconds later i am connected to my network.

Btw, thanks a lot for your help. Hopefully you or someone will find something cause this drives me crazy!

Thanks
Didier

---

### Post by kevdog on 2007-10-27
Sorry Im out of ideas -- I would suggest wicd, but I really dont think that is going to solve anything.

---

### Post by beou on 2007-10-27
No problem. Thank you very much for your time.

---

### Post by jamesey on 2007-10-31
I have a feeling this problem only affects users who upgraded to gutsy rather than freshly installed it.

---

### Post by Hyperkill on 2007-10-31
I'm having the exact same problem where I had to enter in all of my network information each time to get online.  So, what I did was create a little bash script called runnetwork.sh .  Here is the code I used as an example:

```

#/bin/bash
sudo iwconfig wlan0 mode Managed
sudo iwconfig wlan0 key restricted 910d349a0db11bb0067bdc3a04
sudo iwconfig wlan0 essid TonyDebbie
sudo dhclient wlan0

```

Now, after I boot up I go into a terminal and type: sudo sh runnetwork.sh

afterwards, I get online.  I am currently trying to get the script to run in the session on boot but having issues because I have to input a password to run the sudo command.  Oh well, hope this at least helps a little bit and makes things easier.

---

### Post by HokeyFry on 2007-10-31
did you install ndiswrapper from source or from the ubuntu repos?

---

### Post by beou on 2007-10-31
Hello,

thank you for all your answers and ideas, I'm going to try to answer everybody.

To kevdog, I installed wicd and have exactly the same issue. No wireless network on startup, but if I click on the button "hidden network" and I enter my SSID, immediately all network are found, including mine. Also, I can connect to my network without reentering the informations b/c it is all saved. Side note: my network is not hidden, I can find it without any issue with all my other computers, and with this one as well once the "link" light blinks on my card.

To jamesey,  I performed a fresh install of Gutsy. I was actually having the same issue on Feisty, so rather than doing an upgrade I preferred doing a clean install.

To Hyperkill, my issue is not that my network information is not saved, it is that my card doesn't find any wireless networks, mine in particular. It looks like the scanning functionality doesn't start at boot time somehow. Therefore, since it doesn't find any network, it cannot connect anywhere. I actually wrote a script similar to yours (and btw have the same issue with sudo) where i only do "sudo iwconfig wlan0 essid didier". The command itself returns an error and doesn't work (i guess this will be the next thread), but it is actually enough to get the link light to blink, whatever this means behind the scene, and automatically connect to my network.

To HokeyFry, I installed ndiswrapper from ubuntu repo. But, on Feisty, I installed it from source distro and had the same issue.

Hopefully, nobody will fall asleep trying to read entirely this long answer! English is not my natural language (i'm french) so I apologize if my explanations are not clear.

Thank you all

Didier

---

### Post by beou on 2007-11-08
Hello all,

I ran some more research:
1) I executed a "ps -ef" right after startup and I get a certain list of processes running.
2) I executed the command "sudo iwconfig wlan0 essid didier" and then another "ps -ef".

I get 2 new processes running:
/sbin/wpa_supplicant -g /var/run/wpa_supplicant-global2
/sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.wlan0.leases -pf /var/run/dhclient.wlan0.pid -q -e dhc_dbus=31 -d wlan0

Does that ring a bell to anybody?

Also, I have a question: is wpa_supplicant a module that need to be started automatically, or is it just submitted by network manager?

Thanks
Didier

---

### Post by mpierce on 2007-11-08
Let's try to manual edit your /etc/network/interfaces file.

   sudo vi /etc/network/interfaces

Your card is probably going to be eth1 and not wlan0 but you can try to configure it both ways. (My card was id wlan0 but would never work until I made it eth1)

Here's what you need in the file: 

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
# eth1
auto 00:0E:35:EB:A9:7F     #explicitly id wireless card by mac address
# eth0
auto 00:11:43:6F:7A:FA      #explicitly id nic by mac address

# The primary network interface
auto eth1
iface eth1 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed    #tell wi-fi how it will be managed
        wireless-essid BiPAC_7402GL     #router name
        wireless-key1 10c51ab4xxxxxxxx     #WEP 128-bit key

iface eth0 inet dhcp

---

### Post by beou on 2007-11-09
Hello,

I read in several places over the web that wireless-tools doesn't work with WPA encryption, so I didn't try exactly what you said.
Instead, I went into network manager and changed for a manual configuration. Then I went into the interfaces files and made changes accordingly to what you wrote.

Here's how my file looks like:

didier@didier-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto 00:0F:66:BB:64:88

iface eth1 inet dhcp
wpa-psk 92e2ad0a645e7477c2f3e1cd67224932f68f311678e9952ebd6de8b075fcc8c6
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid didier

auto eth1


Is this conform to what you wanted me to try? Anyway, I tried it and it still doesn't connect. The link light on my card is still off after booting.

Thanks
Didier

---

### Post by mpierce on 2007-11-09
If you network is secure you have to tell it what your wire key is and you probably need to tell it how it's managed.  

Whatever you have done, test it.

sudo ifup eth1 and see if you got an ip address on the card. If that doesn't work you may need to try it with wlan0.

I'd try what I ask to simplify everything and then try your method; you have nothing to lose.

If you get it working, we can also edit this file, /etc/init.d/bootmisc.sh to make sure it works on started up:
   At the bottom of the file, after the <esac> and before <: exit 0 if this exists>
   # ensure that my network card is initialized at startup
   if up eth1
   #

Let's the simple way first.

---

### Post by beou on 2007-11-10
Ok so I tried this configuration, but still I'm unable to connect to my network.

Here's what I have for a ifup, after reboot:
```
didier@didier-laptop:~$ sudo ifup wlan0
[sudo] password for didier:
ifup: interface wlan0 already configured
didier@didier-laptop:~$
```

And whatever I try, I cannot connect to my network using that configuration. I have to come back to a roaming mode.

Something interesting I noticed, when I run ifconfing, here's what I have:
```
didier@didier-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:02:66:7B:75  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1056 (1.0 KB)  TX bytes:1056 (1.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0F:66:BB:64:88  
          inet6 addr: fe80::20f:66ff:febb:6488/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:395 (395.0 b)  TX bytes:621 (621.0 b)
          Interrupt:11 Memory:58000000-58000800 

wlan0:ava Link encap:Ethernet  HWaddr 00:0F:66:BB:64:88  
          inet addr:169.254.7.69  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Memory:58000000-58000800 

```

Any idea what is this "wlan0:ava" thing?

Thanks

---

### Post by charlewi on 2007-11-10
Hi

I have exactly the same problem except I'm using the PCI version of the Linksys WMP54G. I am using WEP key encryption, I wonder if this is causing the problem? Note: this is a completely clean install. Basically it won't automatically connect on boot however on manual connection, or switching manual connection off / on, it works fine, although it takes a long time to connect. On Ubuntu 7.04 it connected instantly.

I installed ndiswrapper using my Windows rt61 driver which made little difference  (I now see connection strengths in network-manager). 

I tried disabling network manager and the alternative (rwifi?) to no avail.

I tried adding the connection details to /etc/networks/interfaces but I still have slow connection and, critically, no automatic connection at boot, I need to untick then tick the 'Manual Connection' in Manual Connection dialog.

The weird thing is that once connected it runs fine, which makes me wonder if somethings no getting loaded in the right order on bootup?

Has anyone had any further thoughts? Personally I could live with it but I'm setting the computer up for my technology-phobic parents and would be great if I could fix this!

Incidentally I'm a big fan of Ubuntu, the posts on these forums always seem really friendly compared to lots of linux sites, it's much appreciated!

Many thanks in advance.

Charlie

**** not to worry, I found a Belkin wifi card knocking around and tried swapping it for the Linksys - all working great now. Good luck Beou.

---

### Post by beou on 2007-11-10
Thanks man! Good that you've been able to find a solution.
I'm still searching mine...
What Belkin did you use? Maybe my card is too old and not fully compatible with the new releases of ubuntu.

---

### Post by shoryuken on 2007-11-11
Hi,

I'm having the same exact problem running the same card on Gutsy. 

I use Wifi-Radar to activate the connection since it saves all the settings and I don't need to write a script. The only annoying thing is that the connection does not come up automatically and the scan only works after a couple of attempts at activating the connection through Wifi-Radar.

I've put wext as the WAP driver.

It would still be nice to figure out how to fix the problem so that after boot-up the card would automatically scan and connect to the network.

What I don't understand is why after the connection is made ifconfig and iwconfig both report wlan0 statistics:
ifconfig:
wlan0     Link encap:Ethernet  HWaddr 00:18:F8:41:24:41  
          inet addr:10.0.0.106  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f8ff:fe41:2441/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21793 errors:0 dropped:22 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8121353 (7.7 MB)  TX bytes:3197828 (3.0 MB)
          Interrupt:5 Memory:38000000-38000800 

iwconfig:
wlan0     IEEE 802.11g  ESSID:"MyHome"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:F7:63:F9   
          Bit Rate=11 Mb/s   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management: off
          Link Quality:68/100  Signal level:-52 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


but "sudo ifup -a" reports the following:
Ignoring unknown interface eth2=eth2.
Ignoring unknown interface ath0=ath0.
Ignoring unknown interface wlan0=wlan0.

:confused:

---

### Post by gigaferz on 2007-11-11
hello,

I bought a couple of zonetwireless cards pci & usb.

I had to edgys at the moment, 
in one pc i installed from source following ndiswrapper guide @ sourceforge
on the other one i just updated the repos and it worked right away (i didnt try that on the first one ,it just ocurred to me)
they ran fine I even upgraded to feisty on the first one, everythings still goodll
however on the second one I did a fresh install, ever since i've had a similar problem.
I used to enter sudo  iwconfig blah password essid ...  like 10 times or sometimes just one.... and it worked. I gave up and went back to eth0.

Now im setting up an ancient machine for a friend and i donated my pci zonet, with a fresh feisty install. And Im back to the same problem, well maybe worse...
i enter the manual iwconfig command, bring down & up the interfaces, enter iwconfig again.go to the network manager, enable it and disable it,, and after a few tries doing everything It comes up.

Knowing I have a wireless fesity working good, I could look at those config files to see how is configured to have no problems....

My question here is, which files should I look up to see if I can make it work on a different computer?
im going through all this because is for a total windos biased person, and with no experience at all,.

thankyou all

sudo dhclient wlan0 after iwconfig etc etc DOEs the trick

Somebody here helped me writing a script(well he did it,lol) so it can be used in any wireless network with wep protection....

---

### Post by gigaferz on 2007-12-18
hello 

I managed to make my wireless run at start up, in 2 different omputers different ubuntu versions.

Inside  etc folder there is this file rc.local



most of the times there is nothing there but you can put some commands so they run right away.
    
          I used to have @ work this command to get internet back then
   "mii-tool -F  10baseT -FD eth1"   this was for a 10mbps network 

  now in that same file but in different computers i use a command to activate my wireless devices. (assuming it DOes work but you have to do it manually everytime you turn on the computer)

     "sudo iwconfig wlan0 essid home key open s:qwert"         
      "sudo dhclient wlan0"                                            
  all before the line "exit 0"

 thanks to user dmizer

---

