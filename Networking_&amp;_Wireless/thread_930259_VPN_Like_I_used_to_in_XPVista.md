---
title: "VPN Like I used to in XP/Vista"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by 10gallons on 2008-09-25
Hi,
I'm a week old Ubuntu user so please excuse my ignorance, I'm working hard to change that.

I had Vista on my laptop and it ran terribly. I put Ubuntu 8.04 on, and it is running MUCH better. On my XP and Vista PC's I had a few VPN connections setup using the generic Microsoft VPN client to several client networks.

I need to get these connections happening again but now with Ubuntu.

Here's what I know about the VPN connections I need to get into. I VPN into Cisco routers, provide a username and password and the connection is established. Once I'm authenticated I then used to use Microsofts RDP client to get onto the clients servers and perform administration tasks.

So far I have installed:
network-manager-pptp
openvpn
openvpn-blacklist
pptp-linux
vpnc

I am also using Wicd for my WiFi connection.

I cannot find anywhere to setup my VPN connection? Have I not installed something? Maybe I haven't looked in the right place?

Also, once I get my VPN connection established, what can I use to then gain access to my clients Windows server consoles and log in etc??

I'm not the sharpest knife in the drawer when it comes to Linux, so please include as much detail as possible.

Sorry for the long post and thanks for any help.

---

### Post by willca on 2008-09-26
If you got your vpn working...then to rdp to a windows box...I guess thats what you want...otherwise ignore this..

You can do it with rdesktop or tsclient

sudo apt-get install rdesktop
or
sudo apt-get install tsclient

I use rdesktop but if you prefer gui, then tsclient.

In a terminal session,
rdesktop -u username -p password IPaddress

---

### Post by 10gallons on 2008-09-26
Hi, thanks for the reply. No I haven't got my VPN going, I'm still trying to work out how to setup the connection details.

With openvpn, should I see a GUI interface for it somewhere? If not, where should I go to find what I need and when I'm there, what do I need to do to get it all to work?

All help greatly appreciated.

---

### Post by smautf on 2008-09-26
I'm also a noob, but this looks like what you're looking for:

The Network Manager Applet (nm-applet), which shows up in your notification area on gnome-panel, provides a GUI for setting up PPTP VPN if network-manager-pptp is installed. You should be able to get this GUI with the packages you have. I'm pretty sure you should have nm-applet - otherwise you can install it. Also, [COLOR="Red"]I don't know how this will work alongside wicd.[/COLOR] To start nm-applet:
```
nm-applet
```

I hope this helps!

If you know a bit about networking, you can configure openvpn in a config file or at the command line without the help of a GUI. For instructions enter:
```
man openvpn
```

---

### Post by vanadium on 2008-09-26
For cisco networks, you are still missing network-manager-vpnc.

```

sudo apt-get install network-manager-vpnc

```

You will then be able to create a connection to your cisco network using the network manager icon:

* Clik it, select "VPN connections - Configure VPN"
* "Add" for a new connection
* A "wizard" appears now: "forward", select Compatible Cisco, Forward
* Fill in the gateway and groupname on the "Required" tab.
* "Forward" and "Apply" will create the connection, which you can changed later using the Edit buton in the VPN connections dialog.

The VPN connections you created will appear on top of the menu you get when you select "VPN connections" from the network manager icon. Click the name to activate the vpn connection.

---

### Post by jasoncravens on 2008-10-02
I am also having trouble connecting to a windows network through VPN with hardy heron. I tried the above suggestions and got an error trying to install network manager vpn

jason@jason-desktop:~$ sudo apt-get install network-manager-vpnc
[sudo] password for jason: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
network-manager-vpnc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up secvpn (2.21) ...
Starting Monitor Daemon for Secure Virtual Private Network: cp: cannot stat `/etc/inittab': No such file or directory
invoke-rc.d: initscript secvpnmon, action "start" failed.
dpkg: error processing secvpn (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 secvpn
E: Sub-process /usr/bin/dpkg returned an error code (1)
jason@jason-desktop:~$ 



Any suggestions, this is the only thing keeping me from totally leaving windows behind! :)

---

