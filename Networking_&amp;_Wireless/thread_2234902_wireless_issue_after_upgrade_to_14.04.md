---
title: "wireless issue after upgrade to 14.04"
date: 2014-07-17
forum: Networking &amp; Wireless
---

### Post by jsabina1 on 2014-07-17
Hi everybody,
I upgraded few days ago to 14.04.
Since then I have problems with the wireless connection.
When I login it cannot see any network and the icon of the wifi has a question mark ?
If from terminal I run ifdown wlan 0 and ifup wlan0 I have the prompt of password from the wallet and everything works again.
I think for some reason it needs to authenticate in kwallet before allowing me to connect?
How can I solve?
(Kde)
thanks

---

### Post by Hadaka on 2014-07-17
Hi, take a read here and see if it helps..
[http://askubuntu.com/questions/451593/lubuntu-nm-applet-wifi-icon-missing](http://askubuntu.com/questions/451593/lubuntu-nm-applet-wifi-icon-missing)
are you running Lubuntu?

---

### Post by jsabina1 on 2014-07-18
Thanks a lot, I will read.
My icon is not missing though.
No it's not Lubuntu now, just installed Ubuntu and KDE, then after few months upgraded to 14.04.
thanks

---

### Post by grahammechanical on 2014-07-18
Is the connection set to automatically connect? The upgrade may have changed the settings.

Regards

---

### Post by jsabina1 on 2014-07-18
Yes,
it is set to automatically connect and I selected also that all users are allowed to use the connection.
I noticed that when I do sudo ifdown wlan0 and then sudo ifup wlan0 I have a popup for authentication from KDE daemon needs to authenticate on KDE wallet.
after I type the password the connection is enabled..
so some permission issue... but where to look?

---

### Post by varunendra on 2014-07-21
> **jsabina1 said:**
> so some permission issue... but where to look?

First place to look would be the groups you are a member of. That is, the output of -
```
id
```

For a detailed report about your wireless setup, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by jsabina1 on 2014-07-21
thanks varun,
after reading around that the networkmanager was not very good I unistalled it and installed wicd and now everything works fine

---

### Post by varunendra on 2014-07-21
Hope it remains a permanent solution, because unless NM succumbed to some bug, it is as good (even better in versatility) as wicd or any other network manager if configured properly (which for the most part is automatic). :)

For now, if you think the problem is solved and is stable, please mark the thread as [SOLVED]. Thanks!

---

### Post by jsabina1 on 2014-07-21
oh ok, I don't know why but in many threads or articles I read a lot of negative comments about it.
Installed wicd everything works fine, so at the moment I would say it's solved.
thanks!

---

