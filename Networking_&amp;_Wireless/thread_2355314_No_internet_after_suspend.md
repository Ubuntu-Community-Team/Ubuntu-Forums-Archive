---
title: "No internet after suspend"
date: 2017-03-11
forum: Networking &amp; Wireless
---

### Post by mistcloud-misty on 2017-03-11
Hello. My wireless was working mostly okay until I did an update yesterday morning. After work I came home and opened my laptop and although it said I was connected to my network, no pages loaded (host name not resolved on Chrome). I tried unplugging and replugging the wireless USB, and it reconnected to the network but still no access.. 

When I checked the connection information everything was okay. I tried disabling and re-enabling wireless. I did just about everything except restarting the network manager, mostly because I didn't remember the command. Nothing worked until I rebooted completely. This morning the same thing happened. I finally remembered to copy and paste the reboot command so if it happens again later I can see if that works.

In the meantime, I'm not exactly sure what was recently updated that would cause this. Any ideas? 

Here's my wireless info in pastebin from the command.

[http://paste.ubuntu.com/24158555/](http://paste.ubuntu.com/24158555/)

---

### Post by kwbmm on 2017-03-15
I'm having the exact same issue and don't understand what's the problem..
I solve it by typing in terminal
```
sudo systemctl restart network-manager
```
but would like to avoid doing this manually...

EDIT: I must say that I can successfully ping the router or any other computer connected to the wifi network. Only internet connectivity is missing.

---

### Post by scriber on 2017-03-16
I too am having the same problem now, only way to get it working is a reboot :(

---

### Post by kwbmm on 2017-03-16
> **scriber said:**
> I too am having the same problem now, only way to get it working is a reboot :(

Did you try?
```
sudo systemctl restart network-manager
```

---

### Post by scriber on 2017-03-16
> **kwbmm said:**
> Did you try?
```
sudo systemctl restart network-manager
```

Yes, it worked, but kind of a cludgy workaround ( for me ) as I've never had an issue until now, hopefully it will be fixed in the next OS update as that's when it broke.

Thanks for the reply though, much appreciated :cool:

---

### Post by kwbmm on 2017-03-16
Yeah I know... I'll look for a solution as this bothers me too

---

### Post by praseodym on 2017-03-17
The reason is systemd! This script works:

[https://forum.ubuntuusers.de/topic/nach-16-10-installation-kein-internet-mehr-nac/2/#post-8652643](https://forum.ubuntuusers.de/topic/nach-16-10-installation-kein-internet-mehr-nac/2/#post-8652643)

You only need to replace rtl8187 in that script with your module name

---

### Post by kwbmm on 2017-03-17
> **praseodym said:**
> The reason is systemd! This script works:

[https://forum.ubuntuusers.de/topic/nach-16-10-installation-kein-internet-mehr-nac/2/#post-8652643](https://forum.ubuntuusers.de/topic/nach-16-10-installation-kein-internet-mehr-nac/2/#post-8652643)

You only need to replace rtl8187 in that script with your module name

Bummer... Because I do not have that file in that location... :(

---

### Post by praseodym on 2017-03-17
The "sudo touch" command creates the new one. If the last one is not there, doesn't matter

---

### Post by kwbmm on 2017-03-17
> **praseodym said:**
> The "sudo touch" command creates the new one. If the last one is not there, doesn't matter

Oh yes, thank you! To see what should be substituted I ran

```
lsmod
```

And looked for cfg80211 entry.

Is that correct?

I created the script and updated it accordingly. Will test if it works.

---

### Post by scriber on 2017-03-18
All the above is Greek to me, haven't a clue what praseodym posted means, am still having to use the restart manager thing for now :twisted:

Hope this gets fixed soon.

---

### Post by kwbmm on 2017-03-18
> **scriber said:**
> All the above is Greek to me, haven't a clue what praseodym posted means, am still having to use the restart manager thing for now :twisted:  Hope this gets fixed soon.  I don't know if I used the script in the wrong way, but it's not working... So if you don't understand what's written there don't bother..

---

### Post by scriber on 2017-03-18
> **kwbmm said:**
> I don't know if I used the script in the wrong way, but it's not working... So if you don't understand what's written there don't bother..

I won't :)

---

### Post by praseodym on 2017-03-19
Ok, please run

```
sudo touch /lib/systemd/system-sleep/wakeon_suspend.sh
```
Now open this new file as root:

```
gksudo gedit /lib/systemd/system-sleep/wakeon_suspend.sh
```
Add this
```

#!/bin/sh
 case $1/$2 in
  pre/*)
    echo "aktivate $2..."
     /bin/systemctl stop network-manager.service
      /sbin/modprobe -rf ath9k_htc
    ;;
  post/*)
    echo "wakeup from $2..."
     /sbin/modprobe ath9k_htc
      /bin/systemctl start network-manager.service
    ;;
esac

```
Save, close the editor and set the exec flag:
```
sudo chmod a+x /lib/systemd/system-sleep/wakeon_suspend.sh
```
Now test suspend

---

### Post by kwbmm on 2017-03-20
Not working for me:

```

#!/usr/bin/env sh

MODULE_NAME="brcmfmac"

case $1 / $2 in
    pre/* )
        echo "Activate  $2 ..."
        /bin/systemctl stop network-manager.service
        /sbin/modprobe -rf $MODULE_NAME
    ;;
    post/* )
        echo "Wakeup from  $2 ..."
        /sbin/modprobe $MODULE_NAME
        /bin/systemctl start network-manager.service
    ;;

```

---

### Post by kwbmm on 2017-03-21
I may have solved the issue, at least for me.
Open up /etc/NetworkManager/NetworkManager.conf
```

sudo nano /etc/NetworkManager/NetworkManager.conf 

```

Change this line
```

dns=dnsmasq

```

To this:

```

#dns=dnsmasq

```

---

### Post by scriber on 2017-03-22
At first it didn't appear to work, but decided to do a reboot and it seems to be  working now.

Thanks for that kwbmm, much appreciated.

So what does that line change do ?

---

### Post by vasa1 on 2017-03-28
> **scriber said:**
> ...
So what does that line change do ?
Very often, a # at the start of a line or even internally comments out the remaining content of that particular line, if that's what you're asking.

---

### Post by scriber on 2017-03-28
Thanks for that vasa1 , that was what I was asking about :cool:

I haven't been in Ubuntu for days now, kinda annoying as I only have a wireless connection, I live in the country and the only connection is via a wireless tower 4km away.

Works fine in Windoze though....

---

