---
title: "Wireless stopped after update"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by jbraum on 2008-06-12
My wireless stopped working after an update.  Has anyone had this happen to them, and what did you do to fix it.  

Acer Aspire 5315-2164 with a Atheros wireless card

---

### Post by guildofghostwriters on 2008-06-12
Pretty much whenever there's a kernel update, the serialmonkey drivers for my rt73 chipset wireless usb dongle are no longer listed under hardwire drivers and I have to reinstall them from scratch. Because I'm so used to it now, I've saved the guide I used - [http://ubuntuforums.org/showthread.php?t=709260&highlight=rt73+eldragon&page=2](http://ubuntuforums.org/showthread.php?t=709260&highlight=rt73+eldragon&page=2) - as a text file on my desktop and I download the latest version of the driver before restarting whenever I'm prompted to restart after an update. Then after I restart I just follow the guide and my wireless drivers are working again.

Did your wireless work without you having to do anything when you first installed ubuntu or did you have to install drivers? If you had to do something to get the wireless working, just do that again. Otherwise, I don't know.

---

### Post by rsw1965 on 2008-06-12
I have the acer 4315 with the atheros 5007EG card running under a patched madwifi driver and it is simply a matter of recompiling  the driver and using the modprobe command to reinsert the revised module.

This has been the most useful link for me:

[http://ubuntuforums.org/showthread.php?t=792158](http://ubuntuforums.org/showthread.php?t=792158)

I think you probably have the same card in the acer 5315.

Robert

---

### Post by jbraum on 2008-06-13
That did seem to work.  When I iwconfig I get no wireless extensions.

---

### Post by jbraum on 2008-06-13
Got it...

[http://ubuntuforums.org/showthread.php?p=4999962](http://ubuntuforums.org/showthread.php?p=4999962)

---

### Post by tim183 on 2008-06-13
trying to get the wifi going on a new hp dv6000 with this atheros chip.

i had it working using the same method a few days ago, however after a re-install of ubuntu 8.04 i get the following output:


 wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
--16:30:34--  [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
           => `madwifi-ng-r2756+ar5007.tar.gz'
Resolving snapshots.madwifi.org... failed: Name or service not known.

has the file moved?

---

### Post by malath on 2008-06-13
hi
my wireless internet connection was just working fine untill i installed the virtualbox-ose-module
after i finished the installation i found a request to reboot the system. as soon as the system rebooted the wireless connection was lost and i am unable to connect to it again.

I even dont have audio working

---

### Post by tim183 on 2008-06-13
bump

---

### Post by 2on2on on 2008-09-28
Hello, I want you please to read this article it may help you:
[http://ronymattar.com/blog/?p=10]("http://ronymattar.com/blog/?p=10")

---

