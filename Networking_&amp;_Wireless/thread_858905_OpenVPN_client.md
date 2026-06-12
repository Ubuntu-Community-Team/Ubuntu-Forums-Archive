---
title: "OpenVPN client"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by finlost on 2008-07-14
I am hoping I can get OpenVPN configured under Ubuntu 8.04 for work.  I currently have it running on Vista, so OpenVPN does work on my employers network.  

Via Synaptic, I installed *openvpn* and *openvpn-blacklist*.  

After installing, I haven't a clue what to do.  

I need to copy my three certificates from my Vista machine to Ubuntu.  Where do the files need to be copied to?  

How do I even execute/start OpenVPN?

---

### Post by UboneHead on 2008-07-14
What I had to do was install nm-applet, which is not the same as Network Monitor although the icons are exactly the same and they show up in the same area of the panel (taskbar). You will probably need network-manager-openvpn as well.
When you get that stuff installed, you need to configure the vpn. Click on the nm-applet icon, and you should see a VPN Connections item and under that, Configure VPN... (If you don't see that, then you're not clicking the nm-applet icon but some other network related thing that looks the same. Right-click and check About. You may have to manually add it to the panel.)
When you get to the Create VPN Connection - 2 of 2 dialog, you will see where to paste the path to the certificates (so it doesn't really matter where you copy them to).
It's all very intuitive--took me less than a week.

---

### Post by finlost on 2008-07-15
Thanks for the guidance.  I figured it wasn't too difficult, but I was stuck.  

For the record, I installed the following packages via Synaptic

```
network-manager
network-mangager-openvpn
openvpn
openvpn-blacklist
```

I then had to add "VPN Connection Manager (OpenVPN) to the Ubuntu menu.  I did this via Systems:Preferences:Main Menu.

I then clicked on Applications:Internet:VPN Connection Manager (OpenVPN).  Next I had to click on the "Wired Network Connection" icon in the upper right of the screen.  I selected VPN Connections:Configure VPN.

It then asked for my certificate locations and some other information.  I need to ask the IT Deptartment the "gateway address"

I hope this ends up working as I prefer to use my Ubuntu desktop for work over my Vista laptop.

---

