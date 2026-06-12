---
title: "Cisco VPN Client"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by fabriciogomes on 2007-04-21
Hi,

I recently installed Ubuntu 7.04 and tried to install the Cisco VPN client to access my university's wireless network, but the instalation fails. When using ubuntu 6.10 i don't get the error and it works just fine. Can anyone give me a hand at this?

---

### Post by K0LO on 2007-04-21
I have the same issue. The VPN client version that I'm using is 4.8.00. If I boot with an older kernel (2.6.17-11-386) then the VPN client works fine. Booting with the latest kernel (2.6.20-15-386) does not work. It seems to build OK but then when trying to start the vpn subsystem I get the error "CiscoVPN/cisco_ipsec.ko -1 Invalid module format".

Maybe the VPN client isn't compatible with kernel 2.6.20? I'll check with the IT folks at work on Monday.

Meanwhile you can boot into Ubuntu 7.04 but use the older kernel as a workaround.

---

### Post by K0LO on 2007-04-21
Fabriciogomes:

I got this working by patching the installer files. Here is an article that tells how to do that:
[http://tuxx-home.at/archives/2007/04/10/T15_55_43/](http://tuxx-home.at/archives/2007/04/10/T15_55_43/)

But you need to change the command for applying the patch file to:```
sudo patch -i <filename>
```where <filename> is the path to the patch file.

---

### Post by teslaspigeon on 2007-05-14
Thanks for the informative post...   I'm closer, but I must still be missing something.

I used the patch:  vpnclient-linux-2.6.19+-rev1.diff
I even tried doing the patch command both with and without the "-i" flag.

It seemed to build OK, but when trying to start the module, I still get:
# /etc/init.d/vpnclient_init start
Starting /opt/cisco-vpnclient/bin/vpnclient: insmod: error inserting '/lib/modules/2.6.20-15-386/CiscoVPN/cisco_ipsec.ko': -1 Invalid module format

my kernel version is 2.6.20-15-386   and I used:
Directory containing linux kernel source code []/lib/modules/2.6.20-15-generic/build


K0LO - did you have any luck?
:confused:

---

### Post by teslaspigeon on 2007-05-14
OK.   finally got it.

I had to install the correct headers...   the generic/386 thing threw me off.
sudo apt-get install linux-headers-2.6.20-15-386

output of    uname -r
2.6.20-15-386

Then use this for the build/kernel source directory:
/lib/modules/2.6.20-15-386/build

like I said I was close...   but just needed a little more.
This [pos]("http://ubuntuforums.org/showthread.php?t=423926&page=2&highlight=vpnclient+feisty")t helped me out
[http://ubuntuforums.org/showthread.php?t=423926&page=2&highlight=vpnclient+feisty]("http://ubuntuforums.org/showthread.php?t=423926&page=2&highlight=vpnclient+feisty")

---

