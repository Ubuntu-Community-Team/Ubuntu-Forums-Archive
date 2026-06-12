---
title: "&quot;Bad Archive Mirror&quot; Error during kickstart install"
date: 2017-11-25
forum: Networking &amp; Wireless
---

### Post by supertight on 2017-11-25
here is a copy of the ks.cfg file 
```
#platform=AMD64 or Intel EM64T

#System language
lang en_US
#Language modules to install
langsupport en_US
#System keyboard
keyboard us
#System mouse
mouse
#System timezone
timezone America/Los_Angeles
#Root password
rootpw --disabled
#Initial user
user joe --fullname "joe" --iscrypted --password $1$ASCq9cy8$wdwDcOuNM0H.Lnt.CfXfJ0
#Reboot after installation
reboot
#Use text mode install
text
#Install OS instead of upgrade
install
#Use Web installation
url --url http://archive.ubuntu.com/ubuntu/dist/artful/main/installer-amd64/current/images/netboot
#System bootloader configuration
bootloader --location=mbr
#Clear the Master Boot Record
zerombr yes
#Partition clearing information
clearpart --all --initlabel
#Disk partitioning information
part swap --size 512
part / --fstype ext4 --size 11000
part /boot --fstype ext4 --size 500
part /var --fstype ext4 --size 5000
part /tmp --fstype ext4 --size 5000
part /opt --fstype ext4 --size 1 --grow
#System authorization infomation
auth  --useshadow  --enablemd5
#Network information
network --bootproto=dhcp --device=eth0
#Firewall configuration
firewall --disabled --ssh
#X Window System configuration information
xconfig --depth=32 --resolution=1152x864 --defaultdesktop=GNOME --startxonboot
#Run the Setup Agent on first boot
firstboot --enable
#Package install information
%packages
@ kubuntu-desktop

```

I'm not sure the web install url is correct. Other than that, I'm lost.
Thank you for reading.

---

