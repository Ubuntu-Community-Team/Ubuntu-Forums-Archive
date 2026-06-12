---
title: "Intel 3945 wireless not working on Dell Latitude D520 after resume: Edgy 6.10"
date: 2007-01-05
forum: Networking &amp; Wireless
---

### Post by cbourner on 2007-01-05
I have got Ubuntu Edgy 6.10 running on my Dell Latitude D520, including wireless (Intel 3945) using WPA security, which starts from boot correctly.

But ...

If I suspend to RAM, and then resume, the wireless is no longer working, and ifdown/ifup doesn't fix it - I have to reboot.

Does anyone have any suggestions as to how I might fix this?  It has occurred to me that if, on suspend, the system performed an orderly ifdown, and then an ifup on resume, it might work.

Any help anyone can offer would be appreciated.

---

### Post by meldroc on 2007-01-08
I've seen the same problem on my laptop - mine's an Asus A8Js, and the wireless is also an Intel 3945.  When I do a suspend, sometimes when I resume, the wireless stops working.

I note that if I do an iwconfig, when things are working correctly, it'll show wireless-related information for eth1, but after a suspend and resume, when this bug hits, it shows eth1 with "no wireless extensions".

---

### Post by cbourner on 2007-01-08
I think I have fixed it.

By renaming the S*-ifup.sh file in /etc/acpi/resume.d to  S89-ifup.sh (I can't remember what number it was to start with) and also the S*-down-interfaces.sh file to S11-down-interfaces.sh in /etc/acpi/suspend.d hibernate is now working properly.

I have the occasional problem with suspend to RAM, but that is not networking related.

Let me know if this works for you!

---

### Post by meldroc on 2007-01-10
I just made a discovery on my Asus A8Js

Sometimes, on suspend or hibernate, then resume, my wireless doesn't come back - it stops responding.  As I mentioned, when this happens, if I do an iwconfig, normally, it would show all sorts of wireless information for eth1, but when this glitch happens, iwconfig shows "no wireless extensions" for eth1.

I just found that if I do "sudo modprobe -r ipw3945" followed by "sudo modprobe ipw3945" (which unloads and reloads the 3945 wireless kernel driver), it brings my wireless back to life.

Cool.  Now I would like to figure out how to make this automagically happen, that way suspend and resume Just Work.  I imagine that involves tinkering with the scripts in /etc/acpi/resume.d...

---

### Post by meldroc on 2007-01-11
OK, does anybody know why my wireless card goes catatonic after resuming from hibernate or suspend, forcing me to reload the driver?  This is a pain.

---

### Post by ddinsdale on 2007-01-12
Debian has a new release of the deamon for this device.  I pieced this together from other threads on the subject and it works--even from hibernation.

goto 
[http://http.us.debian.org/debian/poo....1.2-6_all.deb](http://http.us.debian.org/debian/poo....1.2-6_all.deb)  
[http://http.us.debian.org/debian/pool/contrib/i/ipw3945/](http://http.us.debian.org/debian/pool/contrib/i/ipw3945/)

look for the latest source: ipw3945-source_<version>_all.deb

download to desktop or just run it from there with the package installer.

sudo dpkg -i ipw3945-source_<version>_all.deb  

Then I did this:
sudo apt-get update && sudo apt-get install network-manager

---

### Post by meldroc on 2007-01-14
I've found a hack that works for me - minimal tinkering with the config files, and ensures that the wireless card doesn't go catatonic - I've suspended and resumed multiple times, and it's come back every time.

Edit /etc/default/acpi-support, find the MODULES= line, and change it so it reads 

```
MODULES="ipw3945"
```

By doing this, the acpi code will automagically unload the module on a suspend, and reload it upon resume.

---

### Post by cbourner on 2007-01-16
meldroc's solution certainly improved it, but while the network came up OK, Gnome Network Manager didn't realise, and showed the animation as if it were trying to connect.

I'm going to try the new ipw3945 daemon next.

---

### Post by meldroc on 2007-01-16
I had that happen once.  Usually, I fixed that by quitting and restarting the network manager (knetworkmanager in my case.)

But usually, knetworkmanager is actually working correctly.  It starts with a spinning gear icon indicating it's trying to connect to something (suspending the machine will drop all wi-fi connections) but after a few seconds, it gets its act together and automatically connects to a known access point if it finds one (mine knows about my home router and my work router.)

I can tell if the wireless card is on speaking terms with the world by firing up a terminal and running iwconfig.

---

### Post by ecoxmit on 2007-02-02
I had the same problem. Meldroc solution seems to have fix it. Thanks!

---

### Post by MegaFlop on 2007-03-25
> **cbourner said:**
> I think I have fixed it.

By renaming the S*-ifup.sh file in /etc/acpi/resume.d to  S89-ifup.sh (I can't remember what number it was to start with) and also the S*-down-interfaces.sh file to S11-down-interfaces.sh in /etc/acpi/suspend.d hibernate is now working properly.

I have the occasional problem with suspend to RAM, but that is not networking related.

Let me know if this works for you!

Using the Ubuntu 7.04 beta. I was having a problem with ipw3945 resuming after suspend and I renamed the files according to the above (except on my machine there was no 'S' prefix) and it worked.

---

### Post by tommie74 on 2007-06-17
My computer with Xubuntu feisty had a problem with getting an ip-adress after waking from hibernation. I´ve solved this problem by changing /etc/default/acpi-support

Editing this file, look for the line below, where to add [networking] after that no problems anymore:

# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES="networking"

Hope this will work for you to,
Thomas.

---

