---
title: "Help with network adapter (rtl8821ce) in Ubuntu"
date: 2019-07-21
forum: Networking &amp; Wireless
---

### Post by ron-in-reno on 2019-07-21
I have never used Linux before. I installed Ubuntu (ubuntu-19.04-desktop-amd64.iso) on my flash drive using Rufus and there seems to be no support whatsoever for the network adapter (Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter). Everything works fine in Windows 10. Windows 10 is my only available platform to access internet or any networking on my Lenovo IdeaPad S145 laptop. I use WiFI.
 
I cannot find the Linux driver for this chipset. Even if I did, I have no idea how to install or compile it. I’m unfamiliar with Linux and its command line functions. What little documentation I found online suggests using a temporary wired ethernet connection to help with installation. Unfortunately, I don’t have that option in Ubuntu.
Could someone please provide elementary step-by-step instructions to get this network adapter working so I can access the internet on WiFi. I would like to eventually get away from windows.

Hope someone can help.

---

### Post by jeremy31 on 2019-07-21
If you have Ubuntu installed, in terminal do
```
sudo apt install git dkms build-essential
git clone https://github.com/tomaspinho/rtl8821ce.git
cd rtl8821ce
sudo ./dkms-install.sh
```

Secure Boot will need to be disabled in UEFI/BIOS, you can check Secure Boot status with
```
mokutil --sb-state
```

---

### Post by SeijiSensei on 2019-07-21
> **ron-in-reno said:**
> Windows 10 is my only available platform to access internet or any networking on my Lenovo IdeaPad S145 laptop. I use WiFI.
It's always useful to have an Ethernet cable available in case you have wifi issues.  Then you can plug the laptop directly into one of the "LAN" ports on your router with the cable.  Amazon sells them for as little as [four bucks]("https://www.amazon.com/AmazonBasics-RJ45-Cat-6-Ethernet-Patch-Cable-5-Feet-1-5-Meters/dp/B00N2VILDM/").

---

### Post by ron-in-reno on 2019-07-21
That Dose not work. Here is what happens while Ubuntu:

```
sudo apt install git dkms build-essentialReading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version (12.6ubuntu1).
build-essential set to manually installed.
The following additional packages will be installed:
  git-man liberror-perl
Suggested packages:
  menu git-daemon-run | git-daemon-sysvinit git-doc git-el git-email git-gui gitk gitweb git-cvs git-mediawiki git-svn
The following NEW packages will be installed:
  dkms git git-man liberror-perl
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 4969 kB/5036 kB of archives.
After this operation, 34.2 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err:1 http://archive.ubuntu.com/ubuntu disco/main amd64 liberror-perl all 0.17027-2
  Temporary failure resolving 'archive.ubuntu.com'
Err:2 http://archive.ubuntu.com/ubuntu disco/main amd64 git-man all 1:2.20.1-2ubuntu1
  Temporary failure resolving 'archive.ubuntu.com'
Err:3 http://archive.ubuntu.com/ubuntu disco/main amd64 git amd64 1:2.20.1-2ubuntu1
  Temporary failure resolving 'archive.ubuntu.com'
Get:4 cdrom://Ubuntu 19.04 _Disco Dingo_ - Release amd64 (20190416) disco/main amd64 dkms all 2.6.1-4ubuntu1 [67.0 kB]
E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/libe/liberror-perl/liberror-perl_0.17027-2_all.deb  Temporary failure resolving 'archive.ubuntu.com'
E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/git/git-man_2.20.1-2ubuntu1_all.deb  Temporary failure resolving 'archive.ubuntu.com'
E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/git/git_2.20.1-2ubuntu1_amd64.deb  Temporary failure resolving 'archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

Also, what and were is "[COLOR=#000000]Secure Boot"? [/COLOR]When I enter mokutil --sb-state I get the following:

```
EFI variables are not supported on this system
```

---

### Post by SeijiSensei on 2019-07-22
Did you run "sudo apt update" first?

---

### Post by jeremy31 on 2019-07-22
> **ron-in-reno said:**
> That Dose not work. Here is what happens while Ubuntu:

```
sudo apt install git dkms build-essentialReading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version (12.6ubuntu1).
build-essential set to manually installed.
The following additional packages will be installed:
  git-man liberror-perl
Suggested packages:
  menu git-daemon-run | git-daemon-sysvinit git-doc git-el git-email git-gui gitk gitweb git-cvs git-mediawiki git-svn
The following NEW packages will be installed:
  dkms git git-man liberror-perl
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 4969 kB/5036 kB of archives.
After this operation, 34.2 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err:1 http://archive.ubuntu.com/ubuntu disco/main amd64 liberror-perl all 0.17027-2
  Temporary failure resolving 'archive.ubuntu.com'
Err:2 http://archive.ubuntu.com/ubuntu disco/main amd64 git-man all 1:2.20.1-2ubuntu1
  Temporary failure resolving 'archive.ubuntu.com'
Err:3 http://archive.ubuntu.com/ubuntu disco/main amd64 git amd64 1:2.20.1-2ubuntu1
  Temporary failure resolving 'archive.ubuntu.com'
Get:4 cdrom://Ubuntu 19.04 _Disco Dingo_ - Release amd64 (20190416) disco/main amd64 dkms all 2.6.1-4ubuntu1 [67.0 kB]
E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/libe/liberror-perl/liberror-perl_0.17027-2_all.deb  Temporary failure resolving 'archive.ubuntu.com'
E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/git/git-man_2.20.1-2ubuntu1_all.deb  Temporary failure resolving 'archive.ubuntu.com'
E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/git/git_2.20.1-2ubuntu1_amd64.deb  Temporary failure resolving 'archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

Also, what and were is "[COLOR=#000000]Secure Boot"? [/COLOR]When I enter mokutil --sb-state I get the following:

```
EFI variables are not supported on this system
```

Can you USB tether to a smartphone in order to run the commands?

---

### Post by pablo3212olbap on 2019-09-08
Hi, this is almost the same, it dosen't work? 
Please let me know if that work because I'm thinking to buying this laptop. Thank you.

---

### Post by wildmanne39 on 2019-09-08
Hello pablo3212olbap if you need help please start your own thread instead of posting in someone else's, please read the forum rules:

[https://ubuntuforums.org/misc.php?do=showrules](https://ubuntuforums.org/misc.php?do=showrules)

You posted a link with appropriate language which I have removed.

---

