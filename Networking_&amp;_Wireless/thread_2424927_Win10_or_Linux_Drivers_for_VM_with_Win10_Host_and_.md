---
title: "Win10 or Linux Drivers for VM with Win10 Host and Unbuntu Guest"
date: 2019-08-17
forum: Networking &amp; Wireless
---

### Post by merlot160 on 2019-08-17
I have installed a USB WiFi adaptor which finds my wireless network but cannot connect. After trying to connect for a short time I get "Activation of network connection failed". I am using Windows 10 Host and Ubuntu 18.04 guest. Various drivers are available on the manufacturers website, including Linux with full installation instructions, but as it is a VM, I have installed the Windows 10 one. Is this correct?

Are there any other tweaks or settings I need to do to get a connection? It was connecting yesterday, but after rebooting etc I cannot get it to connect again although it always finds my wireless network including some of the neighbours. I have the network adaptors disabled in the VBox settings as I do not want it to connect by cable and it was connecting yesterday with this setup.

Any advice would be appreciated.

---

### Post by SeijiSensei on 2019-08-17
You should make the connection on the host system. The VM guest will use that. However you need to have at least one network connection enabled in the guest. Usually the default is "NAT," where the VM hides behind the host.  Essentially the host acts the same way any standard router does.

---

### Post by cruzer001 on 2019-08-17
NAT is the recommended choice, vBox needs the extension pack to use external usb ports, you have it installed?

---

### Post by merlot160 on 2019-08-17
> **cruzer001 said:**
> NAT is the recommended choice, vBox needs the extension pack to use external usb ports, you have it installed? Yes I have the VBox extension pack installed.

I want to be able to leave the host connected by Ethernet and use the wireless connection for the guest. Any ideas on how I can do that?

---

### Post by cruzer001 on 2019-08-17
Nope, never tried that.  For the guest to see it, the host must first recognize it.  That would be my first thought, but I have nothing to go on.  Sorry

---

### Post by cruzer001 on 2019-08-17
I did get several hits at the vBox forum.  Here's one

[https://forums.virtualbox.org/viewtopic.php?f=6&t=83077](https://forums.virtualbox.org/viewtopic.php?f=6&t=83077)

---

### Post by TheFu on 2019-08-17
Hardware connected to the VM host is managed by the host, Win10.

The guest only sees virtual hardware unless you go out of your way to allow exclusive access to the hardware for the guest only.  While this is possible and relatively easy with USB devices, for networking, it is usually best unless you are an expert to let the host deal with the network hardware and provide the guest with a virtual "standard" adaptor.  For Linux, the virtio drivers are preferred for network and storage devices, since they have lower overhead and fantastic performance.  I don't know if vbox supports virtio drivers.  Lacking that, present an Intel PRO/1000 network adaptor to the guest.  It doesn't matter what your real network hardware is, the hypervisor handles that, assuming the "cable connect" check box is enabled for the correct NIC in the VM setting.

There is lots of advice for specific VM configurations and better performance.  The virtualbox manual is comprehensive and actually pretty clear. [https://www.virtualbox.org/manual/](https://www.virtualbox.org/manual/)  The Networking chapter is well worth reviewing, since there are a few caveats for some configurations - like the host-only setup, which you might want to use if you don't want the VM on your LAN or internet.

UPDATE - I see you want wifi for the guest only.  That's the USB passthru option you'll need to setup inside the running Guest VM - top center of the screen should show a menu if you mouse there. The host OS cannot be using it or it will not work.

---

### Post by merlot160 on 2019-08-17
I have the USB passthru setup and have created a filter for my USB adaptor. As  noted the guest is finding and showing the available WiFi networks and asking for passwords but just cannot connect?

---

### Post by TheFu on 2019-08-17
> **merlot160 said:**
> I have the USB passthru setup and have created a filter for my USB adaptor. As  noted the guest is finding and showing the available WiFi networks and asking for passwords but just cannot connect?

It isn't clear why you want wifi for the guest.  If it is for some security testing (deep wifi attacks as a security researcher), then that makes sense, but if you just want to have both the hostOS and the Guest OSes on the same LAN, then the "bridged" networking option inside each VM with the wired ethernet connection is much better. No need for wifi at all.  In bridged mode, all members of the bridge are on the same subnet, usually getting network settings from the LAN DHCP server automatically.

R U a security researcher an **need** Linux in a guest VM to have direct access to the wifi?  Can't say that I've heard of other uses outside that one, but there certainly can be.  I've not done it, but my security professional buddies do the passthru thing all the time for the WPA2 hacking.

---

### Post by merlot160 on 2019-08-18
The guest connection cannot go through the  router as it will then give the same IP address as the host (and the reason this is not desirable is unimportant). It needs to connect to a mobile WiFi 4G router. The VM will replace a separate laptop with this connection.

---

### Post by TheFu on 2019-08-18
> **merlot160 said:**
> The guest connection cannot go through the  router as it will then give the same IP address as the host (and the reason this is not desirable is unimportant). It needs to connect to a mobile WiFi 4G router. The VM will replace a separate laptop with this connection.

Yep. Good reason.  
You've probably already seen these links:
[https://forums.virtualbox.org/viewtopic.php?f=6&t=78426](https://forums.virtualbox.org/viewtopic.php?f=6&t=78426) seems to say that different devices aren't successful at being passed through.
[https://unix.stackexchange.com/questions/528342/trying-to-make-my-usb-wifi-adapter-work-on-virtualbox-kali-guest-windows-host](https://unix.stackexchange.com/questions/528342/trying-to-make-my-usb-wifi-adapter-work-on-virtualbox-kali-guest-windows-host)

I know people who do it, but they are very specific about the wifi USB device, since they need specific capabilities for their research.

---

### Post by SeijiSensei on 2019-08-19
> **merlot160 said:**
> The guest connection cannot go through the  router as it will then give the same IP address as the host (and the reason this is not desirable is unimportant). It needs to connect to a mobile WiFi 4G router. The VM will replace a separate laptop with this connection.

In VirtualBox, if I specify "bridged networking" in the Network configuration rather than NAT, my VM gets an entirely different IP address when booted.  Right now my Linux host has 192.168.100.58, and my Windows VM has 192.168.100.61. That's because the VM has an entirely different MAC address from the host, and thus my router's DHCP server gives it a different address.  Because of that, I see no reason the same behavior would not apply to a Windows host and a Linux guest.

In "bridged" mode, the VM sits directly on the network the same way the host does.

---

### Post by TheFu on 2019-08-19
Yep.  The OP is trying to have Windows use 1 WAN connection and the VM guest running Ubuntu use a different WAN connection.
At least that is what I understand.

---

### Post by SeijiSensei on 2019-08-19
Yes, I realize that. But he seemed to be working under the misconception that the host and guest must have the same IP if they use the same interface.  

> The guest connection cannot go through the router as it will then give the same IP address as the host

That's not true for VirtualBox with bridged networking, and I suspect it's not true for other VM software either.

---

