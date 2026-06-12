---
title: "USB modem installation"
date: 2020-04-26
forum: Networking &amp; Wireless
---

### Post by aneczkaby on 2020-04-26
Hello All,
I am new to this forum. I am new to any forum at all.
 I know that this topic was discussed many times but I could not find a relevant thread or the information is missing.

I have a USB modem - the most popular - Huawei E3372 and it works great on a desktop installation of my new ubuntu 20.4 but... it does not work on the ubunto 20.4 server instance. I have no idea what is the matter.

Here below is the output from syslog on the server:
==================================================

pr 26 12:10:36 m-sam kernel: [15756.620331] usb 2-1.5: new high-speed USB device number 9 using ehci-pci
Apr 26 12:10:36 m-sam kernel: [15756.650804] usb 2-1.5: New USB device found, idVendor=12d1, idProduct=1f01, bcdDevice= 1.02
Apr 26 12:10:36 m-sam kernel: [15756.650810] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Apr 26 12:10:36 m-sam kernel: [15756.650814] usb 2-1.5: Product: HUAWEI_MOBILE
Apr 26 12:10:36 m-sam kernel: [15756.650817] usb 2-1.5: Manufacturer: HUAWEI_MOBILE
Apr 26 12:10:36 m-sam kernel: [15756.650821] usb 2-1.5: SerialNumber: 0123456789ABCDEF
Apr 26 12:10:36 m-sam kernel: [15756.651818] usb-storage 2-1.5:1.0: USB Mass Storage device detected
Apr 26 12:10:36 m-sam kernel: [15756.652130] scsi host5: usb-storage 2-1.5:1.0
Apr 26 12:10:36 m-sam mtp-probe: checking bus 2, device 9: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5"
Apr 26 12:10:36 m-sam mtp-probe: bus: 2, device: 9 was not an MTP device
Apr 26 12:10:36 m-sam systemd[1]: Starting USB_ModeSwitch_2-1.5:1.0...
Apr 26 12:10:36 m-sam usb_modeswitch_dispatcher[3241]: Could not read attribute: No such file or directory
Apr 26 12:10:36 m-sam usb_modeswitch_dispatcher[3241]: message repeated 2 times: [ Could not read attribute: No such file or directory]
Apr 26 12:10:36 m-sam mtp-probe: checking bus 2, device 9: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5"
Apr 26 12:10:36 m-sam mtp-probe: bus: 2, device: 9 was not an MTP device
Apr 26 12:10:37 m-sam kernel: [15757.681529] scsi 5:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Apr 26 12:10:37 m-sam kernel: [15757.682384] scsi 5:0:0:1: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
Apr 26 12:10:37 m-sam kernel: [15757.683883] sr 5:0:0:0: Power-on or device reset occurred
Apr 26 12:10:37 m-sam kernel: [15757.686150] sr 5:0:0:0: [sr1] scsi-1 drive
Apr 26 12:10:37 m-sam kernel: [15757.708793] sr 5:0:0:0: Attached scsi CD-ROM sr1
Apr 26 12:10:37 m-sam kernel: [15757.708959] sr 5:0:0:0: Attached scsi generic sg2 type 5
Apr 26 12:10:37 m-sam kernel: [15757.709281] scsi 5:0:0:1: Attached scsi generic sg3 type 0
Apr 26 12:10:37 m-sam kernel: [15757.710504] sd 5:0:0:1: Power-on or device reset occurred
Apr 26 12:10:37 m-sam usb_modeswitch: switch device 12d1:1f01 on 002/009
Apr 26 12:10:37 m-sam kernel: [15757.734128] sd 5:0:0:1: [sdb] Attached SCSI removable disk
Apr 26 12:10:37 m-sam kernel: [15757.734137] scsi 5:0:0:0: rejecting I/O to dead device
Apr 26 12:10:37 m-sam multipath: sdb: can't store path info
Apr 26 12:10:37 m-sam kernel: [15757.883549] usb 2-1.5: USB disconnect, device number 9
Apr 26 12:10:37 m-sam kernel: [15758.248311] usb 2-1.5: new high-speed USB device number 10 using ehci-pci
Apr 26 12:10:37 m-sam kernel: [15758.278270] usb 2-1.5: New USB device found, idVendor=12d1, idProduct=14dc, bcdDevice= 1.02
Apr 26 12:10:37 m-sam kernel: [15758.278275] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Apr 26 12:10:37 m-sam kernel: [15758.278279] usb 2-1.5: Product: HUAWEI_MOBILE
Apr 26 12:10:37 m-sam kernel: [15758.278282] usb 2-1.5: Manufacturer: HUAWEI_MOBILE
Apr 26 12:10:37 m-sam kernel: [15758.282379] cdc_ether 2-1.5:1.0 eth0: register 'cdc_ether' at usb-0000:00:1d.0-1.5, CDC Ethernet Device, 0c:5b:8f:27:9a:64
Apr 26 12:10:37 m-sam kernel: [15758.283056] usb-storage 2-1.5:1.2: USB Mass Storage device detected
Apr 26 12:10:37 m-sam multipath: sdb: can't store path info
Apr 26 12:10:37 m-sam networkd-dispatcher[763]: WARNING:Unknown index 8 seen, reloading interface list
Apr 26 12:10:37 m-sam kernel: [15758.288462] scsi host5: usb-storage 2-1.5:1.2
Apr 26 12:10:37 m-sam mtp-probe: checking bus 2, device 10: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5"
Apr 26 12:10:37 m-sam mtp-probe: bus: 2, device: 10 was not an MTP device
Apr 26 12:10:37 m-sam systemd-udevd[3261]: Using default interface naming scheme 'v245'.
Apr 26 12:10:38 m-sam systemd-udevd[3261]: ethtool: autonegotiation is unset or enabled, the speed and duplex are not writable.
Apr 26 12:10:38 m-sam kernel: [15758.312428] cdc_ether 2-1.5:1.0 enx0c5b8f279a64: renamed from eth0
Apr 26 12:10:38 m-sam systemd-networkd[735]: eth0: Interface name change detected, eth0 has been renamed to enx0c5b8f279a64.
Apr 26 12:10:38 m-sam networkd-dispatcher[763]: WARNING:Unknown index 8 seen, reloading interface list
Apr 26 12:10:38 m-sam mtp-probe: checking bus 2, device 10: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5"
Apr 26 12:10:38 m-sam mtp-probe: bus: 2, device: 10 was not an MTP device
Apr 26 12:10:38 m-sam usb_modeswitch_dispatcher[3241]: Could not read attribute: No such file or directory
Apr 26 12:10:38 m-sam usb_modeswitch[3241]: usb_modeswitch: switched to 12d1:14dc on 2/10
Apr 26 12:10:38 m-sam multipathd[616]: sdb: path already removed
Apr 26 12:10:39 m-sam kernel: [15759.313540] scsi 5:0:0:0: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
Apr 26 12:10:39 m-sam kernel: [15759.313979] sd 5:0:0:0: Attached scsi generic sg2 type 0
Apr 26 12:10:39 m-sam kernel: [15759.314612] sd 5:0:0:0: Power-on or device reset occurred
Apr 26 12:10:39 m-sam kernel: [15759.329257] sd 5:0:0:0: [sdb] Attached SCSI removable disk
Apr 26 12:10:39 m-sam multipath: sdb: can't store path info
Apr 26 12:10:39 m-sam multipathd[616]: uevent trigger error
Apr 26 12:10:39 m-sam multipath: sdb: can't store path info
Apr 26 12:10:39 m-sam multipath: sdb: can't store path info
Apr 26 12:10:39 m-sam usb_modeswitch_dispatcher[3241]: Unable to open bind list file: No such file or directory
Apr 26 12:10:39 m-sam usb_modeswitch[3241]: usb_modeswitch: add device ID 12d1:14dc to driver option
Apr 26 12:10:39 m-sam usb_modeswitch[3241]: usb_modeswitch: please report the device ID to the Linux USB developers!
Apr 26 12:10:40 m-sam multipathd[616]: sdb: spurious uevent, path not found
Apr 26 12:10:40 m-sam multipathd[616]: uevent trigger error
Apr 26 12:10:40 m-sam multipathd[616]: sdb: spurious uevent, path not found
Apr 26 12:10:40 m-sam multipathd[616]: uevent trigger error
Apr 26 12:10:40 m-sam ModemManager[3186]: <info>  Couldn't check support for device '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5': not supported by any plugin
Apr 26 12:10:46 m-sam systemd[1]: [email]usb_modeswitch@2-1.5:1.0.servic[/email]e: Succeeded.
Apr 26 12:10:46 m-sam systemd[1]: Finished USB_ModeSwitch_2-1.5:1.0.

======================================================

$ ip link
8: enx0c5b8f279a64: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ether 0c:5b:8f:27:9a:64 brd ff:ff:ff:ff:ff:ff

I have tried to follow 'ModemManager installation and configuration manual' but I have failed on the first step:

======================================
$ systemctl status snap.modem-manager.modemmanager.service&#9679; snap.modem-manager.modemmanager.service - Service for snap application modem-manager.modemmanager
     Loaded: loaded (/etc/systemd/system/snap.modem-manager.modemmanager.service; enabled; vendor preset: enabled)
     Active: inactive (dead) since Sun 2020-04-26 11:36:26 UTC; 46min ago
    Process: 2932 ExecStart=/usr/bin/snap run modem-manager.modemmanager (code=exited, status=0/SUCCESS)
   Main PID: 2932 (code=exited, status=0/SUCCESS)

kwi 26 11:36:24 m-sam systemd[1]: Started Service for snap application modem-manager.modemmanager.
kwi 26 11:36:24 m-sam modem-manager.modemmanager[2932]: + export SNAP_APP_PATH=/snap/modem-manager/414
kwi 26 11:36:24 m-sam modem-manager.modemmanager[2932]: + LOG_LEVEL=INFO
kwi 26 11:36:24 m-sam modem-manager.modemmanager[2932]: + DEBUG=
kwi 26 11:36:24 m-sam modem-manager.modemmanager[2932]: + [ -f /var/snap/modem-manager/414/.debug_enabled ]
kwi 26 11:36:24 m-sam modem-manager.modemmanager[2932]: + exec /snap/modem-manager/414/usr/sbin/ModemManager --filter-policy=STRICT>
kwi 26 11:36:25 m-sam ModemManager[2932]: <info>  ModemManager (version 1.10.0) starting in system bus...
kwi 26 11:36:26 m-sam ModemManager[2932]: <warn>  Could not acquire the 'org.freedesktop.ModemManager1' service name
kwi 26 11:36:26 m-sam ModemManager[2932]: <info>  ModemManager is shut down
kwi 26 11:36:26 m-sam systemd[1]: snap.modem-manager.modemmanager.service: Succeeded.

$ mmcli -L
No modems were found

======================================

What should I do? What to check more, what to change?

Thanks for any support.

BTW: I have tried to find how the procedure of the new USB device (modem) installation looks like. What is the first step, the second. Which process comes first, how to debug it etc. Could anyone redirect me to relevant source, please?

BRs,
Aneczka

---

### Post by chili555 on 2020-04-26
Frankly, it appears that you are 90% done already!

Your device is, with some bumps in the road, recognized as an external ethernet device; in your case, enx0c5b8f279a64. Let's try the quick and dirty steps first and see how it goes:

```
sudo ip link set  enx0c5b8f279a64 up
sudo dhclient -v enx0c5b8f279a64

```
Do you get an IP address? Any warnings, errors or other problems? 

Typically, in recent Ubuntu versions, networking in servers is configured using netplan. Please check:

```
cat /etc/netplan/*.yaml
```

And also:

```
cat /usr/share/doc/netplan/examples/modem.yaml
```

---

### Post by aneczkaby on 2020-04-26
I was so close :-) Thanks.

$ cat /etc/netplan/*.yaml
# This is the network config written by 'subiquity'
network:
  ethernets:
    enp7s0:
      dhcp4: true
  version: 2

$ cat /usr/share/doc/netplan/examples/modem.yaml
network:
  version: 2
  renderer: NetworkManager
  modems:
    cdc-wdm1:
      mtu: 1600
      apn: ISP.CINGULAR
      username: [email]ISP@CINGULARGPRS.COM[/email]
      password: CINGULAR1
      number: "*99#"
      network-id: 24005
      device-id: da812de91eec16620b06cd0ca5cbc7ea25245222
      pin: 1111
      sim-id: 89148000000011111234
      sim-operator-id: 310260

How to make it fly at the boottime? I do not expect to shut the server down but in such case I would appreciate to recover automatically.
And how can I change the APN?

Thanks
Aneczka

---

### Post by chili555 on 2020-04-26
I don't know much about modems and I certainly don't know if all the data in the example needs to be suppiled in order to connect. I believe that the idea is to adapt the yaml file you have to fit your modem setup and the password details, etc. that your ISP requires to connect, if any.

You said that the modem worked perfectly in a desktop installation. Did you need to supply credentials, passwords, etc. in Network Manager to get it to connect?

What was the result of the dhclient command?

---

### Post by chili555 on 2020-04-26
More information from the command:

```
man netplan
```

> Properties for device type modems:
       [COLOR="#FF0000"]GSM/CDMA  modem  configuration is only supported for the NetworkManager[/COLOR]
       backend.  systemd-networkd does not support modems.

       apn (scalar)
              Set the carrier APN (Access Point Name).  This can be omitted if
              auto-config is enabled.

       auto-config (bool)
              Specify  whether  to  try and autoconfigure the modem by doing a
              lookup of the carrier  against  the  Mobile  Broadband  Provider
              database.  This may not work for all carriers.

       device-id (scalar)
              Specify  the device ID (as given by the WWAN management service)
              of the modem to match.  This can be found using mmcli.

       network-id (scalar)
              Specify the Network ID (GSM LAI format).  If this is  specified,
              the device will not roam networks.
<snip>
You may need to have NM installed and running to proceed.

---

