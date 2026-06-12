---
title: "Lubuntu 16.10 - Ethernet not working"
date: 2017-02-23
forum: Networking &amp; Wireless
---

### Post by pelai on 2017-02-23
Hi!

I've been struggling with the network connections since I installed Lubuntu 16.10 with alternate iso on my Sony Vaio Notebook Model PCG-21313M. The WiFi connection is finnaly working (you can see the solution in [this thread]("https://ubuntuforums.org/showthread.php?t=2352873")), but the ethernet is still not working.

I've tried installing ethtool but this is the result:

```

$ sudo apt-get install ethtool
[sudo] password for pelai:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package ethtool is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package 'ethtool' has no installation candidate

```

I'm quite new with linux and ubuntu.

Thank you!

---

### Post by chili555 on 2017-02-23
Please try:```
sudo apt-get update
sudo apt-get install ethtool
```Now does it install?

Next, let's have a look at the log:```
dmesg | grep -e enp -e jme
```

---

### Post by pelai on 2017-02-24
Hi!

I've updated an then the installation was successful. But the ethernet connection is still not working... and when clicking on the Networks button on the taskbar it shows those messages regarding Ethernet Networks:

Ethernet Network
device not managed

This is the outcome of the dsmeg command:
```

pelai@Petit-Vaio:~$ dmesg | grep -e enp -e jme
[    3.363492] jme: JMicron JMC2XX ethernet driver version 1.0.8
[    3.370853] jme 0000:02:00.5 eth0: JMC260 Fast Ethernet chiprev:22 pcirev:2 macaddr:54:42:49:0e:d2:f2
[    3.685753] jme 0000:02:00.5 enp2s0f5: renamed from eth0

```

---

### Post by chili555 on 2017-02-24
> device not managedAh, haaaa!!

Please let us see:```
cat /etc/NetworkManager/NetworkManager.conf
```And also:```
cat /etc/network/interfaces
```One of the two is malformed.

---

### Post by Bashing-om on 2017-02-24
pelai; Hummm ...

As this is " Lubuntu 16.10 with alternate iso " ....
I am not sure that network-manager is installed by default .. 
show us:
```

dpkg -l network-manager

```
such that then it it is the file /etc/network/interfaces that controls networking.
Please post:
```

cat /etc/network/interfaces

```
to see what we are working with (enp2s0f5 ??)

[INDENT][INDENT]a failure to communicate
[/INDENT][/INDENT]

---

### Post by pelai on 2017-02-26
Hi!

These are the outcomes.
```

pelai@Petit-Vaio:~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false
pelai@Petit-Vaio:~$ 
pelai@Petit-Vaio:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback
pelai@Petit-Vaio:~$ 
pelai@Petit-Vaio:~$ dpkg -l network-manager
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                      Version           Architecture      Description
+++-=========================-=================-=================-=======================================================
ii  network-manager           1.2.6-0ubuntu1    i386              network management framework (daemon and userspace tool

```

---

### Post by Bashing-om on 2017-02-26
pelai; Well ....

what pray tell are you doing here:
source /etc/network/interfaces.d/*

Unless you are up for something non-standard, there is no reason to mess about with what network-manager is doing . And even then if ya messing with networking manually you would not want to use network-manager on the system . You would then control networking from the config files.

[INDENT][INDENT]seems reasonable to me
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2017-02-26
pelai; Hey !!

It has been brought to my attention that beginning in 16.10 " source /etc/network/interfaces.d/* " is default .
I would still be interested in knowing what it's purpose is.

[INDENT][INDENT]fast moving target that it is
[/INDENT][/INDENT]

---

### Post by chili555 on 2017-02-27
Both of the files I requested look perfect to me. This is my (least) favorite kind of problem; everything looks great but it doesn't work.

Let's dig deeper; with the ethernet cable attached:```
dmesg | grep -e jme -e enp
cat /var/log/syslog | grep etwork | tail -n 10
ps aux | grep etwork
```

---

### Post by pelai on 2017-03-04
Hi chili555,

this is the outcome.

```

pelai@Petit-Vaio:~$ dmesg | grep -e jme -e enp
[    3.392918] jme: JMicron JMC2XX ethernet driver version 1.0.8
[    3.394661] jme 0000:02:00.5 eth0: JMC260 Fast Ethernet chiprev:22 pcirev:2 macaddr:54:42:49:0e:d2:f2
[    3.698939] jme 0000:02:00.5 enp2s0f5: renamed from eth0
pelai@Petit-Vaio:~$ 
pelai@Petit-Vaio:~$ 
pelai@Petit-Vaio:~$ dmesg | grep -e jme -e enp
[    3.392918] jme: JMicron JMC2XX ethernet driver version 1.0.8
[    3.394661] jme 0000:02:00.5 eth0: JMC260 Fast Ethernet chiprev:22 pcirev:2 macaddr:54:42:49:0e:d2:f2
[    3.698939] jme 0000:02:00.5 enp2s0f5: renamed from eth0
pelai@Petit-Vaio:~$ 
pelai@Petit-Vaio:~$ 
pelai@Petit-Vaio:~$ cat /var/log/syslog | grep etwork | tail -n 10
Mar  4 10:24:30 Petit-Vaio NetworkManager[811]: <info>  [1488619470.1716] device (wlp1s0): supplicant interface state: authenticating -> associated
Mar  4 10:24:30 Petit-Vaio NetworkManager[811]: <info>  [1488619470.1761] device (wlp1s0): supplicant interface state: associated -> 4-way handshake
Mar  4 10:24:30 Petit-Vaio NetworkManager[811]: <info>  [1488619470.1779] device (wlp1s0): supplicant interface state: 4-way handshake -> completed
Mar  4 10:42:37 Petit-Vaio NetworkManager[811]: <warn>  [1488620557.5953] sup-iface[0x8c1de00,wlp1s0]: connection disconnected (reason -4)
Mar  4 10:42:37 Petit-Vaio NetworkManager[811]: <info>  [1488620557.6172] device (wlp1s0): supplicant interface state: completed -> disconnected
Mar  4 10:42:37 Petit-Vaio NetworkManager[811]: <info>  [1488620557.6995] device (wlp1s0): supplicant interface state: disconnected -> scanning
Mar  4 10:42:39 Petit-Vaio NetworkManager[811]: <info>  [1488620559.2579] device (wlp1s0): supplicant interface state: scanning -> authenticating
Mar  4 10:42:39 Petit-Vaio NetworkManager[811]: <info>  [1488620559.2601] device (wlp1s0): supplicant interface state: authenticating -> associating
Mar  4 10:42:39 Petit-Vaio NetworkManager[811]: <info>  [1488620559.2629] device (wlp1s0): supplicant interface state: associating -> 4-way handshake
Mar  4 10:42:39 Petit-Vaio NetworkManager[811]: <info>  [1488620559.2693] device (wlp1s0): supplicant interface state: 4-way handshake -> completed
pelai@Petit-Vaio:~$ 
pelai@Petit-Vaio:~$ 
pelai@Petit-Vaio:~$ 
pelai@Petit-Vaio:~$ ps aux | grep etwork
root       811  0.2  1.7 111916 17580 ?        Ssl  10:10   0:06 /usr/sbin/NetworkManager --no-daemon
root      1077  0.0  0.3   6040  3244 ?        S    10:10   0:00 /sbin/dhclient -d -q -sf /usr/lib/NetworkManager/nm-dhcp-helper -pf /var/run/dhclient-wlp1s0.pid -lf /var/lib/NetworkManager/dhclient-97e5afcb-5614-41ff-bc11-0f3858b8c3a2-wlp1s0.lease -cf /var/lib/NetworkManager/dhclient-wlp1s0.conf wlp1s0
nobody    1144  0.0  0.3  10544  4040 ?        S    10:10   0:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/var/run/NetworkManager/dnsmasq.pid --listen-address=127.0.1.1 --cache-size=0 --conf-file=/dev/null --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d
pelai     2244  0.0  0.0   6372   848 pts/0    S+   11:02   0:00 grep --color=auto etwork


```

---

### Post by chili555 on 2017-03-04
Well, once again, everything looks just fine. We see nothing to repair!

Your syslog shows a good connection to wireless. I'd love to see the same thing with wifi disabled at the Network Manager icon; in other words, try to force NM to activate ethernet and not wireless and then:```
cat /var/log/syslog | grep etwork | tail -n 10
```When I run this:```
modinfo jme
```I notice this interesting parameter in your driver:```
parm:           force_pseudohp:Enable pseudo hot-plug feature manually by driver instead of BIOS. (int)
```Verrrry interesting! Will you please check the BIOS to see if there is any setting related to ethernet? What is it?

In the meantime, let's experiment:```
sudo modprobe -r jme
sudo modprobe jme force_pseudohp=1
```Any improvement?

Also please try:```
sudo ethtool -s enp2s0f5 autoneg off speed 100 duplex full

```Any change?

What does this tell us?```
sudo ethtool enp2s0f5
```

---

### Post by pelai on 2017-03-07
I've tried all the command you send me, but nothing seems to work.. 

On the BIOS there was no setting related with the ethernet.

This is the output of the last command:

```

pelai@Petit-Vaio:~$ sudo ethtool enp2s0f5
Settings for enp2s0f5:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 10Mb/s
    Duplex: Half
    Port: MII
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pg
    Wake-on: g
    Current message level: 0x000020c6 (8390)
                   probe link rx_err tx_err hw
    Link detected: no

```

---

### Post by chili555 on 2017-03-08
> pelai@Petit-Vaio:~$ sudo ethtool enp2s0f5
Settings for enp2s0f5:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 10Mb/s
    Duplex: Half
    Port: MII
    PHYAD: 1
    Transceiver: internal
    [COLOR="#FF0000"]Auto-negotiation: on[/COLOR]
    Supports Wake-on: pg
    Wake-on: g
    Current message level: 0x000020c6 (8390)
                   probe link rx_err tx_err hw
    [COLOR="#FF0000"]Link detected: no[/COLOR]I've highlighted two things of interest here. 

First, in a previous command, you attempted to turn autonegotiation off; however, it reports as ON. Let's try again:```
sudo ethtool -s enp2s0f5 autoneg off speed 100 duplex full
sudo ethtool enp2s0f5
```Is it off now?

Second, and possibly critical is 'Link detected:no.' That suggests that the device is unaware of any ethernet router, switch or modem at the other end of the cable. Are you quite certain that the cable is good, seated properly at both ends, etc.? Please try another known good cable and re-check:```
sudo ethtool enp2s0f5
```

Possible issue: [http://superuser.com/questions/536748/plugged-in-network-cable-is-not-detected-possibly-related-to-green-ethernet](http://superuser.com/questions/536748/plugged-in-network-cable-is-not-detected-possibly-related-to-green-ethernet)

---

### Post by pelai on 2017-03-09
Hi!

I've turned autonegotiation off succesfully but the link detection is still "not". I've also changed the ethernet cable with another one that I'm using in another computer where the connection is correct and there was no improvement. In fact I switched the cables and both of them work on the other computer but not in this one...

---

### Post by chili555 on 2017-03-09
I tracked down the referenced 1.0.8.5 driver version and it won't compile in any recent Ubuntu version.

Both this:> I haven't read the manual yet so I can't tell you how to do it, but see if you can turn off the Green Networking for the one port your Shuttle is connected to (and leave the auto-negotiation on) and see what happens....and this:> I got rid of the D-Link DIR-652 router and bought a TP-Link TL-WDR3600 instead. With that, I initially had exactly the same problem. Then I installed the DD-WRT firmware, and suddenly, the issue vanished....suggest that it may be fixed by settings in the router. I suggest that you look around in the router and see what can be changed.

Aside from that, I regret that I have no other suggestions aside from buying any number of inexpensive NIC cards to replace the JMicron.

---

### Post by parkerd3 on 2017-03-24
Thank you for helping.  I tried what you suggested for Pelai.  My Xubuntu machine is a Compac Presario, AMD X2 4450a dual core, and wired ethernet only: there is no wifi capability on the computer (the modem is capable of wifi).   I suffer the ignominy of using a windows 7 platform for this communication.  
I would appreciate knowing what file to download onto a win7 platform that can restore wired ethernet on the Xubuntu 16.10 machine using a flashdrive.

```
d@Xu:~$ nmcli g
STATE         CONNECTIVITY  WIFI-HW  WIFI     WWAN-HW  WWAN    
disconnected  none          enabled  enabled  enabled  enabled 
```


```
d@Xu:~$ nmcli n
enabled
```


```
d@Xu:~$ nmcli r
WIFI-HW  WIFI     WWAN-HW  WWAN    
enabled  enabled  enabled  enabled 
```

```
d@Xu:~$ nmcli c
NAME                UUID                                  TYPE            DEVICE 
Wired connection 1  1ed3b6ea-e815-4fde-b882-588cfd64d0d9  802-3-ethernet  --    
``` 


```
d@Xu:~$ nmcli d
DEVICE      TYPE      STATE      CONNECTION 
virbr0      bridge    unmanaged  --         
enp0s7      ethernet  unmanaged  --         
lo          loopback  unmanaged  --         
virbr0-nic  tun       unmanaged  --       
```  


```
d@Xu:~$ nmcli a
nmcli successfully registered as a NetworkManager's secret agent.


** (process:3619): WARNING **: Unable to register authentication agent: GDBus.Errorrg.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject
```




```
d@Xu:~$ sudo apt-get install ethtool
[sudo] password for d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ethtool is already the newest version (1:4.6-1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```


```
d@Xu:~$ sudo ethtool -s enp0s75 autoneg off speed 100 duplex full
Cannot get current device settings: No such device
  not setting speed
  not setting duplex
  not setting autoneg
```


```
d@Xu:~$ dpkg -l network-manager
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                              Version               Architecture          Description
+++-=================================-=====================-=====================-========================================================================
ii  network-manager                   1.2.6-0ubuntu1        amd64                 network management framework (daemon and userspace tools)
```


```
d@Xu:~$ dmesg | grep -e enp -e jme
[  128.124257] forcedeth 0000:00:07.0 enp0s7: renamed from eth0
[ 1451.136542] jme: JMicron JMC2XX ethernet driver version 1.0.8
[ 1489.906843] jme: JMicron JMC2XX ethernet driver version 1.0.8
```




```
d@Xu:~$ cat /var/log/syslog | grep etwork | tail -n 10
Mar 24 08:09:18 Xu gvfsd-network[3447]: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Mar 24 08:09:21 Xu gvfsd-network[3450]: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Mar 24 08:09:24 Xu gvfsd-network[3461]: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Mar 24 08:09:27 Xu gvfsd-network[3455]: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Mar 24 08:09:30 Xu gvfsd-network[3443]: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Mar 24 08:09:33 Xu gvfsd-network[3441]: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
```




```
d@Xu:~$ ps aux | grep etwork
root      1249  0.0  0.5 468028 16700 ?        Ssl  07:59   0:00 /usr/sbin/NetworkManager --no-daemon
d         3447  0.0  0.2 435544  6920 ?        Sl   08:09   0:00 /usr/lib/gvfs/gvfsd-network --spawner :1.17 /org/gtk/gvfs/exec_spaw/3
d         3760  0.0  0.0  14228   928 pts/7    S+   08:40   0:00 grep --color=auto etwork
```

---

### Post by chili555 on 2017-03-24
> I would appreciate knowing what file to download onto a win7 platform that can restore wired ethernet on the Xubuntu 16.10 machine using a flashdrive.
I know of none.

As I said, I regret that I have no other suggestions aside from buying any number of inexpensive NIC cards to replace the JMicron.

---

