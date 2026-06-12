---
title: "What is the GUI VPN client on KDE (not KVpnc)?"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by isrd1 on 2008-04-17
Hello,

I recently installed the KDE desktop just to see what it was like, I'm using Gnome.  I liked lots of things about it but decided to return to Gnome.  One of the apps I did like very much was a graphical front end to a VPN client, it was very simple to use, allowed me to send things like Ctrl+Alt+del to a windows client and fast.  Unfortunately I didn't note what it was, looking at the install logs from Aptitude I thought it might be openvnc, but that's not a GUI, then I tried KVpnc but it wasn't that.  KVpnc is must more, and too, complicated.  The Terminal Server Client in Gnome is OK but I can't seem to send windows control alt key combinations to the host.

I don't think its the network-manager-vpnc mentioned on another thread either, simply because the Synaptic Package Manager talks about that as though its primary purpose was to maintain a connection rather than be a GUI.

Any clues greatly appreciated.

Rob

---

### Post by Chudilo on 2008-04-18
I think you are confused between a VPN client and remote desktop GUI.

You can send Cntl-Alt-Del command within the Terminal server clent in gnome

---

### Post by whouseswindowsanyway on 2008-04-18
i think ur confused too -- but maybe instead of using that --- try to apt-get install xtightvncviewer
--
its 60kb.... very small quick install
--then from term -- just type xtightvncviewer... and it will pop up a small window that asks for ip address -- and will ask for pword -- then when logged in you just hit F8 and a little menu bar pops up -- and u can hit CTRL+ALT_DEL

---

### Post by isrd1 on 2008-04-19
> **Chudilo said:**
> I think you are confused between a VPN client and remote desktop GUI.

You can send Cntl-Alt-Del command within the Terminal server clent in gnome

No, I wasn't confused, unfortunately the Remote Desktop GUI, although it appears to connect just shows a black screen and I can't seem to find any way to change that.

If I press Ctrl+Alt+Del in Terminal Server my ubuntu client offers to shut down, not quite the effect I was looking for.  However, the post about the tightvnc viewer needing F8 prompted me to try that inside Terminal Server and I found it too then shows a menu to allow me to send Ctrl+Alt+Del.  Which means I have a solution, though not the one I was after - I'd still like to know the GUI VPN client that comes with KDE.

Thanks, Rob

---

### Post by isrd1 on 2008-04-19
> **whouseswindowsanyway said:**
> i think ur confused too -- but maybe instead of using that --- try to apt-get install xtightvncviewer
--
its 60kb.... very small quick install
--then from term -- just type xtightvncviewer... and it will pop up a small window that asks for ip address -- and will ask for pword -- then when logged in you just hit F8 and a little menu bar pops up -- and u can hit CTRL+ALT_DEL

I installed xtightvncviewer, and although it wasn't what I was looking for it is, nonetheless, perfectly fine.  I would never have guessed the F8 key though, where would I have found that piece of information from?  The F8 key also worked in the Terminal Server Client too, so yours was a doubly useful reply, thank you.

Rob

---

### Post by helmut_hed on 2008-06-01
isrd1, you may be wanting "krdc", which is the VNC client for KDE.  Kvpnc (Kde VPN Client) is a VPN client.

Sometimes people use these terms interchangeably, but "VPN" is a secure network connection (Virtual Private Network), and VNC (Virtual Network Computing) refers to a protocol that allows you to have a remote desktop across a network connection.  They are typically used together, but are different things.  You can use either one separately...

---

