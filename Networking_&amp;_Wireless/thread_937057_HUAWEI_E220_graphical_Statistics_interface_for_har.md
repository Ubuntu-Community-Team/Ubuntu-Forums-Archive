---
title: "HUAWEI E220 graphical Statistics interface for hardy"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by hayesha on 2008-10-03
Hi all,

I recently bought the HUAWEI E220 hsdpa modem and managed to successfully configured it to run on hardy thanks to the post on this link : [https://help.ubuntu.com/community/DialupModemHowto/Huawei/E220](https://help.ubuntu.com/community/DialupModemHowto/Huawei/E220), and now I was wondering whether I could find any graphical Statistics tool to monitor my internet usage on hardy. I downloaded the source file "he220stat.tar.bz2" provided at [http://oozie.fm.interia.pl/pro/huawei-e220/](http://oozie.fm.interia.pl/pro/huawei-e220/) but the compilation fails due to not availability of some header files. So does any one successfully configured it to work or is there any working tool out there.

Has any one installed the software provided at [https://forge.betavine.net/frs/?group_id=12&release_id=116](https://forge.betavine.net/frs/?group_id=12&release_id=116) to get the thing done and does anyone succeed in installing the [https://forge.betavine.net/frs/download.php/119/vodafone-mobile-connect-card-driver-for-linux_2.0.beta1_i386.deb](https://forge.betavine.net/frs/download.php/119/vodafone-mobile-connect-card-driver-for-linux_2.0.beta1_i386.deb) to hardy. 

Thanks in advance.

Hayesha.

---

### Post by fuzzyk.k on 2009-01-30
OK I downloaded the source and compiled and installed it successfully , you need to install libncurses-devel package which contains ncurses.h

---

### Post by studioguide on 2009-02-01
> **hayesha said:**
> Hi all,

I recently bought the HUAWEI E220 hsdpa modem and managed to successfully configured it to run on hardy thanks to the post on this link : [https://help.ubuntu.com/community/DialupModemHowto/Huawei/E220](https://help.ubuntu.com/community/DialupModemHowto/Huawei/E220), and now I was wondering whether I could find any graphical Statistics tool to monitor my internet usage on hardy. I downloaded the source file "he220stat.tar.bz2" provided at [http://oozie.fm.interia.pl/pro/huawei-e220/](http://oozie.fm.interia.pl/pro/huawei-e220/) but the compilation fails due to not availability of some header files. So does any one successfully configured it to work or is there any working tool out there.

Has any one installed the software provided at [https://forge.betavine.net/frs/?group_id=12&release_id=116](https://forge.betavine.net/frs/?group_id=12&release_id=116) to get the thing done and does anyone succeed in installing the [https://forge.betavine.net/frs/download.php/119/vodafone-mobile-connect-card-driver-for-linux_2.0.beta1_i386.deb](https://forge.betavine.net/frs/download.php/119/vodafone-mobile-connect-card-driver-for-linux_2.0.beta1_i386.deb) to hardy. 

Thanks in advance.

Hayesha.
It took me 3-4 days to manage this.
I am a novice enthusiast and installed Ubuntu Studio 8.10 on my Acer Aspire laptop.
I downloaded the following: [https://forge.betavine.net/frs/download.php/119/vodafone-mobile-connect-card-driver-for-linux_2.0.beta1_i386.deb](https://forge.betavine.net/frs/download.php/119/vodafone-mobile-connect-card-driver-for-linux_2.0.beta1_i386.deb)
Before installing this software, I had to connect to the Internet to update the system and install the dependencies. Yes, I tried doing this with a pen-drive but had a problem with the libxcb-render-util0 package, which the python-gnome2-extras depends on. If you try this from a pen-drive you will probably find that it won't install.
To connect the Internet, I used a "always-on" broadband connection on a local network. After much searching online I discovered the command "sudo dhclient eth0", which then makes a connection, I had to do this because Ubuntu Studio doesn't have a network manager. When connected I performed a "sudo apt-get update" and installed the network manager.
After a reboot, the system connects automatically when plugged in.
Having a working connection, I then go the "System &#8594; Administration &#8594; Synaptic Package Manager". You will need administrative access to use it. When here, install usb utils that appear relevant and install the python-gnome2-extras. After this, it should be possible to install the software referenced at beginning. Then, a reboot should make it possible to use vodafone-connect without problems...
If in doubt, please post and I will try to find a solution.

---

