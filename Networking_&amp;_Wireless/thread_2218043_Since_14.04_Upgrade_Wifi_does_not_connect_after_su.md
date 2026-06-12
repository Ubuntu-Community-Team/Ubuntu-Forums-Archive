---
title: "Since 14.04 Upgrade Wifi does not connect after suspend, ralink RT3290"
date: 2014-04-19
forum: Networking &amp; Wireless
---

### Post by arehragout on 2014-04-19
Hi I have a Ralink RT3290 wireless card,
in 13.10 everything worked well, now in 14.04 after a Suspend/Hibernate action the Wifi tries over and over to connect but fails.

SUSPEND_MODULES="rt2800pci" in etc/pm/config.d/config

doesn't help.

BTW bluetooth doesn't work either! 

Any suggestions?

Thanks!!

---

### Post by praseodym on 2014-04-19
Tried this driver?

[http://forum.ubuntuusers.de/topic/nach-update-kein-wlan-mehr-433/2/#post-5641297](http://forum.ubuntuusers.de/topic/nach-update-kein-wlan-mehr-433/2/#post-5641297)

If it works change the settings in your etc/pm/config.d/config. BTW: Is the file set to executable?

```
sudo chmod +x /etc/pm/config.d/config
```

---

### Post by mih-com on 2014-04-20
same story with ath9k dell inspiron
work again only after shutdown 
reboot not help

---

### Post by praseodym on 2014-04-20
So add the following lines via
```

gksudo gedit /etc/rc.local
```
before "exit 0":
```

modprobe -r ath9k
sleep 5
modprobe ath9k
```
Reboot.

---

### Post by arehragout on 2014-04-20
tried the last idea with my rt2800pci driver, interestingly this showed the same behaviour, which i previously had only after suspend, now already after boot - so no wireless at all.

yes, my config file is executable.

i'll try the driver from first reply, is there any danger in doing so?

thanks for your quick response!

---

### Post by praseodym on 2014-04-20
No, if its compiling (at all) and not working you can easily uninstall it via
```

sudo dkms remove -m Ralink_3290sta -v 2.6.0.0 --all
sudo rm -r /usr/src/Ralink_3290sta-2.6.0.0
sudo rm /etc/modprobe.d/blacklist-rt2800pci.conf  
```

---

### Post by mih-com on 2014-04-21
> **praseodym said:**
> So add the following lines via
```

gksudo gedit /etc/rc.local
```
before "exit 0":
```

modprobe -r ath9k
sleep 5
modprobe ath9k
```
Reboot.

this not helped
sometimes shutdown not helped too
work again after long switch off

---

### Post by shrodi on 2014-04-23
Had the same problem. In my case, the problem was double:

[LIST=1]
[*]the network would not come up at all after suspend; 
[*]after a "sudo restart network-manager", the network would come up again, but the wifi wouldn't connect to my network. 
[/LIST]
 I found a permanent and complete solution based both on [this]("http://askubuntu.com/questions/368671/ubuntu-13-10-wifi-not-re-connecting-after-suspend") and [that]("http://ubuntuforums.org/showthread.php?t=2217542"), which is:
```
sudo touch /etc/pm/sleep.d/wakenet.sh

sudo chmod +x /etc/pm/sleep.d/wakenet.sh

sudo gedit /etc/pm/sleep.d/wakenet.sh
```

Insert the following lines:
  ```
#!/bin/bash
case "$1" in
thaw|resume)
nmcli nm sleep false
pkill -f wpa_supplicant
;;
*)
;;
esac
exit $?
```
And then save.

Hope that helps.

---

### Post by arehragout on 2014-04-26
Thanks shrodi, that worked! :-)

---

### Post by shammydog on 2014-08-28
works!  thank you shrodi!

---

### Post by ashish-coolguy on 2014-08-30
> **shrodi said:**
> I found a permanent and complete solution based both on [this]("http://askubuntu.com/questions/368671/ubuntu-13-10-wifi-not-re-connecting-after-suspend") and [that]("http://ubuntuforums.org/showthread.php?t=2217542"), which is:
Insert the following lines:
  ```
#!/bin/bash
case "$1" in
thaw|resume)
nmcli nm sleep false
pkill -f wpa_supplicant
;;
*)
;;
esac
exit $?
```
And then save.
Hope that helps.

Hey i created a script in **/etc/pm/sleep.d** with this code and made it executable. still it doesnt work for me :|

I am using a Belkin F7D1101v1 wifi adapter with my PC running Ubuntu 14.04 with all latest updates. My pc doesnt connect to WiFi after resuming from suspend and I either have to unplug and replug my wifi adapter or restart ubuntu. Any other fix?

PS - even doing **sudo restart network-manager** from terminal after resuming from suspend doesnt work.

---

### Post by olamina on 2014-09-18
You are a lifesaver, shrodi! I'd tried so many other things and this is the only thing that worked!

---

### Post by BROBA on 2014-09-25
Can someone explain to me how he did this? I'm pretty obsessed...I'd really love to learn how to do this...

---

### Post by mclode on 2014-10-03
Perfect.
My Lenovo Thinkpad T420 now resumes it Wireless connection.
Thank you.

---

### Post by jcisio on 2015-01-05
Thanks [shrodi]("http://ubuntuforums.org/member.php?u=1066413") , it works for me.

---

### Post by telmoamaral on 2015-02-14
Many thanks,shrodi! Like you, I needed both commands too solve the problem (nmcli and pkill), on a Samsung NP530U3B laptop with 14.04.

---

### Post by paul-c-budden on 2015-03-29
Just found this thread.  I had a method that seemed to work most of the time that involved turning counter-clockwise three times, disable wifi, manually suspend, recite a sendmail.cf config, sprinkle 5cc of mouse blood over the keyboard and power back up.
Thank you Shrodi, your fix makes it much faster  :)

---

### Post by bigley-ling on 2015-05-08
thumbs up Shrodi

I just added this line

"nmcli nm sleep false"

into one of my existing sleep.d scripts and it has solved my issue. This fix works well on my Sony UX which I just updated from 12.04 to 14.04.

---

### Post by fl1 on 2015-05-19
Had the same wi fi problem with an HP envy dv6  , ralink rt3290 the connection often fall ; with SHRODI solution all seems to work but sometimes the connection continues to broke down  .

---

### Post by Franck971 on 2015-07-18
Hi,
It helps with Acer Aspire E15 / Ubuntu 15.04
Thanks

---

### Post by williambertram on 2015-10-29
That also seems to have fixed it for me.  Wireless connected after several resumes anyway.  Thanks Shrodi!

---

### Post by jrda on 2015-11-09
Same Problem, same Workaround from Shrodi. Thanks.

---

### Post by bo-nielsen-p on 2016-02-08
Thanks for this work-around....works on DELL E6410

---

### Post by Cyril_DUCROCQ on 2016-05-05
Thanks _too_ shrodi, that worked! :smile:

---

### Post by Kixtosh on 2016-05-07
Yup! Shrodi conquers again!

):P


[LIST]
[*]**Toshiba Portégé R500** (R500-S5004) 
[*]Intel PRO/Wireless 4965 AGN 
[*]Kernel driver in use: **iwl4965** 
[*]Distribution: **Linux Mint 17.3** Rosa 
[/LIST]

---

