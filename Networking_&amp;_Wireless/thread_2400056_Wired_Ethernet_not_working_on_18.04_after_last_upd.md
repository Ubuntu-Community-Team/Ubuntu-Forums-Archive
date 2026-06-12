---
title: "Wired Ethernet not working on 18.04 after last updates."
date: 2018-09-01
forum: Networking &amp; Wireless
---

### Post by grimecho on 2018-09-01
My Ethernet (wired) connection on multiple laptops does not work after installing the standard updates after a fresh 18.04 install. The WiFi (wireless) connections work fine.

The wired connection is not able to get an IP or auto-negotiate with the DHCP server on my router. I am positive that the issue is not with the hardware on my laptop, the network cable, or the settings on my router.

I am includind as much information as possible in anticipation of submitting a bug report for Ubuntu. However, I would like to (a) discover a fix, and (b) identify what specific updated file(s) broke the wired network interface. As it currently exists, 18.04 is unuable for me, as need ethernet networking and don't want to use a non-updated OS.

Networking diagnostic info when successfully connected via WiFi: [URL="http://paste.ubuntu.com/p/VQwz3zSdKN/"]http://paste.ubuntu.com/p/VQwz3zSdKN/
[/URL]Networking diagnostic info when trying to connect via Ethernet: [http://paste.ubuntu.com/p/dmBfXxRHzv/]("https://paste.ubuntu.com/p/dmBfXxRHzv/")

Wired Ethernet **works** under the following:
[LIST]
[*]Ubuntu 18.04 Live 
[*]Ubuntu 18.04 fresh install to laptop's harddrive 
[*]Kubuntu 18.04 w/ pending updates installed to a USB drive\ 
[*]Kali Linux 2018.3 
[/LIST]

Wired Ethernet **does not work** under the following:
[LIST]
[*]Ubuntu 18.04 post-update installed locally 
[*]Kubuntu 18.04 post-update installed to a USB drive 
[/LIST]

Procedure to reproduce the problem:
[LIST=1]
[*]Using an Acer Aspire V laptop 
[*]Download Ubuntu 18.04.1 ISO and install to Flash Drive 
[*]Connect Ethernet 
[*]Boot Ubuntu Live -- Wired Internet is connected and works 
[*]Install Ubuntu (I'm using manual partitioning to set up encryption, but this doen't matter) 
[*]Remove Live USB and reboot 
[*]Installed Ubuntu - Ethernet connects as soon as login happens 
[*]Prompted to install recommended updates (already downloaded) 
[*]Install all updates. - Ethernet sill works 
[*]Restart - Ethernet does not work 
[/LIST]

Symptoms:
[LIST]
[*]GUI Network Manager will show "Wired Connecting". After about 20 seconds, a system try message will say "Connection failed: Activation of network connection failed" 
[*]*dhclient -v enp1s0f1* produces an endless stream of failed attempts 
[/LIST]

```

sudo dhclient -v enp1s0f1

Listening on LPF/enp1s0f1/f8:a9:63:a4:af:27
Sending on   LPF/enp1s0f1/f8:a9:63:a4:af:27
Sending on   Socket/fallback
DHCPDISCOVER on enp1s0f1 to 255.255.255.255 port 67 interval 3 (xid=0xdc351d60)
DHCPDISCOVER on enp1s0f1 to 255.255.255.255 port 67 interval 4 (xid=0xdc351d60)
... (endless)

```

Clearly my router is not on 255.255.255.255. It is on 192.168.0.1 (default gateway)

```

sudo dhclient -v -s 192.168.0.1 enp1s0f1

Listening on LPF/enp1s0f1/f8:a9:63:a4:af:27
Sending on   LPF/enp1s0f1/f8:a9:63:a4:af:27
Sending on   Socket/fallback
DHCPDISCOVER on enp1s0f1 to 192.168.0.1 port 67 interval 3 (xid=0xce5c8048)
DHCPDISCOVER on enp1s0f1 to 192.168.0.1 port 67 interval 7 (xid=0xce5c8048)
... (endless)

```

I tried using 192.168.0.255 and 192.168.0.0 as well with the same results

Unsuccessful fixes:
[LIST]
[*]Restart network manger service 
[*]Delete all Network Manager profiles 
[*]Uninstall and reinstall Network Manager 
[*]Attempt to reinstall all networking utilities by doing the following:
[LIST]
[*]manually download all packages listed from ```
sudo apt list *network* | grep installed
``` 
[*]uninstall listed packages 
[*]reinstall listed packages using ```
dpkg
``` 
[*]This seems like it might have tempoirially fixed the problem Kubuntu 18.04. Some combination of that and some other steps resulted in me being connected via Ethernet after a restart. However, upon the next restart the issue returned 
[/LIST]
    
[/LIST]

Diagnostic information:
diagnostic script ouput when successfully connected via WiFi: [URL="http://paste.ubuntu.com/p/VQwz3zSdKN/"]http://paste.ubuntu.com/p/VQwz3zSdKN/
[/URL]diagnostic script ouput when trying to connect via Ethernet: [http://paste.ubuntu.com/p/dmBfXxRHzv/](http://paste.ubuntu.com/p/dmBfXxRHzv/)


```

ifconfig
enp1s0f1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        ether f8:a9:63:a4:af:27  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 895  bytes 181974 (181.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 6110  bytes 432641 (432.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 6110  bytes 432641 (432.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.14  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::88b5:b0a6:8b6f:3d7a  prefixlen 64  scopeid 0x20<link>
        ether 20:68:9d:41:36:7b  txqueuelen 1000  (Ethernet)
        RX packets 16821  bytes 8300368 (8.3 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 10092  bytes 2101873 (2.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

---

### Post by grimecho on 2018-09-02
I've confirmed that this is affecting an Asus laptop as well.

---

### Post by praseodym on 2018-09-02
Install another driver

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.046.00-1_all.deb
sudo dpkg -i r8168-dkms_8.046.00-1_all.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot

---

### Post by grimecho on 2018-09-04
@praseodym

Thanks! That seems to have worked. The commands you provided seem to be part of a common solution, but I'm wondering if you could clarify a few points. I would like to document the fix so that I can better understand how to apply it to related problems.

1. The first command seems to reinstall several packages related to the Linux kernel. I'm a little confused about why these specific packages were chosen though. My understanding is that build-essential is related to packages used for compiling other packages, but I'm not sure what the linux-headers and dmks packages have to do with networking. I know dkms is related to driver modules, but that it is separate from the actual driver's themselves. Were these packages specific to this issue, or were they more of a catch-all to reinstall when issues arise?

2. Did the latest 18.04 update upgrade the 8168 drivers to 8169? If I didn't already know this, how would I find out (e.g. some kind of system log showing what was changed when I install updates from within Ubuntu)

3. When I installed the 8168 drivers, the package file also had be rebuild the initrd, which I understand is the memory image or ram disk that fires off the rest of the kernel load when Linux starts. Are the networking drivers this deeply embedded in Linux? My assumption was that while a networking stack might be built into the core of a kernel, individual networking drivers operated at a higher level.

4. Finally, my assumption is that by blacklisting the r8169 drivers, I will prevent them from auto-updating in the future.

Thanks again. If you don't have the time to answer these questions, I understand. Just glad to have Linux updated and usable again.  .... Now to roll back the drivers on three other installs....

2.

---

### Post by pnck on 2018-09-04
Hello,

The same problem is here [https://ubuntuforums.org/showthread.php?t=2399918](https://ubuntuforums.org/showthread.php?t=2399918)

However this solution doesn't work. Still can't connect to isp dhcp server. 

@grimecho can you do tcpdump of dhcpdiscover messages?

Thanks

---

### Post by praseodym on 2018-09-04
1. You need the headers and dkms to ensure that dkms compiles the source code after each kernel upgrade

2. No, they are separated. From experience, r8168 works much better with the cards showing [10ec:8168]

3. Yes, they are compiled into the kernel. Windows "attaches" them to the microkernel to an "interface", not with Linux

4. Exactly, otherwise 2 drivers are loaded

---

### Post by praseodym on 2018-09-04
P.S.: Source code is located in /usr/src

---

### Post by grimecho on 2018-09-04
Thanks for the answers and the help.

Seeing as this issue is still originally being caused by applying the latest updates to Ubuntu, I'm going to open a bug report this weekend.

@pnck - I'm getting the same DHCP checksum errors in Wireshark, but I'm still able to connect. On my outgoing DHCP request, the frame check sequence states "Frame check sequence: 0x00000000 incorrect, should be 0xacb0fc3f" just as you posted. However, my router still responds with a DHCP ACK addressed to and containing my assigned IP.

Here are the filtered Wireshark logs if you want to look: [https://drive.google.com/open?id=1BAorF0NiEPjpWB7UzE7EbTx3BLGY1rl4](https://drive.google.com/open?id=1BAorF0NiEPjpWB7UzE7EbTx3BLGY1rl4)

---

### Post by pnck on 2018-09-05
@grimecho thanks a lot. I wan't to say that my home DHCP server sends dhcpoffer, however ISP DHCP doesn't do this. &#1057;onsequently Ubuntu dhclient works with home router DHCP server in spite of wrong checksum. I'm planning to create the bug report too.

---

### Post by grimecho on 2018-09-05
If you're having issues with getting an IP address directly from your ISP, can't you just connect via a NATed router? Lots of benefits to this besides just easier configuration. Of course, you might have apps or services that need an external IP address directly

---

### Post by pnck on 2018-09-10
Thanks, yes, I agree with you about router, however it isn't best decision for my mother's place. So I would prefer connect Ubuntu pc direct to ISP.

Did you create bag report?

---

### Post by lcreid on 2018-09-24
I used @praseodym's solution and it appears to have worked. However, I had to reboot three times to get everything working properly, i.e., wireless connecting automatically, WiFi working, and icon appearing in the task bar with the correct content. Since then I've rebooted at least two more times and both network interfaces appear to be working. (I hate it when rebooting appears to fix problems, but I guess that's where we're at in 2018.)

Is this a change that I should roll back after a future update if I want my system to be "out-of-the-box" Ubuntu as much as possible?

---

### Post by upandacross on 2018-09-25
Update - wired connection successfully established upon first boot. Fails upon reboot. Our's is not to reason why, our's is but to reboot and die.

Regrettably, this solution did not survive rebooting. Will leave it here for hysterical purposes and will keep you posted.

After the usual suite of false leads, especially those soley focused on network manager, I settled in on what changed with 17.10: migration from ifupdown (network manager) to netplan.   My guess is that network manager, without guidance from netplan, was sending the DHCP request with ipv6 and my old router couldn't deal with ipv6. Whatever the problem was, syslog showed an ip address request sent to my DHCP server but no reply was ever received and the wired connection was never established. Wifi was working fine. Go figure.

The fix for me with 18.04 was described in the netplan page [here]("https://goo.gl/rr4rrd") and augmented to use dhcp4 as described [here]("https://goo.gl/MGvAvg") under the "Configuring DHCP" section. Interestingly, "netplan generate" gave me nothing in the target directory /etc/netplan. I had to create a file there with vi (named "01-netcfg.yaml" but only the ".yaml" matters as this is the only file I needed). The ethernet device name was revealed with "ifconfig". So, the final contents of my yaml file was:

```
network:
  version: 2
  renderer: NetworkManager
  ethernets:
    enp6s0f1:
      dhcp4: yes


```

Next, a change to /etc/network/interfaces:

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto enp6s0f1
iface enp6s0f1 inet dhcp
```

Finally, there is a change to /etc/NetworkManager/NetworkManager.conf telling network manager to manage the wired connection):

```
plugins=ifupdown,keyfile

[ifupdown]
managed=true


```



These plus "netplan apply" and all was well.

Mileage may vary.

---

### Post by santiagomd3305 on 2019-01-07
grimecho, Yes, It does. I have an Asus with the same problem.

---

### Post by Briasaurus Rex on 2019-02-11
Having the same problem on a Dell Precision T7500 with a Broadcom BCM5761. upandcross's solution worked only temporarily. No better than restarting the service. Output of journalctl /usr/sbin/NetworkManager indicates the connection times out but then fails to fully reconnect. Attempts to reconnect continuously with time out errors until the service is restarted.

---

### Post by gelfling6 on 2019-03-26
beginning to sound like it did happen with the update, Mine happening with a
Toshiba C855D laptop and a Asus M2N32 desktop (On both ports enp0s16 & 17),
 tried the patch above, restarted, no change.

---

### Post by stephenfkennedy on 2019-06-03
> **upandacross said:**
> Update - wired connection successfully established upon first boot. Fails upon reboot. Our's is not to reason why, our's is but to reboot and die.

Regrettably, this solution did not survive rebooting. Will leave it here for hysterical purposes and will keep you posted.

After the usual suite of false leads, especially those soley focused on network manager, I settled in on what changed with 17.10: migration from ifupdown (network manager) to netplan.   My guess is that network manager, without guidance from netplan, was sending the DHCP request with ipv6 and my old router couldn't deal with ipv6. Whatever the problem was, syslog showed an ip address request sent to my DHCP server but no reply was ever received and the wired connection was never established. Wifi was working fine. Go figure.

The fix for me with 18.04 was described in the netplan page [here]("https://goo.gl/rr4rrd") and augmented to use dhcp4 as described [here]("https://goo.gl/MGvAvg") under the "Configuring DHCP" section. Interestingly, "netplan generate" gave me nothing in the target directory /etc/netplan. I had to create a file there with vi (named "01-netcfg.yaml" but only the ".yaml" matters as this is the only file I needed). The ethernet device name was revealed with "ifconfig". So, the final contents of my yaml file was:

```
network:
  version: 2
  renderer: NetworkManager
  ethernets:
    enp6s0f1:
      dhcp4: yes


```

Next, a change to /etc/network/interfaces:

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto enp6s0f1
iface enp6s0f1 inet dhcp
```

Finally, there is a change to /etc/NetworkManager/NetworkManager.conf telling network manager to manage the wired connection):

```
plugins=ifupdown,keyfile

[ifupdown]
managed=true


```



These plus "netplan apply" and all was well.

Mileage may vary.


Hello. I have tried the above but seem to have done something wrong:

subprocess.CalledProcessError: Command '['udevadm', 'test-builtin', 'net_setup_link', '/sys/class/net/enp3s0:avahi']' returned non-zero exit status 4

Please advise.

Thank you
Stephen

Update:

I resorted to manually inputting the IP address information. It worked for a day but now my Ethernet card doesn't seem to be detected at all. 

lshw -C network output no longer includes "logical name"

Drowning in forum links. Need help!

---

### Post by viaciofano on 2020-03-06
I feel that I have the same issue in that a bug has caused loss of ethernet. This happened to a machine that i have had for 10 years with no probelm. I then found another pc tower. Loaded the LTS 18.04 that I had on a USB. set up and found the same issue. 
I am not able to get ethernet working on both machines now. I tried the previous command but it returned on mine Couldnt find any package?

If you can help me? I am a newbie with commands though and need the detail with steps. 

Thanks in advance

---

### Post by viaciofano on 2020-03-06
Really sorry, found that a ethernet lead was faulty from the router to the switch. changed it and all working now. 

Thanks in advance

---

### Post by leroy22 on 2020-03-13
> **grimecho said:**
> My Ethernet (wired) connection on multiple laptops does not work after installing the standard updates after a fresh 18.04 install. The WiFi (wireless) connections work fine.

The wired connection is not able to get an IP or auto-negotiate with the DHCP server on my router. I am positive that the issue is not with the hardware on my laptop, the network cable, or the settings on my router.

I am includind as much information as possible in anticipation of submitting a bug report for Ubuntu. However, I would like to (a) discover a fix, and (b) identify what specific updated file(s) broke the wired network interface. As it currently exists, 18.04 is unuable for me, as need ethernet networking and don't want to use a non-updated OS.

Networking diagnostic info when successfully connected via WiFi: [URL="http://paste.ubuntu.com/p/VQwz3zSdKN/"]http://paste.ubuntu.com/p/VQwz3zSdKN/
[/URL]Networking diagnostic info when trying to connect via Ethernet: [http://paste.ubuntu.com/p/dmBfXxRHzv/]("https://paste.ubuntu.com/p/dmBfXxRHzv/")

Wired Ethernet **works** under the following:
[LIST]
[*]Ubuntu 18.04 Live 
[*]Ubuntu 18.04 fresh install to laptop's harddrive 
[*]Kubuntu 18.04 w/ pending updates installed to a USB drive\ 
[*]Kali Linux 2018.3 
[/LIST]

Wired Ethernet **does not work** under the following:
[LIST]
[*]Ubuntu 18.04 post-update installed locally 
[*]Kubuntu 18.04 post-update installed to a USB drive 
[/LIST]

Procedure to reproduce the problem:
[LIST=1]
[*]Using an Acer Aspire V laptop 
[*]Download Ubuntu 18.04.1 ISO and install to Flash Drive 
[*]Connect Ethernet 
[*]Boot Ubuntu Live -- Wired Internet is connected and works 
[*]Install Ubuntu (I'm using manual partitioning to set up encryption, but this doen't matter) 
[*]Remove Live USB and reboot 
[*]Installed Ubuntu - Ethernet connects as soon as login happens 
[*]Prompted to install recommended updates (already downloaded) 
[*]Install all updates. - Ethernet sill works 
[*]Restart - Ethernet does not work 
[/LIST]

Symptoms:
[LIST]
[*]GUI Network Manager will show "Wired Connecting". After about 20 seconds, a system try message will say "Connection failed: Activation of network connection failed" 
[*]*dhclient -v enp1s0f1* produces an endless stream of failed attempts 
[/LIST]

```

sudo dhclient -v enp1s0f1

Listening on LPF/enp1s0f1/f8:a9:63:a4:af:27
Sending on   LPF/enp1s0f1/f8:a9:63:a4:af:27
Sending on   Socket/fallback
DHCPDISCOVER on enp1s0f1 to 255.255.255.255 port 67 interval 3 (xid=0xdc351d60)
DHCPDISCOVER on enp1s0f1 to 255.255.255.255 port 67 interval 4 (xid=0xdc351d60)
... (endless)

```

Clearly my router is not on 255.255.255.255. It is on 192.168.0.1 (default gateway)

```

sudo dhclient -v -s 192.168.0.1 enp1s0f1

Listening on LPF/enp1s0f1/f8:a9:63:a4:af:27
Sending on   LPF/enp1s0f1/f8:a9:63:a4:af:27
Sending on   Socket/fallback
DHCPDISCOVER on enp1s0f1 to 192.168.0.1 port 67 interval 3 (xid=0xce5c8048)
DHCPDISCOVER on enp1s0f1 to 192.168.0.1 port 67 interval 7 (xid=0xce5c8048)
... (endless)

```

I tried using 192.168.0.255 and 192.168.0.0 as well with the same results

Unsuccessful fixes:
[LIST]
[*]Restart network manger service 
[*]Delete all Network Manager profiles 
[*]Uninstall and reinstall Network Manager 
[*]Attempt to reinstall all networking utilities by doing the following:
[LIST]
[*]manually download all packages listed from ```
sudo apt list *network* | grep installed
``` 
[*]uninstall listed packages 
[*]reinstall listed packages using ```
dpkg
``` 
[*]This seems like it might have tempoirially fixed the problem Kubuntu 18.04. Some combination of that and some other steps resulted in me being connected via Ethernet after a restart. However, upon the next restart the issue returned 
[/LIST]
      
[/LIST]

Diagnostic information:
diagnostic script ouput when successfully connected via WiFi: [URL="http://paste.ubuntu.com/p/VQwz3zSdKN/"]http://paste.ubuntu.com/p/VQwz3zSdKN/
[/URL]diagnostic script ouput when trying to connect via Ethernet: [http://paste.ubuntu.com/p/dmBfXxRHzv/](http://paste.ubuntu.com/p/dmBfXxRHzv/)


```

ifconfig
enp1s0f1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        ether f8:a9:63:a4:af:27  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 895  bytes 181974 (181.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 6110  bytes 432641 (432.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 6110  bytes 432641 (432.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.14  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::88b5:b0a6:8b6f:3d7a  prefixlen 64  scopeid 0x20<link>
        ether 20:68:9d:41:36:7b  txqueuelen 1000  (Ethernet)
        RX packets 16821  bytes 8300368 (8.3 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 10092  bytes 2101873 (2.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```


The problem might be 192.168.0.1 is not the default gateway address, better check it out. you can send me the model of your router I'll check on [https://192-168-0-1.us/]("https://192-168-0-1.us") for a solution.

---

