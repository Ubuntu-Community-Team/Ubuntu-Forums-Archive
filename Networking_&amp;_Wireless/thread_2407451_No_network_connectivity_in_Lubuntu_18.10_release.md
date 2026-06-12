---
title: "No network connectivity in Lubuntu 18.10 release?"
date: 2018-12-04
forum: Networking &amp; Wireless
---

### Post by chris-db on 2018-12-04
Just booted up Lubuntu 18.10 64-bit and there seems to be a problem with the network manager.
Here is a picture with the image booted in a VMware Workstation VM:
[ATTACH=CONFIG]281880[/ATTACH]
As you can see the network interface is down.
The emulated interface is the well known e1000.
This also happened on a physical host, so is unlikely a driver problem. The physical host had several network adapters and all were down.
I managed to manually bring an interface up on the physical host and it was functional for the respective session, but not in the first try.
Was NM tested before release?

---

### Post by howefield on 2018-12-04
Thread moved to the "*Virtualisation*" forum.

---

### Post by chris-db on 2018-12-04
This is not a virtualization problem. The problem is present on all platforms.
I described how the issue appears in VMware just because it can easily be reproduced by anyone.

---

### Post by QIII on 2018-12-04
Networking in 18.10 works fine for me in a KVM VM, so I don't think it is an indication that something wasn't tested.  Not at home, but I'll try to remember to look at later.

We'll let howefield decide if he wants to move the thread back.

---

### Post by chris-db on 2018-12-04
I don't know if it was clear, but I was referring to [Lubuntu lxqt distro]("http://cdimage.ubuntu.com/lubuntu/releases/18.10/release/lubuntu-18.10-desktop-amd64.iso").

---

### Post by QIII on 2018-12-04
I can spin up a Lubuntu VM and look at that.

---

### Post by QIII on 2018-12-04
I'm typing this from a Lubuntu 18.10 VM through a private NIC connection (I have 14 ports on this machine, so I assign one privately to each VM).

Are you running in bridged mode when you run this from a VM?  What can you tell us about your physical hardware when you are running on bare metal?

---

### Post by chris-db on 2018-12-05
Baremetal:
[root@localhost:~] lspci
...
0000:00:1f.6 Network controller: Intel Corporation Ethernet Connection (2) I219-V [vmnic0]
0000:04:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter
0000:05:00.0 Network controller: Wilocity Ltd. Wil6200 802.11ad Wireless Network Adapter
and a TP-Link UE300.
I remember that all had the correct driver loaded, but all interfaces were down.

VM Workstation:
Just a regular E1000 NIC:
[COLOR=#D4D4D4][FONT=Consolas][COLOR=#569cd6]ethernet0.connectionType[/COLOR] [COLOR=#b5cea8]=[/COLOR] [COLOR=#ce9178]"nat"[/COLOR]
[COLOR=#569cd6]ethernet0.addressType[/COLOR] [COLOR=#b5cea8]=[/COLOR] [COLOR=#ce9178]"generated"[/COLOR]
[COLOR=#569cd6]ethernet0.virtualDev[/COLOR] [COLOR=#b5cea8]=[/COLOR] [COLOR=#ce9178]"e1000"[/COLOR]
[/FONT][/COLOR]

---

### Post by QIII on 2018-12-05
OK.  Let's move this back to Networking & Wireless and concentrate first on the bare metal issue.

For those interested in helping, let's please keep this to a standard install for now and we can deal with the virtualization issues in a different thread.

---

### Post by chris-db on 2018-12-05
Looks like they fixed it. I downloaded the iso again, and network is working.
[http://cdimage.ubuntu.com/lubuntu/releases/18.10/release/lubuntu-18.10-desktop-amd64.iso](http://cdimage.ubuntu.com/lubuntu/releases/18.10/release/lubuntu-18.10-desktop-amd64.iso) now has 601a688695af640e3e75155651167697571eeb8b hash.
The one that I downloaded 3 days ago had 2ff38a8c19579d9d557fbdb68c8981c5a576e772 hash.

---

