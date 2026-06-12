---
title: "Linux/XP on separate Drives, Howto configure Grub 2 script"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by dazz100 on 2010-05-22
Hi

I have WinXP and Ubuntu 9.10 installed on separate HDs.  I can boot off either HD by configuring the boot order in the BIOS.  Not very user friendly.  I need to configure Grub 2 to boot off either HD and OS.

When I boot Ubuntu, no Grub menu is displayed.

I have read up on Grub 2 configuration. I know that I need to edit/write a script stored in /etc/grub.d/.  I haven't been able to find out the right boot command to put in the script.  

I see how the sintax works. How to I figure out the specific boot command for Win XP??

Any help would be much appreciated.

---

### Post by Darkness Des on 2010-05-22
When you boot into Linux, go into the terminal (Applications -> Accessories -> Terminal) and run the following command:
```
sudo os-prober
```
and post the output here. If it picks up Windows XP, run
```
sudo update-grub
```
and that should also pick up Windows XP. If it's just that Grub doesn't pick up XP, please reply and I'll help with that.

---

### Post by wilee-nilee on 2010-05-22
> **dazz100 said:**
> Hi

I have WinXP and Ubuntu 9.10 installed on separate HDs.  I can boot off either HD by configuring the boot order in the BIOS.  Not very user friendly.  I need to configure Grub 2 to boot off either HD and OS.

When I boot Ubuntu, no Grub menu is displayed.

I have read up on Grub 2 configuration. I know that I need to edit/write a script stored in /etc/grub.d/.  I haven't been able to find out the right boot command to put in the script.  

I see how the sintax works. How to I figure out the specific boot command for Win XP??

Any help would be much appreciated.

You say 2 HD's but is this a wubi install? 
This script will be the best thing to post in code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by dazz100 on 2010-05-22
Hi

The output from <update-grub> is below.


user@Ubuntu-Desktop:~$ sudo os-prober
[sudo] password for user: 
/dev/sdb1:Microsoft Windows XP Professional:Windows:chain
user@Ubuntu-Desktop:~$ sudo update-grub
error: cannot open `/dev/sda' while attempting to get disk size
error: cannot open `/dev/sda' while attempting to get disk size
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
error: cannot open `/dev/sda' while attempting to get disk size
grub-probe: error: Cannot find a GRUB drive for /dev/sdc5.  Check your device.map.

error: cannot open `/dev/sda' while attempting to get disk size
grub-probe: error: Cannot find a GRUB drive for /dev/sdc5.  Check your device.map.

Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sdb1
error: cannot open `/dev/sda' while attempting to get disk size
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

done
user@Ubuntu-Desktop:~$ 


When I checked the device.map file, it contained this line:

(hd0)   /dev/sda



so does that mean I should add to device.map the line?

(hd1)  /dev/sdb


Without making any changes to the device.map file, I rebooted.
I got a Grub menu displayed.

I can select Linux and boot OK.

When selecting the Windows menu choice, I got an error message
Invalid signature.

---

### Post by dazz100 on 2010-05-23
Hi

I found a bug report [here ]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/448557")

It seems to describe my problem but it should have been fixed.  


I have just found this link [here]("http://blog.redbranch.net/2010/01/grub-2-windows-7.html").  It seems to have a solution.  I will try it when I get back to my PC.

---

### Post by oldfred on 2010-05-23
You must have installed with only one drive connected so it only sees one.

If it complains about a device map
sudo grub-mkdevicemap
sudo update-grub

---

### Post by dazz100 on 2010-05-24
Hi

Did that and got the following:

user@Ubuntu-Desktop:~$ sudo grub-mkdevicemap
[sudo] password for user: 
user@Ubuntu-Desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sdb1
done
user@Ubuntu-Desktop:~$ 

This looks promising so I am going to restart and see if I can boot XP.

---

### Post by dazz100 on 2010-05-24
Sweet.

I am writing this on XP after selecting from the GRUB menu.

This one is SOLVED.

Thanks for all the helpful advice.

---

