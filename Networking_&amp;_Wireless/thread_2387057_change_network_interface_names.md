---
title: "change network interface names"
date: 2018-03-14
forum: Networking &amp; Wireless
---

### Post by delfiler on 2018-03-14
well now i got a fun problem for you guys, on my ubuntu server i have four network interfaces two of which are built in and are properly called eth1 and eth2 but the other two are called some long line of gibberish (not super long like 23 characters). all i want is to change their names to be like the built in ones, nice and short

now i know for a fact that the following code isn't the solution:
```
nano /etc/network/interfaces
```
that let's me just activate the interfaces so that i can use the as a network interface that can connect to the internet, no what i want is to adjust how they are called (i know i might be repeating myself).
so i hope someone knows how to do this

---

### Post by praseodym on 2018-03-14
It is from the package "biosdevname". One "recovery" option is
```

sudo apt-get purge biosdevname
sudo update-initramfs -u -k all
```
Reboot and check
```

ifconfig -a
```
You may need to adjust your "interfaces" file again

---

### Post by delfiler on 2018-03-15
> **praseodym said:**
> It is from the package "biosdevname". One "recovery" option is
```

sudo apt-get purge biosdevname
sudo update-initramfs -u -k all
```
Reboot and check
```

ifconfig -a
```
You may need to adjust your "interfaces" file again

and you are sure that i can change the names from the long gibberish to something proper like ethX

---

### Post by praseodym on 2018-03-15
It should change automatically back to eth0, eth1, wlan0, wlan1, etc.

[https://stackoverflow.com/questions/27112436/how-does-biosdevname-really-work](https://stackoverflow.com/questions/27112436/how-does-biosdevname-really-work)

---

### Post by Hadaka on 2018-03-15
Hi, if the Ubuntu version is older than 16.04, then
 an edit and add will be needed for */etc/udev/rules.d/70-persistent-net.rules *
If the Ubuntu version is 16.04 or newer then...
[COLOR=#ff0000]*****[/COLOR]Before any commands are issued..please read the reference link. *Note comment #2.
 
This code allows for the verification of each command.
**Please** copy and paste one line at a time to avoid typo's
```
sudo cp /etc/default/grub /etc/default/grub.txt
cat /etc/default/grub.txt
dqs=`sudo sed -n '/splash/=' /etc/default/grub`
echo "$dqs"
sudo sed -i ''$dqs's/sh/& net.ifnames=0/1' /etc/default/grub
sudo sed -n "$dqs"p /etc/default/grub
sudo update-grub
```

#Quick Change Method
# *If you are feeling lucky and dont care to backup or verify...
```
sudo sed -i '11s/sh/& net.ifnames=0/1' /etc/default/grub
sudo update-grub
```

# ** How To Revert To Original File & Settings. **
#*Providing a backup file was created per instructions *
#*Copy and paste the following  2 commands to overwrite and restore
#* /etc/default/grub to the original configuration prior to changes.
```
sudo mv /etc/default/grub.txt /etc/default/grub
sudo update-grub
``` 
[COLOR=#ff0000]***Reference**[/COLOR]
[https://askubuntu.com/questions/767786/changing-network-interfaces-name-ubuntu-16-04](https://askubuntu.com/questions/767786/changing-network-interfaces-name-ubuntu-16-04)

---

