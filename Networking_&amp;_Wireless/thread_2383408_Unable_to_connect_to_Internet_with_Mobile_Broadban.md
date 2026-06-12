---
title: "Unable to connect to Internet with Mobile Broadband"
date: 2018-01-24
forum: Networking &amp; Wireless
---

### Post by paulromano-8 on 2018-01-24
I do not have access to a fixed line broadband connection, so I rely on a 3G cellular connection using a USB modem. Under Ubuntu 17.10 (also Kubuntu & Ubuntu-Mate) I can not get a working Internet connection. The modem works fine OOTB under 16.04 and Debian 9 Stretch on the same box, and also under Mint 18.2 & Windows on another system, so it is not a hardware issue.

When I insert the modem, dmesg shows it being identified as:-
Product: Vodafone Mobile Broadband K3570-Z
Manufacturer: Vodafone (ZTE)
CD-ROM Vodafone  USB SCSI CD-ROM  USB PQ: 0 ANSI: 2
idVendor=19d2, idProduct=1007/1008

I can create and save a new Mobile Broadband connection with the modem showing as a QUALCOMM INCORPORATED 33. However, when I try to connect I get a message "Connecting" (Kubuntu - "Preparing to connect") but no connection is ever made and after about 2 minutes it times out without any error message. The cellular signal strength is good, and I have tried the modem in all 8 USB ports (both USB 2.0 & 3.0). My ISP (Vodacom) does not have any password requirements. The modem works in the older distros with default settings.

Under Windows, this type of modem acts first as a CD device to load the necessary software, then switches mode to a modem device, so I thought it might be a problem with usb_modeswitch. However, this modem is listed in the file /lib/udev/rules.d/40-usb_modeswitch.rules.

Something has changed between 16.04 & 17.10. Does anyone know what the cause may be and how to fix it?
Thanks

---

### Post by Hadaka on 2018-01-24
Hi, To begin..I have very limited broadband connection knowledge.
Have you checked the current modeswitch version ?
[http://manpages.ubuntu.com/manpages/zesty/man1/usb_modeswitch.1.html](http://manpages.ubuntu.com/manpages/zesty/man1/usb_modeswitch.1.html)
Looks like current version is..2.5.1+repack0-1ubuntu1
[https://launchpad.net/ubuntu/artful/+source/usb-modeswitch](https://launchpad.net/ubuntu/artful/+source/usb-modeswitch)
and you might also try..for a known usb ubuntu 17.04 - 17.10 bug..
```
printf "[device]\nwifi.scan-rand-mac-address=0\n"| sudo tee -a /etc/NetworkManager/*.conf
```
Hope that helps.

"17.04-17.10 USB bug ref."
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1681513](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1681513)

---

### Post by paulromano-8 on 2018-01-25
@Hadaka
usb_modeswitch --version reports Version 2.5.1.

I don't know how to confirm the full package name. Normally I would use Synaptic but this is a fresh install of Ubuntu 17.10 that has never been connected to the Internet so this is not installed. There are no files in /var/cache/apt and apt-cache showpkg usb_modeswitch doesn't work either.

I tried your bug code without success. It did append 2 lines to NetworkManager.conf OK. I commented out the 2 previous lines (ending in address=no) but that didn't work either, even after a reboot. Do you have a bug reference for this code? I did a quick search on Launchpad & on bugzilla.gnome.org but couldn't find anything relevant.

---

### Post by Hadaka on 2018-01-25
Hi,between my limited knowledge and Ubuntu 17.10 scarce documentation, Im not much help. 
This same link [https://askubuntu.com/questions/9707...bile-broadband]("https://askubuntu.com/questions/970785/ubuntu-17-10-problem-with-mobile-broadband")
also had a suggestion to downgrade to
modemmanager to version 1.4.12-1ubuntu1 and it worked on 17.10

how to remove the existing..modemmanager..modeswitch
[http://installion.co.uk/ubuntu/xenia...all/index.html]("http://installion.co.uk/ubuntu/xenial/main/m/modemmanager/uninstall/index.html")
          ```
sudo apt-get remove modemmanager
sudo apt-get remove --auto-remove modemmanager
``` 
Then install..version 1.4.12-1ubuntu1
[https://www.howtoinstall.co/en/ubunt...l/modemmanager]("https://www.howtoinstall.co/en/ubuntu/xenial/modemmanager")
Hope this helps.

---

### Post by paulromano-8 on 2018-01-25
Thanks to separate links provided by Hadaka, this issue has been resolved. The root cause appears to be with modemmanager. The existing version 1.6.x was removed and a downgraded version 1.4.12-1ubuntu1 installed in its place.
```

sudo apt remove modemmanager
sudo apt autoremove modemmanager

```
Then install moemmanager-1.4.12-1ubuntu1 as used by Ubuntu 16.04.

---

### Post by Hadaka on 2018-01-25
Fantastic ! glad you were able to resolve !
Thank You for marking your thread solved.

---

