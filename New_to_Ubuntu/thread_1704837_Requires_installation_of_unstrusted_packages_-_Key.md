---
title: "Requires installation of unstrusted packages - KeysServer issues."
date: 2011-03-11
forum: New to Ubuntu
---

### Post by Narchie on 2011-03-11
Hi,

I have been trying to get keys from keyserver.ubuntu.com

Basically I have been trying to follow the instructions [here]("http://www.liberiangeek.net/2010/10/fix-requires-installation-untrusted-packages-error-ubuntu-10-10-maverick-meerkat/") 

After running sudo apt-get update

I get the following list of keys that I need to get:

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B725097B3ACC3965
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B725097B3ACC3965
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 500E60CE43C56F3F
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40C18E9EC07EE05F
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8771ADB0816950D8


When I run 
sudo apt-key adv --recv-key --keyserver keyserver.ubuntu.com 8771ADB0816950D8

It ends with the following error:

> Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-key --keyserver keyserver.ubuntu.com 8771ADB0816950D8
gpg: requesting key 816950D8 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error


Any suggestions?

I have also tried different keyservers.

Thank you in advance
 :)

---

### Post by Hippytaff on 2011-03-11
are you running behind a proxy server?

---

### Post by Narchie on 2011-03-11
Yes I am but I installed NTMLAPS as well as tried manually entering 
export http_proxy=http://xxx.xxx.xxx.xxx:80

I can install apps without any issues via terminal (thanks to NTMLAPS)

---

### Post by Hippytaff on 2011-03-11
Maybe have a go without the proxy...then if that works you can look into it in more depth, but at least you get your keys

---

### Post by Narchie on 2011-03-11
Will have to set up a 3g modem for that.

Ahh well, Monday, off home now.

Thank you for the assistance.

---

### Post by Hippytaff on 2011-03-11
No worries - let us know how it goes

---

### Post by Narchie on 2011-03-14
Arrgh! plugged in what is supposed to be the simplest USB 3g modem to use on Ubuntu 10.10 (huwaei e220) and it does not even recognize it.

Anyway back to the drawing board.

---

### Post by Hippytaff on 2011-03-14
You might need to use [mode_switch ]("http://manpages.ubuntu.com/manpages/maverick/en/man1/usb_modeswitch.1.html")to use the usb.
 
What does```
lsusb
``` return?

---

### Post by Narchie on 2011-03-14
Does see it there but when I run the new mobile connection wizard 
After running that command I can now connect to the modem, Thanks. T still have not worked out how to use it for connecting to the internet though (I can connect and disconnect the e220 but not get onto the internet using it.

Apologies for all the silly questions.


> $ lsusb
Bus 007 Device 002: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 2001:f103 D-Link Corp. [hex] DUB-H7 7-port USB 2.0 hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


---

### Post by Hippytaff on 2011-03-14
The mobile connetion wizard should do all the gubbins for you if you provide the correct details. If you've already done that, try clicking on the wireless icon the thing like a radar becon, on the top panel and see if the connetion is liste. If so click it to connect to it

---

### Post by Narchie on 2011-03-14
I have connected to it but when I remove all my proxy settings (even in firefox) I still can not get onto the internet via the modem.

It connects and disconnects quite easily and I know it's connected due to the solid blue light that comes onto the modem.

---

### Post by Hippytaff on 2011-03-14
Can you ping anything when it's connected?
```

ping www.google.com
```

---

### Post by Narchie on 2011-03-14
Left it for about an hour before CTRL+C

> ~$ ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (74.125.230.115) 56(84) bytes of data.
^C
--- [www.l.google.com](www.l.google.com) ping statistics ---
2446 packets transmitted, 0 received, 100% packet loss, time 2461140ms


---

### Post by Hippytaff on 2011-03-14
Then it's not connecting. Are you sure there is coverage there? and that the correct info has been inputted into the 3G wizard effort.

---

### Post by Narchie on 2011-03-15
Hi, 

I am sure it is connecting, we also have good 3g coverage in this area (I use 3g as a backup for when the ADSL line drops).

[ATTACH]186099[/ATTACH]

---

### Post by Hippytaff on 2011-03-15
I don't understand why you can't ping then. I guess you've tried rebooting etc
 
Can you remove the usb. put it back in and post theoutput of```
demsg | tail
```
or```
dmesg | less
``` any useful info about how the kernel, dbus and udev is powering up and initialising the usb should appear at the bottom of the dmesg log.

---

### Post by Narchie on 2011-03-15
Hi,

As below

Thank you
Sean

> [13278.508518] usb 7-1: new full speed USB device using uhci_hcd and address 2
[13278.940030] Initializing USB Mass Storage driver...
[13278.941790] scsi6 : usb-storage 7-1:1.0
[13278.941890] usbcore: registered new interface driver usb-storage
[13278.941892] USB Mass Storage support registered.
[13279.080043] usb 7-1: USB disconnect, address 2
[13279.816519] usb 7-1: new full speed USB device using uhci_hcd and address 3
[13279.997888] scsi9 : usb-storage 7-1:1.2
[13281.000988] scsi 9:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[13281.024972] sr1: scsi-1 drive
[13281.025117] sr 9:0:0:0: Attached scsi CD-ROM sr1
[13281.025441] sr 9:0:0:0: Attached scsi generic sg2 type 5
(END) 


---

### Post by Hippytaff on 2011-03-15
ok...its recognising the usb as a mass storage device instead of a wireless dongle. You need to use [usb_modeswitch ]("http://manpages.ubuntu.com/manpages/maverick/en/man1/usb_modeswitch.1.html")to tell it that it's a wireless dongle.
 
forum member [Alexfish posted this tutorial ]("http://ubuntuforums.org/showthread.php?t=1331660")on how to use modeswitch. I'm in work at the moment, but I'll check back in a bit...let me know how it goes
 
[I also found this which may help]("http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=466")

---

### Post by Narchie on 2011-03-17
Hi, 

I decided to try a different approach.

1. Using a different proxy server now.
2. I removed all the sources that were giving me hassles then put them back again one at a time and after putting each one back I would do an update.

All working perfectly now and no need for the 3g modem on the system (yet).
I'll get back to that again when I have the time.

Thanks again for all the help :)

---

### Post by Hippytaff on 2011-03-17
Your welcome...sorry we couldn't resolve the second issue, but at least your able to do what you originally wanted to do. Glad you sorted it :-)

---

### Post by vini on 2011-05-01
You can get the key here

[http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xB725097B3ACC3965](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xB725097B3ACC3965)

---

