---
title: "[SOLVED] OpenVPN via NetworkManager doesn't work correctly"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by core on 2008-07-13
Hi

I'm no expert in VPN or other Networking issues, i've just be given 2 pairs of files to configure VPN via openvpn.

I've used those in Windows, opening the .ovpn one - let's say work.ovpn - to successfully connect to my working company.

In Hardy i'm having a bit of a trouble with this.
Using the same files, I do "sudo openvpn work.ovpn" and I successfully connect, just like in Windows. Fine.

But I justed wished that network manager applet could handle openvpn connections. And then I find with the right plugin package it does!

So I go installing, but then I notice there's no way to import my work.ovpn file into network manager (is there?), so I start messing with the configs, based on the contents of work.ovpn. But I'm getting no full success til know.

I've failed a couple of times, but I finnaly got it to connect to VPN. Or at least It claims so.. and here is my real problem.

Connecting through the terminal, openvpn connects and I'm allowed to do whatever I used to do: connect via ssh to other machines for instance.

Connecting though network-manager, i can't do any ssh to anywhere.

There are config options on work.ovpn that I can't find where to define them within network-manager.
My work.ovpn:

```

client                                  #sure
dev tun                               #ok, didn't  check "Use TAP device"
proto tcp                             #ok, checked "Use TCP connection"
remote myserver.com 1234  #ok, filled in IP and Port fields
resolv-retry infinite              #I have no idea where to set the following 4 settings...
nobind
persist-key
persist-tun
ca ca.crt                              #ok, I've set these 3 files in main config window
cert user.crt
key user.key
comp-lzo                             #ok, checked "Use LZO compression"
verb 3                                 #nowhere to set this, but I'm sure it isn't needed

```Does anyone have an idea of why I can't get to ssh-connect to a machine at my work, like I do If I start this from the terminal?
Does anyone know how do I import an ovpn file? The "Import Saved Configuration" doesn't seem to work for this.
Note: I connect with ssh to a machine's IP, not using any names, so I think it can't be a DNS problem.

Thanks in advance!

---

### Post by core on 2008-07-13
Forget It, Tried the for the 11th time, just after posting, and It worked this time (I wish someone please give my time back! :-P)

---

### Post by sokool on 2008-10-09
Can you explain what exactly did you do? beacouse i have the same problem like you, and my config file almost looks like yours, but network manager openvpn still dosn't work.

---

