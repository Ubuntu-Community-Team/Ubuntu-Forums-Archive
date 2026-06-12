---
title: "wireless trouble..."
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by dkobel on 2008-08-19
Hey, I'm setting up my dad with ubuntu on his brand new hp pavilion dv9910us. So far, most things are working well except the wireless. The restricted drivers are installed/enabled, but there is still no wireless internet. No matter if I switch on or off the wireless manually, it still does not show up or catch a signal (and when I access admin>networking it doesn't show up at all.)

can anyone kindly help me out?

---

### Post by Sam Lars on 2008-08-19
Could you post the output of
```
lspci | grep Network
```
One thing I would suggest in Ndiswrapper.

---

### Post by dkobel on 2008-08-19
nothing showed up when i did lspci ... however, i looked at some other stuff and i have an Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter. people say it's easy to install via madwifi (see this website: [http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work/](http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work/) ) but when I get to sudo make install i get this error:
> dennis@dennis-laptop:~/Desktop/madwifi-ng-r2756+ar5007$ sudo make install
cd: 1: can't cd to /lib/modules/2.6.24-21-server/build
Makefile.inc:66: *** /lib/modules/2.6.24-21-server/build is missing, please set KERNELPATH.  Stop.

I googled that, and it said something about making a symbolic link? things that i tried to make a symbolic link were vague and i don't know what they mean...

---

### Post by Sam Lars on 2008-08-19
Thanks for the info.
A link will just point to a path that does exist, so you don't have to copy the whole directory over.
Find in /lib/modules the latest kernel version you have, such as 2.6.24-20-generic.  Replace "yourversion" in the following command with the directory you find:
```
sudo ls /lib/modules/yourversion/build /lib/modules/2.6.24-21-server/build
```
If it complains about "directory does not exist" or something similar, then do
```
sudo mkdir /lib/modules/2.6.24-21-server
```
And try the first command again.

---

### Post by Ayuthia on 2008-08-19
> **Sam Lars said:**
> Thanks for the info.
A link will just point to a path that does exist, so you don't have to copy the whole directory over.
Find in /lib/modules the latest kernel version you have, such as 2.6.24-20-generic.  Replace "yourversion" in the following command with the directory you find:
```
sudo ls /lib/modules/yourversion/build /lib/modules/2.6.24-21-server/build
```
If it complains about "directory does not exist" or something similar, then do
```
sudo mkdir /lib/modules/2.6.24-21-server
```
And try the first command again.

I think Sam Lars meant to say:
```
sudo ln -s /lib/modules/yourversion/build /lib/modules/2.6.24-21-server/build
```

This will create the symbolic link.

---

### Post by nicedude on 2008-08-19
If you find that you have a AR5007 Atheros adapter and are using Ubuntu Hardy 32bit then I have a guide that is step by step to install it with a current Madwifi driver. The driver I have linked in my guide is tested and works with WEP & WPA as well as supports both Monitor mode and packet injection for hacking purposes. This guide and especially my driver are only for 32bit Hardy with an AR5007 , So if that is what you are working with it will work. Note no Madwifi drivers work with USB devices so anyone with an Atheros based USB wifi device are stuck with Ndiswrapper for drivers. But if its in your laptop its not USB based obviously.

To see if you do have a AR5007 you should both run the following command as well as Google your laptop model like so "model wifi chipset" as sort of a confirmation. Here is the command to check and I will show you what it should be in the output to verify you have a AR5007

lspci -n

In the output you should see one device with the following ID -> 168c:001c (rev 01) . it will most likely be toward the bottom of the list of output.

HERE IS WHAT MINE SHOWS AS               
05:00.0 0200: 168c:001c (rev 01)

Here is a link to my guide if anyone has this adapter and needs help to install it.

[http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)

If you get stuck using my guide or don't understand something then just PM me and I will help you.

---

### Post by dkobel on 2008-08-22
i use the ar242x, not 5007. :(

---

