---
title: "user not allowed to do sudo after computer name changed"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by televisi on 2009-07-29
Hi guys,
I need urgent help, as I unable to do **sudo -i** or even **su** (as root is locked by default by Ubuntu server 9.04)

Originally my computer name is A, then I changed it to B by running the following script
**sudo changeComputerName**:
> 
echo "B" > /etc/hostname
/etc/init.d/hostname.sh stop
/etc/init.d/hostname.sh start
now, everytime I run** sudo -i **or **sudo <command>**, it gives the following error:
[COLOR=Red]**Sorry, user <USERNAME> is not allowed to execute '/bin/bash' as root on B**[/COLOR]
(as you can see, computer name has changed to B, and for some reason my user can't be identified in the new computer name)

Does anyone know how to resolve this issue?, as I can't run as root anymore...

Thanks heaps

---

### Post by wojox on 2009-07-29
Change it back to A :)

[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

---

### Post by televisi on 2009-07-29
Er... I tried the step written in [http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)
When I select "Drop to root shell prompt", it asked my root password.

As by default Ubuntu lock root user, it asked:
"Give root password for maintenance"

any other solution?

Thanks

---

### Post by televisi on 2009-07-29
Arrgghh!!! I think I know why my server screw up, I think I forgot to change the /etc/hosts accordingly...

I think this make the system confused, don't you think?
> 
/etc/hosts:

127.0.0.1           B
192.168.0.3        B            A


As you can see in the above, I forgot to replace the Alias and the ip address not match with below eth0 config

and my /etc/network/interfaces:
> 
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
     address 192.168.0.94
     netmask 255.255.255.0
     network 192.168.0.0
     broadcast 192.168.0.255
     gateway 192.168.0.254
     dns-nameservers 192.168.0.254


Ps: Even I unable to do sudo command, I still able to ping internet

---

### Post by wojox on 2009-07-29
Do:

```
cat /etc/hosts
```

Paste it up here.

---

### Post by AndyCee on 2009-07-29
I'd restart in single-user mode (CLI only) and put A back into /etc/hostname.

---

### Post by wojox on 2009-07-29
Still have your CD:

[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

---

### Post by CatKiller on 2009-07-29
> **televisi said:**
> Arrgghh!!! I think I know why my server screw up, I think I forgot to change the /etc/hosts accordingly...

Yep. If /etc/hosts and /etc/hostname disagree on what the computer is called, sudo doesn't work. Boot into single-user mode or from the live cd and change /etc/hosts to match what /etc/hostname says the computer should be called.

---

### Post by televisi on 2009-07-29
> **AndyCee said:**
> I'd restart in single-user mode (CLI only) and put A back into /etc/hostname.
I tried the single-user mode as written in:
> - [http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)
- and [http://digitalpbk.blogspot.com/2009/03/reset-root-password-linux-fedora-debian.html](http://digitalpbk.blogspot.com/2009/03/reset-root-password-linux-fedora-debian.html)

-when I add "single" at the end of "Kernel recovery mode":
it displaying the GUI Recovery Menu, and when I choose "Drop to root shell prompt", it asks the root password

- when I add "single init=/bin/bash" at the end of "Kernel recovery mode":
my keyboard just freeze and I unable to type anything from the shell :(

> **wojox said:**
> Still have your CD:

[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)
As I have Ubuntu server 9.04 edition, when I put in the cd, it doesn't have "try Ubuntu / Live CD" options, should I use Ubuntu Desktop 9.04 to 'simulate' the recovery process as written in>  [https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)  ?

---

### Post by sisco311 on 2009-07-29
> **televisi said:**
> Er... I tried the step written in [http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)
When I select "Drop to root shell prompt", it asked my root password.

As by default Ubuntu lock root user, it asked:
"Give root password for maintenance"

any other solution?

Thanks

sulogin is patched in Ubuntu, if the root account password is locked, then you are not prompted for a password in Recovery Mode.

So, you probably have enabled  the root account.

To lock the root account password or set up a new password:
[list=i]
[*] boot the computer

[*] at the grub menu [COLOR="Red"]highlight the Recovery Mode[/COLOR] option

[*] press e for edit

[*] highlight the kernel line and hit e for edit

[*] [COLOR="Red"]delete *ro single*[/COLOR] from the end of the line and replace it with *rw init=/bin/bash*

[*] hit Enter, then b to boot

[*] in the shell make sure that the root partition is mounted rw:
```
mount -o remount,rw /
```

[*] lock the password (or change it):
```
passwd -l root
```

to change the password (**not recommended**):
```
passwd root
```

[*] reboot the computer: press Ctrl+Alt+Del
[/list]

Now you can boot in Recovery Mode and resolve the sudo problem.

[list=1]

[*] make sure that the hostname is the same in both /etc/hostname and /etc/hosts

[*] > Sorry, user <USERNAME> is not allowed to execute '/bin/bash' as root on B

edit the sudoers file:
```
visudo
```

and allow your user to use sudo. add something like:
```
username ALL=(ALL) ALL
```

[list]
[*]username = the user name :)
[*]ALL = from any Host/IP
[*](ALL) = can run as any user
[*]ALL = all commands.
[/list]

your line in the sudoers file probably looks like this:
```
username oldhostname=(ALL) ALL
```
so, you have to change it to:
```
username newhostname=(ALL) ALL
```

[thread=1132821]HowTO: Sudoers Configuration[/thread]
[/list]

HTH

---

### Post by televisi on 2009-07-29
Sisco et all, Thanks for your comprehensive tips.

I've been following your steps below, and after try to boot, the linux just crash (I can't type anything through my keyboard, although the fact it gives root shell prompt).

> **sisco311 said:**
> 
[LIST=i]
[*] [COLOR=Red]delete *ro single*[/COLOR] from the end of the line and replace it with *rw init=/bin/bash*
[*] hit Enter, then b to boot
[*] in the shell make sure that the root partition is mounted rw:
[/LIST]


I suspect this is something to do with USB error, as this error comes up before the root shell prompt:

> 
[4.011132] usb 2-1.1: new low speed USB device using uhci_hcd and address 3 Done.
[4.204231] usb 2-1.1: configuration #1 choosen from 1 choise
root@(none):/#_


as far as I remember, I only add the following line at the last line of my /etc/sudoers:
> <USER> ALL=(ALL) NOPASSWD:/usr/bin/rsync

---

### Post by sisco311 on 2009-07-29
> **televisi said:**
> Sisco et all, Thanks for your comprehensive tips.

I've been following your steps below, and after try to boot, the linux just crash (I can't type anything through my keyboard, although the fact it gives root shell prompt).



I suspect this is something to do with USB error, as this error comes up before the root shell prompt:



as far as I remember, I only add the following line at the last line of my /etc/sudoers:

Well, you can try to start sh (dash) instead of bash. *wr init=/bin/sh*, but I doubt that it will work.

You can use a Live CD/DVD/USB stick to resolve the problem.
You don't need a GUI for this, so you can use the alternate or server install CD as well as any other distro's Live CD.

Assuming that you use the server install cd:
[list]
[*] boot the cd :)
[*] switch to a virtual terminal: Ctrl+Alt+F2
[*] mount the root partition:
```
mkdir /mnt/ubuntu
mount -t auto -o defaults /dev/sda1 /mnt/ubuntu

```

replace /dev/sda1 with the root partition (use *fdisk -l* to list the partitions)

[*]lock the root account:
```
cp /mnt/ubuntu/etc/shadow /mnt/ubuntu/etc/shadow-backup
```

```
nano /mnt/ubuntu/etc/shadow
```

You will see something like:
```
root:$6$A3SATtpZ$4Fa5Ux.oT6w1uN0oScYb3Cv/UuADx5I6yEuiAiAxxkrOpLLOOLZ...:14438:0:99999:7:::

```

$6$A3SATtpZ$4Fa5Ux.oT6w1uN0oScYb3Cv/UuADx5I6yEuiAiAxxkrOpLLOOLZ.... is the encrypted password. 

put a ! before it in order to lock the account:

```
root:**!**$6$A3SATtpZ$4Fa5Ux.oT6w1uN0oScYb3Cv/UuADx5I6yEuiAiAxxkrOpLLOOLZ....:14438:0:99999:7:::

```
save the file and exit (Ctrl+x, y Enter) 

[*]reboot:
```
reboot
```
you should be able to boot in recovery mode.[/list]

---

### Post by televisi on 2009-07-29
> **sisco311 said:**
> Well, you can try to start sh (dash) instead of bash. *wr init=/bin/sh*, but I doubt that it will work.
Yes the above technique resulting the same, crash and hang and unable to type anything
 
> **sisco311 said:**
>  
You can use a Live CD/DVD/USB stick to resolve the problem.
You don't need a GUI for this, so you can use the alternate or server install CD as well as any other distro's Live CD.
 
 

Assuming that you use the server install cd:
[LIST]
[*]boot the cd :)
[*]switch to a virtual terminal: Ctrl+Alt+F2
[*]mount the root partition:
```
mkdir /mnt/ubuntu
mount -t auto -o defaults /dev/sda1 /mnt/ubuntu

```
 
replace /dev/sda1 with the root partition (use *fdisk -l* to list the partitions)
[/LIST]Hi Sisco, correct me if I'm wrong, the step I've done:
[LIST]
[*]Boot Using Ubuntu Desktop 8.04 Live CD
[*]Select "try Ubuntu without installing anything in your PC"
[*]Once the GUI comes up, pressing CTRL + ALT + F2
[*]mkdir /mnt/ubuntu
[/LIST]Error:
```
mkdir: cannot create directory `/mnt/ubuntu': Permission denied
```
[LIST]
[*]fdisk -l
[/LIST]Error: 
```
Cannot open /dev/sda
Cannot open /dev/sdb

```
 
Please note the following GRUB details I retrievewhen I edit the "Kernel Recovery mode"
```
kernel /vmlinuz-2.6.28-11-server root=/dev/mapper/VG--data-VG--root ro quiet splash
```
 
Would that error message (Cannot open /dev/sda) something to do with LVM I use? 
 
Thanks heaps for your step-by-step solution!!!

---

### Post by t0p on 2009-07-29
> **televisi said:**
> Yes the above technique resulting the same, crash and hang and unable to type anything
 
Hi Sisco, correct me if I'm wrong, the step I've done:
[LIST]
[*]Boot Using Ubuntu Desktop 8.04 Live CD
[*]Select "try Ubuntu without installing anything in your PC"
[*]Once the GUI comes up, pressing CTRL + ALT + F2
[*]mkdir /mnt/ubuntu
[/LIST]Error:
```
mkdir: cannot create directory `/mnt/ubuntu': Permission denied
```
[LIST]
[*]fdisk -l
[/LIST]Error: 
```
Cannot open /dev/sda
Cannot open /dev/sdb

```
 
Please note the following GRUB details I retrievewhen I edit the "Kernel Recovery mode"
```
kernel /vmlinuz-2.6.28-11-server root=/dev/mapper/VG--data-VG--root ro quiet splash
```
 
Would that error message (Cannot open /dev/sda) something to do with LVM I use? 
 
Thanks heaps for your step-by-step solution!!!

1. When you want to create the directory /mnt/ubuntu, you need to use sudo, ie

```
sudo mkdir /mnt/ubuntu
```

2.  You've booted into a live cd session, so your hard disk is unmounted.  (I assume /dev/sda and /dev/sdb are on the hard disk?)  So you need to mount them before you can open them.

---

### Post by televisi on 2009-07-29
> **t0p said:**
> 1. When you want to create the directory /mnt/ubuntu, you need to use sudo, ie
Ah... silly me (I'm such a newbie hehe)...
 
Okay I've done:
 
[html] 
$sudo fdisk -l
it displays:
 
/dev/sda1 *                         Linux
/dev/sda2                            Extended
/dev/sda5                            Linux LVM
 
 
/dev/sdb                              Linux LVM
[/html]
 
now, when I 
```
sudo mount -t auto -o defaults /dev/sda1 /mnt/ubuntu
ls -al

```
there is no /etc/ folder, only some memtest86+.bin, grub folder (I guess this is Live CD content)
 
so I try
```
sudo mount -t auto -o defaults /dev/sda5 /mnt/ubuntu
ls -al

```
Error:
```
 
mount: unknown filesystem type 'LVM2_member'

```
 
AFAIK, to mount LVM, I usually mount it by using /dev/mapper/VG/... but I can't do it now as there is no mapper directory inside /dev....
 
Thanks

---

### Post by sisco311 on 2009-07-30
> **televisi said:**
> 
now, when I 
```
sudo mount -t auto -o defaults /dev/sda1 /mnt/ubuntu
ls -al

```
there is no /etc/ folder, only some memtest86+.bin, grub folder (I guess this is Live CD content)
 

That's probably the /boot partition.

> **televisi said:**
> ```

mount: unknown filesystem type 'LVM2_member'

```
 
AFAIK, to mount LVM, I usually mount it by using /dev/mapper/VG/... but I can't do it now as there is no mapper directory inside /dev....
 
Thanks

[Mounting LVM Disks from Ubuntu LiveCD]("http://specialkevin.com/?p=97")

---

### Post by televisi on 2009-07-30
AWESOME, it works like a charm!!!
Apparently, not only my /etc/hostname screwed up, my super user also no longer under "admin"; which resulting me unable to do any "sudo command"

Now I can sleep better tonight, knowing that I don't have to format company's fileserver.
Tomorrow, I'll summarize the result so everyone that had some problem able to solve it quickly

Thanks so much everyone!!!!

---

