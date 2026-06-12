---
title: "Wireless requires roaming to be turned off and back on before connecting"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by pobbel on 2008-07-26
I am fairly new to linux (couple of weeks) and am trying to make the transition from Windows.  I have a problem with my wireless connection and am trying to work out what the cause is.

When I first boot up, I have no connectivity.  At this stage network manager has wireless set to roaming. The settings for my network are set in nm-editor (i.e. right clicking the nm-applet icon and selecting 'Edit Wireless Networks').

If I open terminal and type 'iwlist wlan0 scan', I get, 'wlan0     No scan results'.

However, if I open network manager (i.e. left click the nm-applet icon and select 'Manual configuration') and setup my network manually, it still will not connect.

But now when I type 'iwlist wlan0 scan', it now see's my wireless network.

I then change back to roaming which now connects automatically using the settings in nm-editor.

Why do I have to disable then re-enable roaming every time before I get connectivity, and why will it not connect in manual mode?



I am using Ubuntu Hardy with ndiswrapper.

I have tried with and without an ndiswrapper entry in /etc/modules.

I have checked to make sure there is an ndiswrapper alias in /etc/modprobe.d

I have removed and reinstalled network-manager and nm-applet

I tried to do a debug by typing 'sudo /etc/init.d/network-manager stop' but this file does not exist (possible problem here?)

I have been reading through the howto's and wiki's but am not sure what I should be looking for.

Any pointers would be greatly appreciated.

---

### Post by pobbel on 2008-07-26
okay to add to the above,  I have just read somewhere that left clicking nm-applet and selecting Manual configuration is actually opening network-admin (I think) this is where I disable and re-enable roaming before I can get connectivity in nm-applet (gnome front-end for network manager, right?)

---

### Post by pobbel on 2008-07-26
I did a check to see if the ndiswapper module was loaded at startup using

```
lsmod
```

ndiswrapper appears in the list, so I moved the alias file /etc/modprobe.d/ndiswapper to the /etc/modprobe.d/arch folder to make sure that the ndiswrapper module was being loaded by nm-applet using /etc/modules file.

After a reboot ```
lsmod
``` listed ndiswapper as being loaded.

I went through the process of disabling and re-enabling roaming to get the network up and running and then checking output of 

```
tail /var/log/messages
```

and got the following (I added notes after each process)

Jul 27 00:18:45 paul-laptop kernel: [   47.550561] [drm] Initialized radeon 1.28.0 20060524 on minor 0
Jul 27 00:18:46 paul-laptop kernel: [   48.261188] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Jul 27 00:18:46 paul-laptop kernel: [   48.261217] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Jul 27 00:18:46 paul-laptop kernel: [   48.261257] agpgart: Putting AGP V2 device at 0000:01:05.0 into 4x mode
Jul 27 00:18:47 paul-laptop kernel: [  181.723641] [drm] Setting GART location based on new memory map
Jul 27 00:18:47 paul-laptop kernel: [  181.723720] [drm] writeback test succeeded in 1 usecs
Jul 27 00:19:09 paul-laptop kernel: [  212.374552] NET: Registered protocol family 10
Jul 27 00:19:09 paul-laptop kernel: [  212.376055] lo: Disabled Privacy Extensions
Jul 27 00:19:09 paul-laptop kernel: [  212.378740] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 27 00:19:09 paul-laptop kernel: [  212.381322] ADDRCONF(NETDEV_UP): wlan0: link is not ready   
-------- After boot (Link LED only is flashing)----------------

Jul 27 00:22:26 paul-laptop kernel: [  133.105759] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 27 00:22:26 paul-laptop kernel: [  133.125585] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul 27 00:22:26 paul-laptop kernel: [  133.193865] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 27 00:22:27 paul-laptop kernel: [  134.106516] NET: Registered protocol family 17 
----- After disabling roaming using Network Admin (Both Link and Act LEDs Flashing) but still no connection ---------

Jul 27 00:23:50 paul-laptop kernel: [  165.157143] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 27 00:23:50 paul-laptop kernel: [  165.189797] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul 27 00:24:01 paul-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Jul 27 00:24:14 paul-laptop kernel: [  648.264938] ndiswrapper (iw_set_freq:334): setting configuration failed (C0010015)
Jul 27 00:24:14 paul-laptop kernel: [  648.354222] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul 27 00:24:18 paul-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.domain_name
Jul 27 00:24:18 paul-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Jul 27 00:24:18 paul-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Jul 27 00:24:18 paul-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu
----After re-enabling roaming and falling back to Network manager (Link LED goes solid, Act LED flashes) connection established---------


Can anyone see anything obviously wrong with my setup?

Can anyone tell me what else I should be looking for?

---

### Post by pobbel on 2008-07-26
I have now tried unistalling network manager and then installing wicd.  

When wicd is installed ```
iwlist wlan0 scan 
``` sees my network and wicd shows my network, but I could not get it to connect.:(

Just in case I was complicating the problem, I uninstalled wicd and reverted back to Network Manager.  Still with the same old problem of having to open Network Admin and disabling roaming then re-enabling roaming before my wireless will connect.

For something that is supposed to "Just work" it is frustrating me to no end.

I am at a loss as to what is going on.  It is probably something simple as a result of the newbie factor.

Could somebody please help me with this problem?

Thanks in advance.

---

### Post by pobbel on 2008-07-27
Should I report this as a bug?

---

### Post by roachk71 on 2008-07-27
There are quite a few wireless interfaces that don't play nice, due to patent and other legal issues; several manufacturers refuse to release the specifications of their devices to the open source community, and reverse-engineering does take time.

First of all, what brand and model (including version and/or revision) of card are you trying to use?

I'll look the information up in the HCL and Ndiswrapper sites, and report back.

---

### Post by pobbel on 2008-07-27
roachk71 firstly thanks for your reply

I am using a Draytek Vigor 560 PCMCIA card using the Linksys INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01) chipset (17fe:2220)

I have used the driver supplied by Draytek and have also tried a driver listed on the ndiswrapper site (FoxCom driver supplied for various Acer Aspire laptops).  The different drivers did not make any noticable difference, they both seemed to work the same.

I am using ndiswrapper 1.52 and in the past tried to upgrade to 1.53 but that required compiling and installing manually as this is not the version that is supplied in the hardy repositories.  Needless to say, this was a huge failure, and when I reverted back to 1.52, it no longer loaded properly.  I had some help to rectify this.  The module was loaded into the wrong kernel version or something like that (way over my head at this stage to fully understand what was wrong), whatever the problem was, the ndiswrapper module was not being loaded. That is sorted now.

Anyway let me know if you need any further info, or if there is anything I can else I can check or try.

---

### Post by pobbel on 2008-07-27
I have been playing around with this problem and may have found something.

If I type
```
iwlist wlan scan
```
after boot.  It does not see my network

and 

```
iwconfig wlan0
```

gives

```
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:0 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Here's what I have discovered

If I enter

```
iwconfig wlan0 essid any
```

then after a few seconds

```
iwlist wlan scan
```

now lists my network and a connection is soon established.

This is the sort of thing I have been looking for.

Now what do I do?
How can I get this to happen when I boot?
Will it be possible to enable this before I login?

---

### Post by pobbel on 2008-07-27
is this normal even though
"iwconfig wlan0" says that the essid is already set to off/any?

---

### Post by roachk71 on 2008-07-28
This would appear to be another bug in Network Manager (or its panel applet.)

Although the solution I describe here may be inconvenient, it usually results in a more stable connection:


[LIST=1]
[*]Open Synaptic Package Manager, and mark both network-manager and network-manager-gnome for removal, then click Apply. As mentioned, there may be issues with either or both which need to be addressed (it should also be mentioned here that NM has in the past interfered with 'any ESSID' association.)
[*]Manually configure (through the Network Properties dialog) the settings for your access point or router. Most routers and gateways allow the use of DHCP-generated addresses. Also, be sure you write down the router's WEP or WPA key, so it can be copied into the Key dialog (if one is used.)
[/LIST]
Unfortunately, a Network Manager-specific solution may not be immediately forthcoming.

I hope the information presented in this reply is more helpful.

Update to Previous Reply: I couldn't find your card or chipset in either the Ubuntu HCL or the Ndiswrapper list of known cards.

---

