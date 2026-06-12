---
title: "Add a VPN connection is grayed out"
date: 2017-02-04
forum: Networking &amp; Wireless
---

### Post by waltd on 2017-02-04
My OS is Xubuntu 16.10, 64bit.  I'm trying to create an OpenVPN VPN, but the "add a vpn connection" under "vpn connections" is grayed out and will not respond to being clicked on.  I have the vpn config file in a folder, but I can't get the "add a vpn connection" to respond to setting up the vpn.  Why is the "add a vpn connection" grayed out and how can I fix this problem.  Thank you.    
               
I successfully ran these terminal commands to add OpenVPN to the OS:
sudo apt-get install network-manager-openvpn
sudo apt-get install openvpn.

---

### Post by praseodym on 2017-02-04
Try
```

gksudo nm-connection-editor
```

---

### Post by bearlake on 2017-02-04
> **waltd said:**
> My OS is Xubuntu 16.10, 64bit.  I'm trying to create an OpenVPN VPN, but the "add a vpn connection" under "vpn connections" is grayed out and will not respond to being clicked on.  I have the vpn config file in a folder, but I can't get the "add a vpn connection" to respond to setting up the vpn.  Why is the "add a vpn connection" grayed out and how can I fix this problem.  Thank you.    
               
I successfully ran these terminal commands to add OpenVPN to the OS:
sudo apt-get install network-manager-openvpn
sudo apt-get install openvpn.

One more package needed. ;)

```
sudo apt install network-manager-openvpn-gnome
```

---

### Post by waltd on 2017-02-05
The menu option "VPN Connections" -> "Add a VPN connection" is still grayed out and not responding to being clicked on.  Any ideas on what I'm missing?  I typed in these terminal commands and rebooted my laptop.  Thanks. 
[COLOR=#000000][I]sudo apt-get install openvpn
sudo apt-get install network-manager-openvpn[/I][/COLOR]
[COLOR=#000000][I]sudo apt-get install network-manager-openvpn-gnome
reboot[/I][/COLOR]

---

### Post by bearlake on 2017-02-05
Are you clicking on the Name "VPN" or the selections under the title "VPN"?

Under "VPN" I have 3 choices which anyone could be selected.

---

### Post by praseodym on 2017-02-05
Try reinstalling all of them including the NM:
```

sudo apt-get install --reinstall network-manager-gnome network-manager network-manager-openvpn-gnome network-manager-openvpn openvpn
```
Reboot

---

### Post by waltd on 2017-02-14
I see what I was doing wrong.  I was trying to create a new VPN connection under Network Manager -> VPN Connections.  Now I know that I need to create a new VPN connection under network Manager -> Edit Connections.  I've solved the problem.
Thanks for all the help.

---

### Post by bearlake on 2017-02-14
> **waltd said:**
> I see what I was doing wrong.  I was trying to create a new VPN connection under Network Manager -> VPN Connections.  Now I know that I need to create a new VPN connection under network Manager -> Edit Connections.  I've solved the problem.
Thanks for all the help.

+1 Glad you have it working and posted how you did the job.

I'm sure others have done the same and others will do the same. ;)

---

### Post by carinyuso on 2018-01-12
How did you solved the problem?

---

