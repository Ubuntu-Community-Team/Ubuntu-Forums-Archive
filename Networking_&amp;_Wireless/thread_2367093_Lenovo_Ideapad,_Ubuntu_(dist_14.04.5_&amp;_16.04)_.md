---
title: "Lenovo Ideapad, Ubuntu (dist 14.04.5 &amp; 16.04) cannot connect to internet through wifi"
date: 2017-07-25
forum: Networking &amp; Wireless
---

### Post by arunavoster on 2017-07-25
Hello,
I got my new laptop Lenovo Idepad 510 and tried installing 16.04, it worked great for a couple of days and suddenly one fine day it stopped connecting to the internet, it couldn't even detect the wifi networks. I am new to 16.04 so thought of falling back to 14.04 LTS but here I can detect the wifi but cannot connect to the internet at all. I checked all the threads, and I apologize the wireless-info script did not give me any info, after running it the entire info.txt got replaced by one line that is ########wireless-info start##########. Also, wired connection is not working as well.
**PRESENTLY I AM RUNNING 14.04 LTS SO PLEASE DONT BE CONFUSED WITH 16.04.**

Also kindly if you provide me solutions like sudo apt-get update or install of anything I won't be able to do them, as I can't access to the internet from my Ubuntu dist. 

Things that I have already tried:
[LIST=1]
[*][https://askubuntu.com/questions/894846/connected-to-the-wireless-but-no-internet-access](https://askubuntu.com/questions/894846/connected-to-the-wireless-but-no-internet-access)
[*][https://ubuntuforums.org/showthread.php?t=2238087](https://ubuntuforums.org/showthread.php?t=2238087)
[*][https://itsfoss.com/fix-no-wireless-network-ubuntu/](https://itsfoss.com/fix-no-wireless-network-ubuntu/)
[*][https://askubuntu.com/questions/488139/installed-ubuntu-14-04-cannot-connect-to-internet-with-wired-or-wireless-conne](https://askubuntu.com/questions/488139/installed-ubuntu-14-04-cannot-connect-to-internet-with-wired-or-wireless-conne)
[*][https://askubuntu.com/questions/458967/ubuntu-14-04-my-computer-sees-the-wireless-network-but-wont-connect-to-it-k](https://askubuntu.com/questions/458967/ubuntu-14-04-my-computer-sees-the-wireless-network-but-wont-connect-to-it-k)
[*]I have also tried installing the broadcom driver from the ubuntu iso file like this.
[/LIST]
```

cd /"path_to_USB_directory"
sudo dpkg -i pool/main/d/dkms/*.deb
sudo dpkg -i pool/restricted/b/bcmwl/*.deb

```


However here are some of the outputs:

```
sudo lshw -c network

OUTPUT:
*-network                      description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 10
       serial: c8:5b:76:f8:01:bc
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:127 ioport:5000(size=256) memory:a4104000-a4104fff memory:a4100000-a4103fff
  *-network
       description: Wireless interface
       product: RTL8821AE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: c8:3d:d4:91:5b:e9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8821ae driverversion=4.4.0-31-generic firmware=N/A ip=192.168.1.76 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:131 ioport:4000(size=256) memory:a4000000-a4003fff 
```

```
ifconfig -a
OUTPUT:

eth0      Link encap:Ethernet  HWaddr c8:5b:76:f8:01:bc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:9994 (9.9 KB)  TX bytes:9994 (9.9 KB)


wlan0     Link encap:Ethernet  HWaddr c8:3d:d4:91:5b:e9  
          inet addr:192.168.1.76  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ca3d:d4ff:fe91:5be9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:477 errors:0 dropped:1 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:83676 (83.6 KB)  TX bytes:13303 (13.3 KB) 
```


```
rfkill list
output:

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```


The contents of my /etc/network/interfaces

```
auto lo
iface lo inet loopback

```

---

### Post by vocx on 2017-07-26
> **arunavoster said:**
> Hello,
I got my new laptop Lenovo Idepad 510 and tried installing 16.04, it worked great for a couple of days and suddenly one fine day it stopped connecting to the internet, it couldn't even detect the wifi networks. I am new to 16.04 so thought of falling back to 14.04 LTS but here I can detect the wifi but cannot connect to the internet at all. I checked all the threads, and I apologize the wireless-info script did not give me any info, after running it the entire info.txt got replaced by one line that is ########wireless-info start##########. Also, wired connection is not working as well.
...
[LIST=1]
[*]I have also tried installing the broadcom driver from the ubuntu iso file like this.
[/LIST]
```

cd /"path_to_USB_directory"
sudo dpkg -i pool/main/d/dkms/*.deb
sudo dpkg -i pool/restricted/b/bcmwl/*.deb

```

First of all, if your "lshw" is correct I don't understand why you install the Broadcom drivers. Both your Ethernet and Wifi cards are Realtek, so you should not be using Broadcom drivers at all.

> 
However here are some of the outputs:

```
sudo lshw -c network

OUTPUT:
*-network                      description: Ethernet interface
       product: **RTL8111/8168/8411** PCI Express Gigabit Ethernet Controller
       **vendor: Realtek Semiconductor Co., Ltd.**
...
       configuration: autonegotiation=on broadcast=yes driver=**r8169** driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:127 ioport:5000(size=256) memory:a4104000-a4104fff memory:a4100000-a4103fff
  *-network
       description: Wireless interface
       product: **RTL8821AE** 802.11ac PCIe Wireless Network Adapter
       **vendor: Realtek Semiconductor Co., Ltd.**
...
       configuration: broadcast=yes driver=**rtl8821ae** driverversion=**4.4.0-31-generic** firmware=N/A **ip=192.168.1.76** latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:131 ioport:4000(size=256) memory:a4000000-a4003fff 
```


The Ethernet wired connection should work. It uses a very generic driver, the "r8169".

You should check for solutions regarding the specific model of your Wifi card, which is RTL8821AE. There are many different Realtek cards and drivers. You can browse this subforum and you will see many such threads.

If your Internet was working fine, and it only stopped after a few days, the problem was probably a kernel update. A new kernel introduces new drivers, and sometimes a regression is seen. You could reboot. In the "grub" black screen, you may select "Advanced options", and there select a previous kernel to see if the problem goes away in that version. It seems the version you have when you run the "lshw" command was 4.4.0-31. That seems a bit old, as the current kernel for 16.04 is 4.4.0-87.

Nevertheless, I would make sure the drivers are used by your system.
```

sudo modprobe r8169
sudo modprobe rtl8821ae
sudo service network-manager restart

```
This will try to load the drivers into the kernel, and should not output anything if successful. It will also try to restart the network manager. You seem to be getting a local IP address 192.168.1.76 from your router, so maybe the connection works, but the problem is at your router.

After running the "modprobe" commands, the kernel usually prints a lot of messages as well.
```

dmesg -H | tail -40

```
This will show the last 40 lines printed by the kernel.

I suggest you run the wireless script again, as there may be some important configuration files that may have to be changed. I don't believe the entire output disappeared, maybe you need to scroll through the file if you are viewing it from Windows.

---

### Post by arunavoster on 2017-07-26
> **vocx said:**
> First of all, if your "lshw" is correct I don't understand why you install the Broadcom drivers. Both your Ethernet and Wifi cards are Realtek, so you should not be using Broadcom drivers at all.


The Ethernet wired connection should work. It uses a very generic driver, the "r8169".

You should check for solutions regarding the specific model of your Wifi card, which is RTL8821AE. There are many different Realtek cards and drivers. You can browse this subforum and you will see many such threads.

If your Internet was working fine, and it only stopped after a few days, the problem was probably a kernel update. A new kernel introduces new drivers, and sometimes a regression is seen. You could reboot. In the "grub" black screen, you may select "Advanced options", and there select a previous kernel to see if the problem goes away in that version. It seems the version you have when you run the "lshw" command was 4.4.0-31. That seems a bit old, as the current kernel for 16.04 is 4.4.0-87.

Nevertheless, I would make sure the drivers are used by your system.
```

sudo modprobe r8169
sudo modprobe rtl8821ae
sudo service network-manager restart

```
This will try to load the drivers into the kernel, and should not output anything if successful. It will also try to restart the network manager. You seem to be getting a local IP address 192.168.1.76 from your router, so maybe the connection works, but the problem is at your router.

After running the "modprobe" commands, the kernel usually prints a lot of messages as well.
```

dmesg -H | tail -40

```
This will show the last 40 lines printed by the kernel.

I suggest you run the wireless script again, as there may be some important configuration files that may have to be changed. I don't believe the entire output disappeared, maybe you need to scroll through the file if you are viewing it from Windows.

Hello VOCX,

Thanks for your response first of all. Yes it makes sense , but as I am in desperate need for the ubuntu to work, got an online test to finish up I tried everything even installing broadcom which is quite a stupid act. Regardless, right now I have gone back to ubuntu 14.04 and uninstalled 16.04 that is why you see the older kernel. I should rather remove the mention of 16.04 from my question in order to avoid any confusion. I will report back once I have tried what you suggested.

---

### Post by arunavoster on 2017-07-26
> **vocx said:**
> First of all, if your "lshw" is correct I don't understand why you install the Broadcom drivers. Both your Ethernet and Wifi cards are Realtek, so you should not be using Broadcom drivers at all.


The Ethernet wired connection should work. It uses a very generic driver, the "r8169".

You should check for solutions regarding the specific model of your Wifi card, which is RTL8821AE. There are many different Realtek cards and drivers. You can browse this subforum and you will see many such threads.

If your Internet was working fine, and it only stopped after a few days, the problem was probably a kernel update. A new kernel introduces new drivers, and sometimes a regression is seen. You could reboot. In the "grub" black screen, you may select "Advanced options", and there select a previous kernel to see if the problem goes away in that version. It seems the version you have when you run the "lshw" command was 4.4.0-31. That seems a bit old, as the current kernel for 16.04 is 4.4.0-87.

Nevertheless, I would make sure the drivers are used by your system.
```

sudo modprobe r8169
sudo modprobe rtl8821ae
sudo service network-manager restart

```
This will try to load the drivers into the kernel, and should not output anything if successful. It will also try to restart the network manager. You seem to be getting a local IP address 192.168.1.76 from your router, so maybe the connection works, but the problem is at your router.

After running the "modprobe" commands, the kernel usually prints a lot of messages as well.
```

dmesg -H | tail -40

```
This will show the last 40 lines printed by the kernel.

I suggest you run the wireless script again, as there may be some important configuration files that may have to be changed. I don't believe the entire output disappeared, maybe you need to scroll through the file if you are viewing it from Windows.



Hello VOCX,


I ran, 
```

sudo modprobe r8169
sudo modprobe rtl8821ae
sudo service network-manager restart

```

however, it did not solve. Also I ran the wireless info script again, but same empty output. I am attaching the file anyway.


Also ,
```

dmesg -H | tail -40

```
 
some syntax issues maybe I replaced the -H with -h, however, the tail ain't giving me back anything. For your reference :

```




Usage:
 dmesg [options]


Options:
 -C, --clear                 clear the kernel ring buffer
 -c, --read-clear            read and clear all messages
 -D, --console-off           disable printing messages to console
 -d, --show-delta            show time delta between printed messages
 -E, --console-on            enable printing messages to console
 -f, --facility <list>       restrict output to defined facilities
 -h, --help                  display this help and exit
 -k, --kernel                display kernel messages
 -l, --level <list>          restrict output to defined levels
 -n, --console-level <level> set level of messages printed to console
 -r, --raw                   print the raw message buffer
 -s, --buffer-size <size>    buffer size to query the kernel ring buffer
 -T, --ctime                 show human readable timestamp (could be 
                             inaccurate if you have used SUSPEND/RESUME)
 -t, --notime                don't print messages timestamp
 -u, --userspace             display userspace messages
 -V, --version               output version information and exit
 -x, --decode                decode facility and level to readable string


Supported log facilities:
    kern - kernel messages
    user - random user-level messages
    mail - mail system
  daemon - system daemons
    auth - security/authorization messages
  syslog - messages generated internally by syslogd
     lpr - line printer subsystem
    news - network news subsystem


Supported log levels (priorities):
   emerg - system is unusable
   alert - action must be taken immediately
    crit - critical conditions
     err - error conditions
    warn - warning conditions
  notice - normal but significant condition
    info - informational
   debug - debug-level messages



```

So what can I do next?

---

### Post by arunavoster on 2017-07-26
Solution :
[https://medium.com/@elmaxx/rtl8821ae-wifi-drivers-in-ubuntu-16-04-4c1286524afa](https://medium.com/@elmaxx/rtl8821ae-wifi-drivers-in-ubuntu-16-04-4c1286524afa)

---

### Post by vocx on 2017-07-26
> **arunavoster said:**
> Solution :
[https://medium.com/@elmaxx/rtl8821ae-wifi-drivers-in-ubuntu-16-04-4c1286524afa](https://medium.com/@elmaxx/rtl8821ae-wifi-drivers-in-ubuntu-16-04-4c1286524afa)

There is somethings strange with your system if the wireless script doesn't work.

The "dmesg" command in your system seems to not have the "-H" option, so in any case, you should be able to run it without.
```

dmesg | tail -40

```

Anyways, according to your link, the solution was to download a new version of the "rtl8821ae" kernel module and compile that. I am not entirely sure if this is necessary in a more recent Ubuntu distribution like 17.04, as the newer the version of Ubuntu, the more recent the kernel drivers are. Maybe you only need to compile the source code in 14.04 and 16.04, as they have older kernels.

Now, please remember that the driver modules are tied to the version of the kernel against which you compiled. You can see this in the link you posted, as it asks you to download the "linux-headers". Every time you update your kernel, that is, after it bumps the last number, say 4.4.0-31 going to 4.4.0-32, you need to have the corresponding kernel headers, and you need to recompile the "rtl8821ae" module. So don't delete the "rtlwifi_new" folder that you downloaded. Keep it there for future use.

Also, it is not clear in your posts if you eventually decided to use 14.04, and not 16.04. My suggestion is that since 16.04 is more recent, and still an LTS version, you should use that. If the only problem you had with 16.04 was with the wireless, you should solve this by compiling the kernel module. After that, you should be able to continue using the system. My suggestion is to not stick too long with 14.04 because, although an LTS, you may eventually find that several packages in its repositories are quite old, and you may want to use more recent versions. Using 16.04 should give you a reasonably up to date system.

---

