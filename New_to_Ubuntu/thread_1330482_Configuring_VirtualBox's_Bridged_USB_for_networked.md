---
title: "Configuring VirtualBox's Bridged USB for networked VMs"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by andyzammy on 2009-11-18
Hi, i was wondering if somebody could tell me how to configure VB network settings so that my Fedora Core 5 guest install sees the eth0 as active and in use.

I tried to do it myself and i *think* i managed it (fedora's network settings saw eth0 as "Active") but when my laptop crashed, the host ubuntu's eth0 was "unmanaged", so i had to change /etc/network/interfaces file to it's original state. Whenever i have since tried doing this, it hasn't worked.

If this helps give people a better picture of what i'm doing, i'm trying to [worst case] install oscar (the cluster manager s/w) in order to gain the experience of installing it (a requirement of a uni module) [best case] get a two node VM cluster up and running inside virtualbox.

thanks for your time,
zammy

---

### Post by spikyjt on 2009-11-18
Are you using the OSE version of VirtualBox? If you are using it for academic purposes, you can get the full version free, by adding Sun's own repo. There are instructions at virtualbox.org. The bridged networking works out of the box on the full version.

---

### Post by andyzammy on 2009-11-19
no i'm using the closed source (usb supported) version. i'd rather stick to this one as i do use usb a lot with my VM's.

---

### Post by andyzammy on 2009-11-23
bump. networking vm's not possible then?

---

