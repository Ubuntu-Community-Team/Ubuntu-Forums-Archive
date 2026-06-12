---
title: "Huwai e220 Ubuntu 9.10"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by benmie on 2009-12-14
I recently installed Ubuntu 9.10 and like it very much. 
Found a lot of help on the internet for al kinds og things, but I am having trouble finding a step-by-step guide on HOWTO get the huwai e220 to work on ubuntu 9.10.

Found a lot of solutions, but none of them are working on 9.10.

I am able to work in terminal, but don't know how to get this to work.. 
Hope someone here can help me ;):D

---

### Post by hellomoto on 2009-12-14
I have the same modem running on 9.10. Can u tell me what you have tried/what the problem is? Also what network is it on? Have you tried using network manager to connect, it can be all done through there now, under the mobile broadband tab. :)

---

### Post by benmie on 2009-12-14
I have tried the network manager - disconnected from the wireless and tried connecting - don't get connected.

Then I tried something with usbmodeswitch - not exactly sure what it is - 

I just tried everything they suggested in different threads.

I tried unmount one of the drives, when I insert the usb modem 2 devices are detected, and someone suggested to unmount.

I live in Denmark and use a phonecompany called 3.

---

### Post by benmie on 2009-12-14
I also tried something with wvdial - but appearently I am doing something wrong or missing something :)

Hope you can help me.... what did you do to get it to work? Everywhere I read it says works with Ubuntu 9.04... maybe I should install that version instead?

---

### Post by GeorgeVita on 2009-12-14
Hi **benmie**, please open a terminal window and try: ```
uname -a
``` Recent kernel is 2.6.31-16 or -17  (initial kernel from LiveCD has [bug#446146]("https://bugs.launchpad.net/bugs/446146")).

Also check settings (ask your provider): right click network manager icon, edit connections, mobile broadband, click on provider, edit

Note: 3-dk has 3 options (bredband, premium and mobil abonnement)
>>> choose appropriate as the wrong may cost you more!

Regards,
George

---

### Post by fatality_uk on 2009-12-14
Have you tried the mobile broadband option?

Good guide here
[https://help.ubuntu.com/9.10/internet/C/connecting-mobile.html](https://help.ubuntu.com/9.10/internet/C/connecting-mobile.html)

---

### Post by benmie on 2009-12-14
GeorgeVita
2.6.31-16-generic - so that should be ok.

I tried all settings in network manager - none of them works, after entering pin it says disconnected.

fatality_uk
I will take a look a the guide

---

### Post by GeorgeVita on 2009-12-14
E220 must work with NO tricks using network manager! Just some ideas to test:

- Remove SIM PIN check (insert SIM to a mobile phone and disable it).
- Delete any existing mobile broadband connection (right click network manager icon, edit connections, mobile broadband, click on provider name, delete)
- attach modem and after 20 seconds click on network manager icon
>>> you must have a 'new broadband connection ...' line
>>> if not try to configure it manually 

Some other users say that it need a firmware update ??? (harder way)
[http://ubuntuforums.org/showthread.php?t=1315463](http://ubuntuforums.org/showthread.php?t=1315463)

And from [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)
> Bruno Cunha  wrote on 2009-12-13:  	  #370

I found this temp fix
Run the following command at the console, prior to plugging in the modem to the USB slot;

watch -n1 sudo rmmod usb-storage

This would remove the usb_storage module, and would make the device not detected as a USB storage device. From here I can connect to the internet using the Network Manager's Mobile Broadband as I normally would.

p/s: Do take note that this would make the system to not be able to detect any USB storage devices such as your thumb drives, till the rmmod command is killed.
It's working fine with me until a definitive fix is found


Regards,
George

---

### Post by benmie on 2009-12-14
It works after a firmware upgrade of the huawei :-D
Now I get connected, but when I open firefox it says I have no connection.

In firefox preferences I have checmarked System Proxy and Direct connection in system | preferences | proxy

Also I do not have internet in my virtualbox (running XP)

But I can ssh to my other computer on my network.... 

I don't know if I should close this thread and create a new one for my 2 new issues?
Also new in this forum :D

Thanks for all your inputs.

---

### Post by benmie on 2009-12-15
Now everything works :D

First I tried different browsers
Then I tried to set network.dns.disableIPv6 to false in firefox config

Nothing worked...

then I tried route add default ppp0 and now I can browse on the internet in all my 4 browsers ;) (which I will uninstall again) and I have internet on XP in virtual box

Hope this can help others....

---

### Post by uidb4056 on 2010-01-04
I have the same USB modem that worked flawlessly with previous releases but didn't work with Karmic x64 on my Lenovo W500 (kernel 2.6.31.16-generic). Found in Launchpad that this can be solved updating the firmware of modem this link will show you the way and includes a link on Launchpad with explanations ( [http://azizan.aiskosong.net/?p=458](http://azizan.aiskosong.net/?p=458) ).

I've switched to XP where the modem runs without problems, downloaded the firmware and applied it (only the firmware not the dashboard because Launchpad says is not necessary), after the update of firmware in XP I've checked if still runs on it and Yes! it still works and get as a side benefit that the connection now is at 7.2 GB instead of previous 3.6 GB.

Going back to Karmic again now at connection of the USB the internal disk is showed in desktop but , when starts the modem it was started OK but I was not able to navigate ...

Searching for a solution (apparently the problem was no DNS) I edited the wideband connection starting from terminal 'sudo nm-connection-editor' and in the Tab 'Adjusting IPV4' fill the field DNS Servers with the DNS used by XP and then this was solved.

I hope this can help

---

