---
title: "I accidentally removed gnome keyring and a lot other apps"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by hojgaard on 2009-02-19
Hello.
I have a problem. I was annoyed by the gnome keyring so i decided to remove it. What i didnt saw when i removed it was that apturl, fast user switch applet, gdebi, gdm, gksu, gnome app install, gnome netstatus applet, gparted, hwtest gtk, network manager gnome, software properties gtk, ubufox, ubuntu desktop, update manager, update notifier and usb creator was removed all together when i did that. Now my ubuntu 8.10 wont start (of course). How do i install all those apps again to get my ubuntu to work?

---

### Post by semitone36 on 2009-02-19
lol If you have access to your terminal still I would try sudo apt-get install APP_NAME for each of the apps.  If you lost your terminal too, youre gonna have to reinstall ubuntu

---

### Post by Temposs on 2009-02-19
open a terminal and type this:

```
sudo apt-get install ubuntu-desktop
```

When you uninstall one application linked with ubuntu-desktop, it uninstalls everything.

---

### Post by hojgaard on 2009-02-19
Yeah i found out ;P

But i restarted and i cant get into ubuntu again, so i cant connect to the internet through command line. When i start my computer it gets to commandline...

is it impossible to connect to the internet through that?

---

### Post by Temposs on 2009-02-19
Does your computer automatically connect usually, through a wifi connection or ethernet cable? If so, it should be connected to the internet even if you don't have the graphical interface. You can test your connection with:

```
ping www.yahoo.com
```

or whatever site you like
EDIT: For me, the output of the above command is:

```
ping www.yahoo.com
PING www-real.wa1.b.yahoo.com (69.147.76.15) 56(84) bytes of data.
64 bytes from f1.www.vip.re1.yahoo.com (69.147.76.15): icmp_seq=1 ttl=52 time=71.6 ms
64 bytes from f1.www.vip.re1.yahoo.com (69.147.76.15): icmp_seq=2 ttl=52 time=61.9 ms
64 bytes from f1.www.vip.re1.yahoo.com (69.147.76.15): icmp_seq=3 ttl=52 time=56.7 ms
64 bytes from f1.www.vip.re1.yahoo.com (69.147.76.15): icmp_seq=4 ttl=52 time=63.1 ms
64 bytes from f1.www.vip.re1.yahoo.com (69.147.76.15): icmp_seq=5 ttl=52 time=58.7 ms
64 bytes from f1.www.vip.re1.yahoo.com (69.147.76.15): icmp_seq=6 ttl=52 time=56.3 ms
^C
--- www-real.wa1.b.yahoo.com ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5021ms
rtt min/avg/max/mdev = 56.301/61.415/71.644/5.219 ms

```

---

### Post by hojgaard on 2009-02-19
No unfortunally not...
says unknown host...

---

### Post by mikewhatever on 2009-02-19
> **hojgaard said:**
> Hello.
I have a problem. I was annoyed by the gnome keyring so i decided to remove it. What i didnt saw when i removed it was that apturl, fast user switch applet, gdebi, gdm, gksu, gnome app install, gnome netstatus applet, gparted, hwtest gtk, network manager gnome, software properties gtk, ubufox, ubuntu desktop, update manager, update notifier and usb creator was removed all together when i did that. Now my ubuntu 8.10 wont start (of course). How do i install all those apps again to get my ubuntu to work?

If you have the installation cd, try booting the recovery mode (usually the second boot option), then insert the cd, run **apt-cdrom ad**, then **apt-get install ubuntu-desktop**. This should reinstall the removed files from the cd.

---

### Post by tarps87 on 2009-02-19
You should be able to connect using the command line. First how are you connected wifi or by wire? If you can connect using a wire is will be easier. Do you use a router or is it dial-up?

Can you check if you have an IP
```
sudo ifconfig
```
If you are not sure, can you post the output here

Edit:
Or you can use mikewhatever's more sensible and easier suggestion :)

---

### Post by hojgaard on 2009-02-19
i tried with 
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ubuntu-desktop
but it did not work...

---

### Post by Temposs on 2009-02-19
You have to tell the output when you type each of the commands, or we cannot help you from there.

---

### Post by mikewhatever on 2009-02-19
> **hojgaard said:**
> i tried with 
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ubuntu-desktop
but it did not work...

Sorry to hear that. What didn't work exactly? Which command? Did you get any errors?
I don't think it matter, but you don't need sudo in recovery mode, since you are root already.

---

