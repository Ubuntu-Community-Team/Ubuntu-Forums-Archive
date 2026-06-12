---
title: "gigabyte ga-z170x-gaming g1 mobo with e2400 killer lan not detecting"
date: 2016-06-06
forum: Networking &amp; Wireless
---

### Post by aor2 on 2016-06-06
Hi, I have new mobo ga-z170x-gaming g1 with dual e2400 killer lan, but it wont detect on my ubuntu 14.04 ubuntu server edition. When i run lshw -c network, lan are tagged as unclaimed,

I follow procedure on this link [http://graymattercomputing.net/index.php/how-to/13-atheros-killer-e2400-on-ubuntu](http://graymattercomputing.net/index.php/how-to/13-atheros-killer-e2400-on-ubuntu) but it does not help me.

Can somebody help me fix this killer 2400 lan thing? 

Thanks a lot..

---

### Post by oldfred on 2016-06-06
Try 16.04, it has newer kernel, support software & drivers for Skylake systems.

I built a SFF system with Gigabyte model: Z170N-Gaming 5 motherboard.
But built system before 16.04 was released, but knew I needed 16.04 and it has worked without issue, since Feb.

---

### Post by aor2 on 2016-06-07
> **oldfred said:**
> Try 16.04, it has newer kernel, support software & drivers for Skylake systems.

I built a SFF system with Gigabyte model: Z170N-Gaming 5 motherboard.
But built system before 16.04 was released, but knew I needed 16.04 and it has worked without issue, since Feb.



Hi, Thanks for the reply, are there no option rtaher than upgrading to 16.04? Upgrading might affect my ltsp server since it is a AFS file server kerberos auth with ldap integration. It would perhaps complicate and bring another problem.. hahahahahahaha

---

### Post by jeremy31 on 2016-06-07
Moved to Networking

Try ```
sudo modprobe alx
echo 1969 e0a1 | sudo tee /sys/bus/pci/drivers/alx/new_id >/dev/null
```
It is from [this answer](http://askubuntu.com/a/674118/300665) and it should work but the instructions you followed should have worked

Please post ```
modinfo alx
```

---

### Post by aor2 on 2016-06-08
> **jeremy31 said:**
> Moved to Networking

Try ```
sudo modprobe alx
echo 1969 e0a1 | sudo tee /sys/bus/pci/drivers/alx/new_id >/dev/null
```
It is from [this answer]("http://askubuntu.com/a/674118/300665") and it should work but the instructions you followed should have worked

Please post ```
modinfo alx
```


Hi, thanks for the reply

This line[COLOR=#000000] **temporarily**[/COLOR] fix my problem. 
sudo modprobe alx
echo 1969 e0a1 | sudo tee /sys/bus/pci/drivers/alx/new_id >/dev/null

But when I try to reboot  the machine, networking again failed, Any idea? thanks a lot you save my day......

---

### Post by jeremy31 on 2016-06-08
This should work after reboots 
Create file named
```
/etc/udev/rules.d/99-alx.rules
```
Enter ```
ACTION=="add", ATTRS{idVendor}=="1969", ATTRS{idProduct}=="e0a1", RUN+="/sbin/modprobe alx" RUN+="/bin/sh -c 'echo 1969 e0a1 > /sys/bus/pci/drivers/alx/new_id'"
```

Save file and reboot

---

### Post by aor2 on 2016-06-08
> **jeremy31 said:**
> This should work after reboots 
Create file named
```
/etc/udev/rules.d/99-alx.rules
```
Enter ```
ACTION=="add", ATTRS{idVendor}=="1969", ATTRS{idProduct}=="e0a1", RUN+="/sbin/modprobe alx" RUN+="/bin/sh -c 'echo 1969 e0a1 > /sys/bus/pci/drivers/alx/new_id'"
```

Save file and reboot


Hi, Thanks for the reply,

I wonder udev .rules are for removable device,please correct me if i'm wrong, but I tried the solution and when rebooted still networking fails.

Thanks

---

### Post by jeremy31 on 2016-06-08
That solution has worked for others but we could try something else.  I was able to compile alx from 4.4 source code on a 14.04 laptop with a 3.13 kernel with some newer patches applied.  This is a bit experimental for now, we can start by backing up the existing alx module with
```
sudo mv /lib/modules/$(uname -r)/kernel/drivers/net/ethernet/atheros/alx/alx.ko /lib/modules/$(uname -r)/kernel/drivers/net/ethernet/atheros/alx/alx.ko.bak
```

Then make sure we can build modules
```
sudo apt-get install linux-headers-generic build-essential git
```

Then we copy my 4.4 patched source code from github
```
git clone https://github.com/jeremyb31/alx.git
cd alx
cp /usr/src/linux-headers-`uname -r`/.config ./
cp /usr/src/linux-headers-$(uname -r)/Module.symvers ./
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
sudo cp alx.ko /lib/modules/$(uname -r)/kernel/drivers/net/ethernet/atheros/alx/alx.ko
sudo rm /etc/udev/rules.d/99-alx.rules
sudo depmod -a
```

This should take care of a few different issues with alx
#1 it didn't support your device
#2 sometimes it needed MTU to be set to 8192 to work

And since you are using 14.04 you don't have to worry about the secure boot rules being enforced in kernel 4.4.0-20
Reboot

---

### Post by aor2 on 2016-06-08
> **jeremy31 said:**
> That solution has worked for others but we could try something else.  I was able to compile alx from 4.4 source code on a 14.04 laptop with a 3.13 kernel with some newer patches applied.  This is a bit experimental for now, we can start by backing up the existing alx module with
```
sudo mv /lib/modules/4.4.0-22-generic/kernel/drivers/net/ethernet/atheros/alx/alx.ko /lib/modules/4.4.0-22-generic/kernel/drivers/net/ethernet/atheros/alx/alx.ko.bak
```

Then make sure we can build modules
```
sudo apt-get install linux-headers-generic build-essential git
```

Then we copy my 4.4 patched source code from github
```
git clone https://github.com/jeremyb31/alx.git
cd alx
cp /usr/src/linux-headers-`uname -r`/.config ./
cp /usr/src/linux-headers-$(uname -r)/Module.symvers ./
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
sudo cp alx.ko /lib/modules/$(uname -r)/kernel/drivers/net/ethernet/atheros/alx/alx.ko
sudo rm /etc/udev/rules.d/99-alx.rules
sudo depmod -a
```

This should take care of a few different issues with alx
#1 it didn't support your device
#2 sometimes it needed MTU to be set to 8192 to work

And since you are using 14.04 you don't have to worry about the secure boot rules being enforced in kernel 4.4.0-20
Reboot



YAY! it is finally solve, your a true hokage.. ahahaha thanks a lot your a genius

This solution fix it..

```
sudo apt-get install linux-headers-generic build-essential git
```

Then we copy my 4.4 patched source code from github
```
git clone https://github.com/jeremyb31/alx.git
cd alx
cp /usr/src/linux-headers-`uname -r`/.config ./
cp /usr/src/linux-headers-$(uname -r)/Module.symvers ./
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
sudo cp alx.ko /lib/modules/$(uname -r)/kernel/drivers/net/ethernet/atheros/alx/alx.ko
sudo depmod -a
```


Thank you so much, for your time and support.. KUDOS...

BUT i dont know why when booting still "waiting for networ configration appear" until it reach in booting withour full network configuration (ip address can be ping already on this stage).. It is maybe or perhaps ok with me but It will slow down or consume more time the in boot process... Thanks anyway..

---

### Post by jeremy31 on 2016-06-09
When your kernel updates, your ethernet will fail again.  When that happens use my dkms version
```
sudo apt-get install dkms
sudo dkms add ./alx
sudo dkms build alx/2.0
sudo dkms install alx/2.0
```

Reboot

I am not sure why it is waiting for the network on boot

Please use "Thread tools" menu at top of the page to "Mark as solved"

---

### Post by aor2 on 2016-06-09
> **jeremy31 said:**
> When your kernel updates, your ethernet will fail again.  When that happens use my dkms version
```
sudo apt-get install dkms
sudo dkms add ./alx
sudo dkms build alx/2.0
sudo dkms install alx/2.0
```

Reboot

I am not sure why it is waiting for the network on boot

Please use "Thread tools" menu at top of the page to "Mark as solved"


Hi, 

Ok, this is noted. ill just wait for an update to test,anyhow thanks a lot Sir...I am now relieved.. ahahahahahaha, THANKS......

---

### Post by rsaajamsa on 2016-10-15
jeremy31 you are a life saver. 

The only thing I had to do was edit my /etc/network/interfaces to include the following:

```
auto eth0
iface eth0 inet dhcp
```

Thanks again for your work.

---

