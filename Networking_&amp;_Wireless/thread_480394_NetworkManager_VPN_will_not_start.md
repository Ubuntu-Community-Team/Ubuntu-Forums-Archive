---
title: "NetworkManager VPN will not start"
date: 2007-06-21
forum: Networking &amp; Wireless
---

### Post by klange on 2007-06-21
I just installed the VPN plugin for NetworkManager (PPTP), but I can't seem to get it to start. NetworkManager itself runs fine, but the VPN options are not there. I was attempting to follow [this](http://ubuntuforums.org/showthread.php?t=91249&highlight=vpn+pptp) tutorial, but was unable to complete the second step because, even though apt-get installed the plugin, it won't start.
I'm using Feisty with the newest kernel, and right now I am on my root account to see if it would help.
The VPN I'm trying to connect to is a PPTP VPN running Windows Server 2003.

---

### Post by tact on 2007-06-21
have a look in your synaptic package manager and be sure that the package "network-manager-pptp" was properly installed.

or in terminal just try to install it again
sudo apt-get install network-manager-pptp

if its already installed then it will tell you it had nothing to do.

If its installed and you restarted networkmanager - you should see the menu options for configurig a VPN

---

### Post by klange on 2007-06-21
I have made sure that it was installed, even tried reinstalling it. When right clicking the notification icon, I get "[check] Enable Networking", "[disabled] Connection Information", "About". When I left click, I get "Manual Configuration"

[http://76.189.178.118/networkmanager.png](http://76.189.178.118/networkmanager.png)

---

### Post by tact on 2007-06-21
I see the "Connection information" option is greyed out.  Assume you are not connected to the net via networkmanager or that PC?   If not connected then no option for VPN.  

You need to get connected first...

---

### Post by klange on 2007-06-21
I am connected, using a manual configuration on my wireless card with NetworkManager.
I have no clue as to why it is greyed out.

---

### Post by tact on 2007-06-21
What are the contents of your /etc/network/interfaces file?

Should look like this...

```
auto lo
iface lo inet loopback

```


It there is more stuff in it than above - then comment out everything else like this.

```
auto lo
iface lo inet loopback

#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

```

The reason being - if the ethernet devices are listed in this file they are not controlled by networkmanager.
When you remove all reference to your ethernet devices from theinterfaces file - then networkmanager can manage them.

---

