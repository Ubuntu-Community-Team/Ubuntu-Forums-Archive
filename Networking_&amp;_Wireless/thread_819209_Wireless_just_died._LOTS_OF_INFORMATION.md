---
title: "Wireless just died. LOTS OF INFORMATION"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by FOBoi1122 on 2008-06-05
Hi guys, my wireless just died on me, and i'm trying to figure out why.

Here are some outputs:
jay@jay-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 14
       serial: 00:17:42:69:8b:e5
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.2.10 latency=0 module=sky2 multicast=yes
  *-network
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=iwl4965 latency=0 module=iwl4965



jay@jay-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:17:42:69:8b:e5  
          inet addr:192.168.2.10  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::217:42ff:fe69:8be5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:4860 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3639 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5428626 (5.1 MB)  TX bytes:385688 (376.6 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2096 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2096 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:105320 (102.8 KB)  TX bytes:105320 (102.8 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.63.1  Bcast:192.168.63.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.180.1  Bcast:172.16.180.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



and finally, i tried to do this.... 

jay@jay-laptop:~$ sudo cat /var/log/messages | grep switch
[sudo] password for jay: 
Jun  4 13:07:53 jay-laptop kernel: [   14.940266] SMP alternatives: switching to UP code
Jun  4 13:07:53 jay-laptop kernel: [   15.232882] SMP alternatives: switching to SMP code
Jun  4 13:07:53 jay-laptop kernel: [   30.117461] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun  4 13:33:27 jay-laptop kernel: [  111.577018] SMP alternatives: switching to UP code
Jun  4 13:33:27 jay-laptop kernel: [  111.868988] SMP alternatives: switching to SMP code
Jun  4 13:33:28 jay-laptop kernel: [  126.736685] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun  4 14:28:38 jay-laptop kernel: [   14.419923] SMP alternatives: switching to UP code
Jun  4 14:28:38 jay-laptop kernel: [   14.902407] SMP alternatives: switching to SMP code
Jun  4 14:28:38 jay-laptop kernel: [   25.431368] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun  4 14:49:52 jay-laptop kernel: [   14.543602] SMP alternatives: switching to UP code
Jun  4 14:49:52 jay-laptop kernel: [   15.026190] SMP alternatives: switching to SMP code
Jun  4 14:49:52 jay-laptop kernel: [   27.653251] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun  4 15:52:20 jay-laptop kernel: [   75.423172] SMP alternatives: switching to UP code
Jun  4 15:52:20 jay-laptop kernel: [    0.370461] SMP alternatives: switching to SMP code
Jun  4 16:30:09 jay-laptop kernel: [   14.623684] SMP alternatives: switching to UP code
Jun  4 16:30:09 jay-laptop kernel: [   15.106097] SMP alternatives: switching to SMP code
Jun  4 16:30:09 jay-laptop kernel: [   25.080099] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun  4 16:39:03 jay-laptop kernel: [   15.145457] SMP alternatives: switching to UP code
Jun  4 16:39:03 jay-laptop kernel: [   15.627967] SMP alternatives: switching to SMP code
Jun  4 16:39:03 jay-laptop kernel: [   25.370172] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun  4 17:17:40 jay-laptop kernel: [   95.353207] SMP alternatives: switching to UP code
Jun  4 17:17:40 jay-laptop kernel: [    0.371350] SMP alternatives: switching to SMP code
Jun  4 18:05:05 jay-laptop kernel: [   15.546008] SMP alternatives: switching to UP code
Jun  4 18:05:05 jay-laptop kernel: [   15.838572] SMP alternatives: switching to SMP code
Jun  4 18:05:05 jay-laptop kernel: [   30.430669] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun  4 18:05:05 jay-laptop kernel: [   33.091080] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:586: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x00bb0004
Jun  4 19:41:44 jay-laptop kernel: [  950.720218] SMP alternatives: switching to UP code
Jun  4 19:41:44 jay-laptop kernel: [    0.371396] SMP alternatives: switching to SMP code
Jun  4 23:31:51 jay-laptop kernel: [ 3701.960450] SMP alternatives: switching to UP code
Jun  4 23:31:51 jay-laptop kernel: [    0.367595] SMP alternatives: switching to SMP code
Jun  5 00:19:49 jay-laptop kernel: [   15.812343] SMP alternatives: switching to UP code
Jun  5 00:19:49 jay-laptop kernel: [   16.104374] SMP alternatives: switching to SMP code
Jun  5 00:19:49 jay-laptop kernel: [   31.678171] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun  5 00:21:48 jay-laptop kernel: [   14.894752] SMP alternatives: switching to UP code
Jun  5 00:21:48 jay-laptop kernel: [   15.186880] SMP alternatives: switching to SMP code
Jun  5 00:21:48 jay-laptop kernel: [   30.264651] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun  5 00:25:06 jay-laptop kernel: [   21.406614] SMP alternatives: switching to UP code
Jun  5 00:25:06 jay-laptop kernel: [   21.698758] SMP alternatives: switching to SMP code
Jun  5 00:25:06 jay-laptop kernel: [   37.023729] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun  5 01:31:36 jay-laptop kernel: [   18.950120] SMP alternatives: switching to UP code
Jun  5 01:31:36 jay-laptop kernel: [   19.432604] SMP alternatives: switching to SMP code
Jun  5 01:31:36 jay-laptop kernel: [   29.306255] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun  5 02:47:01 jay-laptop kernel: [   16.699931] SMP alternatives: switching to UP code
Jun  5 02:47:01 jay-laptop kernel: [   16.992567] SMP alternatives: switching to SMP code
Jun  5 02:47:01 jay-laptop kernel: [   33.261259] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun  5 02:47:01 jay-laptop kernel: [   35.007636] iwl4965: Radio disabled by HW RF Kill switch

and because i'm a complete newbie, i did  this for some reason because somewhere else on the forums did it...

jay@jay-laptop:~$ sudo tail -f /var/log/messages
Jun  5 02:53:43 jay-laptop kernel: [  444.322228] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun  5 02:53:43 jay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jun  5 02:53:46 jay-laptop kernel: [  446.573096] NET: Registered protocol family 17
Jun  5 02:53:47 jay-laptop dhcdbd: dhco_input_option: Value -1 cannot be converted to type L 
Jun  5 02:53:47 jay-laptop dhcdbd: dhco_parse_option_settings: bad option setting: new_dhcp_lease_time = -1 
Jun  5 02:53:47 jay-laptop dhcdbd: dhco_input_option: Value -1 cannot be converted to type L 
Jun  5 02:53:47 jay-laptop dhcdbd: dhco_parse_option_settings: bad option setting: old_dhcp_lease_time = -1 
Jun  5 02:53:47 jay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jun  5 02:53:47 jay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jun  5 02:53:47 jay-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers

hope all that helps?

---

### Post by chili555 on 2008-06-05
> iwl4965: Radio disabled by HW RF Kill switchThat's the problem. There is a switch or key combination on your laptop that turns the wireless radio off so you don't waste battery power when you are playing Frozen Bubble on the airplane.

Find those keys and punch them! My laptop have a physical switch, yours may have a combination like Fn+F2 or some such.

When you switch the switch on, you will see the event reported here:```
sudo tail -f /var/log/messages
```Leave the terminal open and watch while you push the switch or key.

When you re-activate wireless, Network Manager will not like giving an IP address when you already have one wired:> jay@jay-laptop:~$ ifconfig -a
eth0 Link encap:Ethernet HWaddr 00:17:42:69:8b:e5
inet addr:192.168.2.10 Bcast:192.168.2.255 Mask:255.255.255.0So, before you go wireless, please detach the wire.

---

### Post by FOBoi1122 on 2008-06-05
is there some way to find that key combination? because as far as i know, there's no key combination. is there a way to find it? I have a physical switch, but it's always been in the "on position" and i never really touched it. Although, i've noticed that in the separate LCD notifications display on my laptop, the wireless icon is turned off. But since it's a physical switch, i'm not sure how or if there is a soft key for it. is there some way to find how to enable it again?>

---

### Post by chili555 on 2008-06-05
Looks like it's a known bug! [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/193970](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/193970)

You might try:```
sudo su
echo '0' > /sys/class/net/wlan0/device/rf_kill
/etc/init.d/networking restart
```Did your wireless come to life? Does it survive a reboot?

---

### Post by FOBoi1122 on 2008-06-05
Hi, I'm not sure if I entered something wrong, but here it is:

root@jay-laptop:/home/jay# sudo su
root@jay-laptop:/home/jay# echo '0' > /sys/class/net/wlan0/device/rf_kill
bash: /sys/class/net/wlan0/device/rf_kill: No such file or directory

---

### Post by chili555 on 2008-06-05
I suppose it may be because wlan0 doesn't exist, yet. Notice there is no logical name in your *lshw* for your wireless device. Please detach the wire and try:```
sudo su
ifdown eth0
ifconfig wlan0 up
echo '0' > /sys/class/net/wlan0/device/rf_kill
/etc/init.d/networking restart
```What happens? Wireless again?

---

### Post by FOBoi1122 on 2008-06-05
Hi there, sorry but i got no luck....

root@jay-laptop:/home/jay# sudo su
root@jay-laptop:/home/jay# ifdown eth0
ifdown: interface eth0 not configured
root@jay-laptop:/home/jay# ifconfig wlan0 up
SIOCSIFFLAGS: No such device
root@jay-laptop:/home/jay# echo '0' > /sys/class/net/wlan0/device/rf_kill
bash: /sys/class/net/wlan0/device/rf_kill: No such file or directory
root@jay-laptop:/home/jay# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
root@jay-laptop:/home/jay# 

wireless still not working

---

### Post by chili555 on 2008-06-06
I have done some more reading here: [https://bugs.launchpad.net/ubuntu/+bug/230844](https://bugs.launchpad.net/ubuntu/+bug/230844)

Let's try:```
sudo su
rmmod iwl4965
modprobe iwl4965
echo '0' > /sys/class/net/wlan0/device/rf_kill
ifconfig
```Does your wlan0 now appear ready to configure and connect?

---

### Post by FOBoi1122 on 2008-06-07
Hi chili555,

sorry about the delay, I'm a student at a university and my finals week is comming up, so i've been preparing for that. but here's the output, again, with no luck =[

jay@jay-laptop:~$ sudo su
[sudo] password for jay: 
root@jay-laptop:/home/jay# rmmod iwl4965
root@jay-laptop:/home/jay# modprobe iwl4965
root@jay-laptop:/home/jay# echo '0' > /sys/class/net/wlan0/device/rf_kill
bash: /sys/class/net/wlan0/device/rf_kill: No such file or directory
root@jay-laptop:/home/jay# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:42:69:8b:e5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1864 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1864 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:93200 (91.0 KB)  TX bytes:93200 (91.0 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.63.1  Bcast:192.168.63.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.180.1  Bcast:172.16.180.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

