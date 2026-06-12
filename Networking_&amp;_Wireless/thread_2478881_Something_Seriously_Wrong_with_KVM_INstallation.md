---
title: "Something Seriously Wrong with KVM INstallation"
date: 2022-09-07
forum: Networking &amp; Wireless
---

### Post by Quarkrad on 2022-09-07
I use virt manager gui to manage a number of ubuntu machines on my Desktop - for some reason I have no internet connection from any kvm machine.  Both ubuntu kvm machines use the default NAT i/f to comm with the (ubuntu 22.04) host.  I can ping the kvm machines from my host and from either kvm to the host.  I decided to install another new kvm machine and compare the configurations but something very odd is (suddenly) happening.  It is very slow to respond.  E.g. I get the install Desktop but no 'do you want to try' vs 'install' options - these do appear after the cursor circling for about 20 mins.  At this point I thought great - but for each change I make during the install (changing language, region,etc) I have to wait 15 to 20mins before any response.  It's like I've gone from something like 100 mb/s fibre internet speed to a 1970s dial-up modem.
There is plenty of space in the pool I'm using for the image - been looking all afternoon for 'a pointer' but I'm stuck at the moment.
note. I have two kvm machines and over the previous months I installed/deleted a number of others so although far from an expert I am reasonably comfortable using virt manager to create images/machines.

---

### Post by TheFu on 2022-09-07
A network misconfiguration could easily manifest with the symptoms described.  I've never used the libvirt network stuff, always prefer to create manual bridges myself, then connect the VMs to which ever bridge is needed.

If you show the interfaces and routing on the host, something might jump out.  I don't have 22.04; too new for me.

---

