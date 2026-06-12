---
title: "nfs shares in /etc/fstab not loaded on boot in 18.04"
date: 2018-05-24
forum: Networking &amp; Wireless
---

### Post by RobertLos on 2018-05-24
Hi, I have some nfs shares to my synology nas configured in /etc/fstab. After installing ubuntu 18.04 these shares are not loaded on boot but I have to manually mount by entering 
```
sudo mount -a
```
for them to be loaded.

the relevant lines in /etc/fstab are:

```

192.168.0.20:/volume1/music			/var3/ds415/music			nfs		user,auto 	0	0
192.168.0.20:/volume1/photo			/var3/ds415/photo			nfs		user,auto	0	0
192.168.0.20:/volume1/video			/var3/ds415/video			nfs		user,auto	0	0
192.168.0.20:/volume1/backups		/var3/ds415/ds415_archives	nfs		user,auto	0	0

```

The main difference I see towards my previous 16.04.4 installation was that the network manager has changed. It now uses /etc/netplan instead of /etc/network/interfaces Can that have anything to to with it?

---

### Post by VincentSKF on 2018-07-13
Same issue here...
it appears that for some reason, ubuntu tries to mount the folder before nsf is loaded during boot...no idea how to change this, but a (messy) workaround is to create a bash script (say runfstab.sh) with:
sleep 30s (or something else)
mount -a
and to schedule a cron job at reboot (edit crontab -eu root with : @reboot /pathtofile/runfstab.sh)
(for some reason the cron job @reboot is also often run before nfs is loaded, hence the sleep 30s, which is probably way too long)

hope that helps

Vincent

---

### Post by HNmYk3h on 2018-07-13
Try the _netdev option along with user,auto.

---

### Post by hsantos74 on 2018-08-26
> **HNmYk3h said:**
> Try the _netdev option along with user,auto.

Can you give an example... I tried to had the option...but doesn't seem to work.

Thanks

---

### Post by hsantos74 on 2018-08-26
> **RobertLos said:**
> Hi, I have some nfs shares to my synology nas configured in /etc/fstab. After installing ubuntu 18.04 these shares are not loaded on boot but I have to manually mount by entering 
```
sudo mount -a
```
for them to be loaded.


Found a solution?

---

### Post by Morbius1 on 2018-08-27
How about this:

[1] Create a file at: **/etc/network/if-up.d/fstab**


  [2] Add this to it:
  ```
#!/bin/sh
mount -a

```  [3] Make the file executable:
  ```
sudo chmod +x /etc/network/if-up.d/fstab 
```  

You are directing the system at boot time to issue a "mount -a" after the network stack is up and operation which if it's like a cifs mount in fstab is the reason your shares are not mounting at boot.

---

### Post by vitaly9 on 2019-01-14
For me the solution was to edit the netplan configuration (**/etc/netplan/50-cloud-init.yaml**)file and set interface as optional: false

---

### Post by N!co on 2019-02-12
> **Morbius1 said:**
> How about this:

[1] Create a file at: **/etc/network/if-up.d/fstab**


  [2] Add this to it:
  ```
#!/bin/sh
mount -a

```  [3] Make the file executable:
  ```
sudo chmod +x /etc/network/if-up.d/fstab 
```  

You are directing the system at boot time to issue a "mount -a" after the network stack is up and operation which if it's like a cifs mount in fstab is the reason your shares are not mounting at boot.

Brilliant! thanks.

---

