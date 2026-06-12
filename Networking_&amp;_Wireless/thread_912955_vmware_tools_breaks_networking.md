---
title: "vmware tools breaks networking"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by simmonsm on 2008-09-07
I've just upgraded my main ubuntu 7.10 (2.6.22.15) box with the latest 1.0.7 vmware server. I already have an existing virtual machine of Ubuntu 8.0.4 (2.7.24.19-server) which works just fine under this environment but of course now when I start the vm I'm told the version of vmware tools is out of date so I start the usual vmware tools upgrade (vmware tools 1.0.7 build 108231) from the tar.gz archive it presents on the virtual cdrom. After installing vmware tools my ethernet no longer works.

lspci still shows the device but ifconfig only shows the loopback interface now. I also found that creating a new 8.0.4 vm now also has the same missing interface problem. Has anyone else used the latest vmware server for Ubuntu ? Any ideas welcomed ?

---

### Post by Mighty_Joe on 2008-09-08
I have the same problem with ESX server 3.5 and a fresh Ubuntu VM.
The live cd running in a VM has networking. Fresh install has networking.  Install VMWare tools, no networking.  ifconfig only shows lo.  
I'm going to follow [this course]("http://peterc.org/2008/62-how-to-install-vmware-tools-on-ubuntu-hardy-804-under-vmware-fusion.html") and see how it goes.

---

### Post by simmonsm on 2008-09-08
> **Mighty_Joe said:**
> I have the same problem with ESX server 3.5 and a fresh Ubuntu VM.
The live cd running in a VM has networking. Fresh install has networking.  Install VMWare tools, no networking.  ifconfig only shows lo.  
I'm going to follow [this course]("http://peterc.org/2008/62-how-to-install-vmware-tools-on-ubuntu-hardy-804-under-vmware-fusion.html") and see how it goes.

Joe, your link gives the information needed to fix the problem for my environment. I just followed 
"Steps To Getting VMware Tools installed on Ubuntu Hardy under VMware Fusion:" 
on that page and now my Ubuntu 8.0.4 32-bit VM has networking again. Many thanks for the link.

- Mark Simmons.

---

### Post by Mighty_Joe on 2008-09-08
The instructions in the above article worked for me.  I have a VM with working networking.  The only bump was running configure for the Open Virtual Machine Tools.  configure looks for two packages, liburiparser and icu, which are either the wrong version or not in the right place.  I told configure not to use those packages and the tools compiled.

---

