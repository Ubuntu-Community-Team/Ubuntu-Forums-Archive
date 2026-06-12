---
title: "Upgraded to 8.04, now wireless doesn't reconnect after suspend"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by scottws on 2008-05-02
I've been using Kubuntu 7.10 Gutsy Gibbon on my Dell D600 series laptop for several months now with great success.

Initially I was having trouble managing my wireless... it just didn't seem like the wireless support was as robust out of the box with Kubuntu than it is with say Windows.  I was able to set wireless networks manually via the /etc/network/interfaces file, but that was a pain to do and nothing like the relatively painless experience of Windows Wireless Zero Configuration.

Then I found the program wifi-radar, which much improves the Linux wireless experience, IMO.  Very similar to what you get on Windows with WZC.  In any case, it was exactly what I was looking for and worked perfectly.  Then I upgraded to Kubuntu 8.04 Hardy Heron.

Now, whenever I suspend my laptop, wireless is broken upon resume.  I can reconnect if I just open the wifi-radar GUI and then press Connect, but it used to handle this automatically.

I checked /etc/acpi/resume.d/ and there is an entry "63-wifi-radar.sh."  The contents are as follows:

```
#!/bin/sh

if [ -x /etc/init.d/wifi-radar ]; then
        /etc/init.d/wifi-radar start
fi

```

I've also tried:

```

#!/bin/sh

if [ -x /etc/init.d/wifi-radar ]; then
        /etc/init.d/wifi-radar restart
fi
```

and
 
```

#!/bin/sh

if [ -x /etc/init.d/wifi-radar]; then
        /etc/init.d/wifi-radar restart
        ifconfig eth1 up
        /usr/sbin/wifi-radar -d
fi

```

...but none of these seem to work.  The file /etc/init.d/wifi-radar does exist and it seems to work properly when I run that script manually.

Help!

---

### Post by Paris Heng on 2008-05-03
> **scottws said:**
> I've been using Kubuntu 7.10 Gutsy Gibbon on my Dell D600 series laptop for several months now with great success.

Initially I was having trouble managing my wireless... it just didn't seem like the wireless support was as robust out of the box with Kubuntu than it is with say Windows.  KNetworkManagerI was able to set wireless networks manually via the /etc/network/interfaces file, but that was a pain to do and nothing like the relatively painless experience of Windows Wireless Zero Configuration.

Then I found the program wifi-radar, which much improves the Linux wireless experience, IMO.  Very similar to what you get on Windows with WZC.  In any case, it was exactly what I was looking for and worked perfectly.  Then I upgraded to Kubuntu 8.04 Hardy Heron.

Now, whenever I suspend my laptop, wireless is broken upon resume.  I can reconnect if I just open the wifi-radar GUI and then press Connect, but it used to handle this automatically.

I checked /etc/acpi/resume.d/ and there is an entry "63-wifi-radar.sh."  The contents are as follows:

```
#!/bin/sh

if [ -x /etc/init.d/wifi-radar ]; then
        /etc/init.d/wifi-radar start
fi

```

I've also tried:

```

#!/bin/sh

if [ -x /etc/init.d/wifi-radar ]; then
        /etc/init.d/wifi-radar restart
fi
```

and
 
```

#!/bin/sh

if [ -x /etc/init.d/wifi-radar]; then
        /etc/init.d/wifi-radar restart
        ifconfig eth1 up
        /usr/sbin/wifi-radar -d
fi

```

...but none of these seem to work.  The file /etc/init.d/wifi-radar does exist and it seems to work properly when I run that script manually.

Help!

It seems everything is fine...hmmmm, need some expert to help u.

---

### Post by svetlin on 2008-05-04
It happens to me also, with a regular lan connection. Maybe this [howto]("http://ubuntuforums.org/showthread.php?t=571188") will help tou.

---

### Post by scottws on 2008-05-04
Thanks, but that's exactly what I do not want.  I don't want to configure the connection manually. I travel and use the laptop all over.

---

### Post by scottws on 2008-05-07
Any other insight into this issue?  It's still a problem.  It's basically as if the script(s?) in /etc/acpi/resume.d aren't called when the machine comes back from a standby.  I say this because when I return from a standby, I can type in "sudo /etc/acpi/resume.d/63-wifi-radar.sh" and it will connect me to one of the wireless networks in my profile for wifi-radar.  It's basically as if the script just isn't being run when it comes back.

This wouldn't be a huge deal for me except that my girlfriend uses this laptop too, and she's used to Windows, where at least the wireless side of things generally just works.  I thought to myself... well, I'll just give her access to admin wifi-radar by putting her in a user group called wireless and putting "%wireless ALL=(ALL) NOPASSWD: /usr/sbin/wifi-radar" in /etc/sudoers but this doesn't work either because kdesu/kdesudo don't seem to respect the NOPASSWD: setting in sudoers.  It always prompts for a password.

This is really a major headache.  I did notice that after the upgrade to 8.04 that the new KNetworkManager is a lot nicer... it actually supports shared key authentication now.  However, while it can see wireless networks, I've had zero success in actually connecting to the encrypted ones (such as my own).  I was hopeful in using that instead of KNetworkManager instead of wifi-radar, but I guess not.

---

### Post by scottws on 2008-05-07
I think I solved the problem.  I looked at KNetworkManager again, and where I was typing the WEP key in said "WEP Passphrase."  I changed this to "WEP 40/104-bit hex," and it worked.  It seems to save the connection information in the kwallet, which I like.

I verified that it can connect on boot and on resume... just have to type in the kwallet password.

The only downside is that it's per user where wifi-radar was system-wide.

---

