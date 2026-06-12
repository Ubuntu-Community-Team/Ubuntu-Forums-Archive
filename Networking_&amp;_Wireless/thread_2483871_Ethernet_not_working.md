---
title: "Ethernet not working"
date: 2023-02-11
forum: Networking &amp; Wireless
---

### Post by kodex99 on 2023-02-11
I recently bought a new CPU (i5 12600) and motherboard (MSI PRO H610M-B DDR4) with Intel 1G LAN (Intel I219V Gigabit LAN controller), the ethernet connection to the router works out of the box on Windows 10/11, but on any Linux distribution it is not even detected. I also installed the drivers officially provided by Intel (e1000e Driver) but nothing, on boot in certain distributions I get this error: "e1000e nvm checksum is not valid". I've read that it works on Windows because it doesn't run this check, am I doomed to use Windows forever?

---

### Post by TheFu on 2023-02-13
> **kodex99 said:**
> I recently bought a new CPU (i5 12600) and motherboard (MSI PRO H610M-B DDR4) with Intel 1G LAN (Intel I219V Gigabit LAN controller), the ethernet connection to the router works out of the box on Windows 10/11, but on any Linux distribution it is not even detected. I also installed the drivers officially provided by Intel (e1000e Driver) but nothing, on boot in certain distributions I get this error: "e1000e nvm checksum is not valid". I've read that it works on Windows because it doesn't run this check, am I doomed to use Windows forever?

I know that a few years ago the I219V NIC had problems.  I'd have assumed those were corrected by now.  However, with a desktop, you can install a different NIC and use that for relatively little money.   I know that these devices work.
```
$ inxi -N
Network:   Device-1: Intel I211 Gigabit Network driver: igb 
           Device-2: Intel 82575GB Gigabit Network driver: igb 
```
as well as an Intel i210 and Intel 82574L as well.[/code]

I think it is smart to avoid Realtek and Marvell NICs.  I know that Broadcom makes some 2.5 Gbps and 10 Gbps NICs and are used in servers with good support too. I don't have the models handy. Sorry.  Intel NICs off load more of the work from the CPU than Realtek and have support for BSD flavors, which usually means Linux is also well supported.  Whenever I'm looking for new hardware, even if I don't plan to run BSD, I look for BSD support for that reason.

Oh ... on the cheaper end, you can find those NICs for $25 from reputable sellers.  I have a quad-port NIC with Intel 82575GB inside too. Works well.

---

### Post by slickymaster on 2023-02-13
*Thread moved to **Networking & Wireless**.*

---

### Post by chili555 on 2023-02-13
> I get this error: "e1000e nvm checksum is not valid"Please see: [http://superuser.com/questions/1104537/how-to-repair-the-checksum-of-the-non-volatile-memory-nvm-of-intel-ethernet-co](http://superuser.com/questions/1104537/how-to-repair-the-checksum-of-the-non-volatile-memory-nvm-of-intel-ethernet-co) Especially: "I used bootutil for Linux from Intel..." etc.

Also see post #7 here:  [https://ubuntuforums.org/showthread.php?t=2351572&highlight=checksum](https://ubuntuforums.org/showthread.php?t=2351572&highlight=checksum)

---

### Post by TheFu on 2023-02-13
Definitely don't replace/add hardware if it isn't needed!  

It is good to see that the fix did happen a few years ago and that something odd seems to have happened in this setup.

BTW, often if we take the error message text, add "ubuntu" and do a web search, some possible fixes are shown.
Whenever posting questions, please include the Ubuntu release number, kernel and any DE, if it is a point-n-click issue.  Some examples:
```
$ inxi -S
System:
  Host: regulus Kernel: 5.4.0-139-generic x86_64 bits: 64 
  Desktop: FVWM2 2.6.8 Distro: Ubuntu 20.04.5 LTS (Focal Fossa) 
```
will get the release, WM/DE and kernel, but that tool isn't included in Ubuntu by default.  

```
$ hostnamectl
   Static hostname: regulus
         Icon name: computer-vm
           Chassis: vm
        Machine ID: <long number>
           Boot ID: <diff long number>
    Virtualization: kvm
  Operating System: Ubuntu 20.04.5 LTS
            Kernel: Linux 5.4.0-139-generic
      Architecture: x86-64
```
is included in ubuntu (probably part of systemd) and provides the release and kernel version.

When it comes to drivers, the kernel version is always important.

---

