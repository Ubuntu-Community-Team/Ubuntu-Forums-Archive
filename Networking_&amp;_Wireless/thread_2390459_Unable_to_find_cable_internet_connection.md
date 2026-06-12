---
title: "Unable to find cable internet connection"
date: 2018-04-29
forum: Networking &amp; Wireless
---

### Post by fikafi08 on 2018-04-29
Hi everyone. 
First of all, I am sorry for my faults in English. 

I have a Asus computer and it has a default installed Windows. And I installed Ubuntu by taking some storage.

My problem is that when I plug in internet cable to my computer, Ubuntu does not notice it and i cannot use cable network on my Laptop. However, there is an important fact that my laptop can easily recognize Wifi on Ubuntu and on Windows it can connect both Wifi and cable internet. So the problem is on Ubuntu when networking is about using cable. Here is some commands which may be beneficial for clear understanding my problem;

Computer Properties:
7,7 GiB
Intel® Core™ i5-5200U CPU @ 2.20GHz × 4
Intel® HD Graphics 5500 (Broadwell GT2) 
64-bit
76,2 GB

```
aysegul@aysegul-X555LNB:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.19.0-32-generic.efi.signed root=UUID=4b5b4b33-7c92-4c96-a119-e13d92b71e81 ro quiet splash vt.handoff=7
```

```
aysegul@aysegul-X555LNB:~$ uname -a
Linux aysegul-X555LNB 3.19.0-32-generic #37~14.04.1-Ubuntu SMP Thu Oct 22 09:41:40 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

Because of long text, I used paste.ubuntu site, so i give you a link which contains my other commands/codes;

[https://paste.ubuntu.com/p/c6R4qP6Dyf/](https://paste.ubuntu.com/p/c6R4qP6Dyf/)

Thanks for reading and help.

---

### Post by praseodym on 2018-04-29
If wireless works, run

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.045.08-2_all.deb
sudo dpkg -i r8168-dkms_8.045.08-2_all.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot

---

### Post by fikafi08 on 2018-04-30
Hi,

The results are there:

[https://paste.ubuntu.com/p/M4ZxJCcv4M/](https://paste.ubuntu.com/p/M4ZxJCcv4M/)

@[**[COLOR=#000000]praseodym[/COLOR]**]("https://ubuntuforums.org/member.php?u=1411497")

---

### Post by praseodym on 2018-05-01
Checked the cable?

---

### Post by fikafi08 on 2018-05-01
I said on the post that
> However, there is an important fact that my laptop can easily recognize  Wifi on Ubuntu and on Windows it can connect both Wifi and cable  internet

So there is no problem about cable because it works on Windows. The problem is about ubuntu.

---

### Post by fikafi08 on 2018-05-01
Is there anyone who helps ?

---

### Post by fikafi08 on 2018-05-03
The problem is still

---

### Post by jobtmp on 2018-05-03
Hi,

I have the same problem - no Wired connection while wi-fi works. Windows system (another one) works fine.  

Let,s hope someone will pay attention.

---

### Post by oldfred on 2018-05-04
Usually the issue is the other way around. Wired just works, but some models of wireless chips need drivers.

You may be able to run the script in sticky at top of this sub-forum. Mostly about the wireless issues, but also gives info on wired.

What does the wired connection show. You may have Internet icon at top right or in System Settings.
See my screen shot. Best not to post your unique hardware address.

---

### Post by jobtmp on 2018-05-04
Hi,

Re: wired connection settings.

In my Settings -> Network I cannot find any details but two options: VPN and Proxy (pls see the image attached).

Is it becouse I I dont have the UEFI or else? please advise.

---

### Post by oldfred on 2018-05-04
Unless there is a setting in your UEFI to turn on the network connection, UEFI or BIOS would not change network.

My UEFI only has a boot from network device option that mentions networking at all. And I have that off, so system does not search for network when booting slowing boot. But, network drivers are still loaded.

---

