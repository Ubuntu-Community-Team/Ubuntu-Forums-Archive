---
title: "Adding VPN (OpenVPN) Ubuntu 14.04 (Trusty)"
date: 2014-04-19
forum: Networking &amp; Wireless
---

### Post by arm-c on 2014-04-19
All,

I used to add all of my VPN connections using the network manager AppIndicator.  When I do this with 14.04, it crashes after I select the saved config file and press OK.  No message... just crash of the process to add a VPN without results being generated.

Does anyone know how to fix this?  I really liked having my VPNs in the NetworkMan AppIndicator.

(Note, I can start a vpn connect from the command line using the HMA script... but not my preferred method to do so.).

Appreciate any help on getting NetworkManager patched/fixed.

---

### Post by ccrs8 on 2014-04-19
I'm seeing this exact behavior.  In Xubuntu 13.10, I had about 10 OpenVPN connections that I set up through the Network Manager.  None of them work now (but my one OpenConnect Cisco VPN connection still worked).  Anyway, I figured I'd delete the VPN connections and recreate them with the configuration files that my VPN service provides (just like I did in 13.10 to add them in the first place).  Upon selecting the configuration file, the entire process ends in a crash and the Ubuntu problem reporting tool opens up.

Edit: To provide more info, I upgraded from Xubuntu 13.10 to 14.04 as opposed to doing a clean install.

---

### Post by paul124 on 2014-04-19
network-manager-openvpn-gnome

I can confirm that it fails on both an upgrade and fresh install. Also it does not matter if you import the connection or create a new one, both fail. Looks like its a problem with entering the certs. 

PPTP and Cisco seem to work fine.

---

### Post by paul124 on 2014-04-20
I have done some more testing on this. If you upgrade from 13.10 to 14.04 the configurations exist and appear to be available. When you start an OpenVPN connection the gnome interface will show it as ON but you will notice that your network device has disconnected. Its crashed the network stack. You get the "Sorry, Ubuntu 14.04 has experienced an internal error" 

My advice is if you need the gnome openvpn client dont upgrade. 

Will report a bug over in launchpad.

---

### Post by arm-c on 2014-04-20
I did post a bug.  I used during beta period.  Last i checked it was unassigned.

---

### Post by ccrs8 on 2014-04-20
I did a clean install of Xubuntu 14.04 this morning and can confirm that it does not work either on clean install or upgrade from 13.10.  Also can confirm that maually entering an OpenVPN connection fails the same way.

---

### Post by skiesare2 on 2014-04-21
This has been reported as a bug at [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1295439](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1295439) 
It was first reported a month ago but is marked as high importance. 
It is still possible to connect to a VPN via the command line, but that makes it awkward to set up an automatic connection.
No-one has mentioned if it affects both 64 and 32 bit installations. I'm on 64bit as was the originator of the bug report.

---

### Post by ccrs8 on 2014-04-21
Both my machines are 64-bit...sorry.

---

### Post by sammiev on 2014-04-21
I have openvpn running with kubuntu 14.04, xubuntu 14.04 and ubuntugnome 14.04

---

### Post by ccrs8 on 2014-04-22
> **sammiev said:**
> I have openvpn running with kubuntu 14.04, xubuntu 14.04 and ubuntugnome 14.04

But are you able to add a new OpenVPN connection (either manually or by importing a config file)?  And if so, 32 or 64 bit machine?

---

### Post by sammiev on 2014-04-22
> **ccrs8 said:**
> But are you able to add a new OpenVPN connection (either manually or by importing a config file)?  And if so, 32 or 64 bit machine?

I was able to add a new connection tonight manually using Xubuntu 64 bit. I included a new picture with Seattle SSL which was not in my last config.

---

### Post by arm-c on 2014-04-23
What method did you use to add a connection manually?  If you know a way to do that, it would be helpful.  I'd need to be able to use a saved .ovpn file as well as possibly designate the required certs.

---

### Post by sammiev on 2014-04-23
> **arm-c said:**
> What method did you use to add a connection manually?  If you know a way to do that, it would be helpful.  I'd need to be able to use a saved .ovpn file as well as possibly designate the required certs.

I have all my certs and keys in one directory. I just point my OpenVPN to where they are store manually and save the path. No different than any other version of Ubuntu I have used over the last few years.

---

### Post by arm-c on 2014-04-24
The issue with ADDING a VPN from a saved .ovpn file still fails.

It is possible to ADD one manually.
1. Select NM App Indicator, --> VPN --> Configure VPN --> Add --> OpenVPN
2. Manually Name your Connection and enter the IP Address for your server
3. Select the type of authrntication:  For me it is Password + Certificates
4. Enter your User Name and Password
5. Select your certificates and keys for the next three boxes.
6. Select Advanced from bottom
7. Enter the PORT (in the .ovpn file, usually at the bottom after the IP address in the "XX" position:
remote ###.###.##.## XX
8. If your VPN is TCP, then check box for "Use a TCP Connection"
9. Select OK and then Save.

At this point, the VPN connection should be listed in the NM AppIndicator as an option.  Select and test your connection.  I was able to add a TCP and a UDP type of connection, but it took a lot more to do than it would have if the import .ovpn saved file worked.

Lets hope they fix this soon so I can easily add other connection... but at least this is a work around that should help people frustrated like I was.

---

### Post by skiesare2 on 2014-04-25
For those of us using AirVPN, the method of manually adding the VPN connection still doesn't work. That is to say that you can add the connection details but not get a connection. There has been discussion of this bug in AirVPN's forums, where users are recommended to connect via the command line, and where the admins have said this;

"[COLOR=#282828][FONT=Verdana]What we detect, and this not good at all for security, is that network-manager runs OpenVPN so that no server certificate verification is required from your OpenVPN. We underline that this is bad for security reasons and we are investigating. This is another good reason ((the other reason is that network-manager does not pass explicit-exit-notify to OpenVPN) to run OpenVPN directly, as long as we do not release the client for Linux."

This may also go some way to explain why, having initiated a connection to the VPN via N-M, when my internet connection drops off, my VPN connection is also lost. But since connecting to the VPN via the command line I have not noticed the VPN connection being lost and my line goes down a lot.


[/FONT][/COLOR]

---

### Post by sheershoff on 2014-05-12
Sometimes the following helps to fix the VPN Connections in the tray:

1. edit the connection (i change the name of connection)
2. relogin
3. try in a minute after logging in

---

### Post by wil on 2014-05-12
My VPN is working again, seem like the bugs were fixed.

Previously I had to use the terminal

$ sudo vpnc myVPNConfFile
$ sudo vpnc-disconnect

---

### Post by jcm69 on 2014-05-16
Hi !
here is the solution I found (using the menus don't work for me) :
install openVPN : sudo apt-get install openvpn
copy your .conf, .crt and .key files in /etc/openvpn (you should see update-resolv-conf there). 
I suggest to give them the rights : -rw------- and make them belong too root.
To start your VPN connection, type sudo /etc/init.d/openvpn start
To stop ... tada! sudo /etc/init.d/openvpn stop
Too bad for the menus but I think I will use this solution for a long time. Tired of trying.
Have care  and take fun
jc

---

### Post by pitchizig on 2014-05-16
Hi!
It seems, since last updates, that Network-Manager accepts to register openVPN configurations. You have to do it manually (no import) as described by arm-c #14.
1. Select NM App Indicator, --> VPN --> Configure VPN --> Add --> OpenVPN
2. Manually name your Connection and enter the IP Address for your server (to be found in a .ovpn file - in the folder supplied by your VPN service provider - on a line which looks like: **remote cl1-ovpn.purevpn.net 53**, where **cl1-ovpn.purevpn.net** is a server IP adress - to adapt of course, cl1 beeing in Chili) and **53** is the suggested port.
3. Select the type of authentification: could be **Password** or** Password+Certificates** depending on your VPN service provider.
4. Enter the user name and password given by your service provider. Find your certificate **ca.crt** and possibly keys in the VPN folder.
5. Select Advanced from bottom, enter the port (53 in the example), compression LZO (usually, it is shown in your .ovpn file under **comp**), select TCP if you are using it.
6. Open the security tab. Your .ovpn file shows the cipher to be selected, usually AES-256CBC.
7. If your VPN provider supplied you with a **Wdc.key**, it is to be entered in the TLS tab (file to be found in your VPN folder). You have to put a **1** on the last line.

Now you can click OK and save.
Remember, you'll find a lot of informations in the .opvn files. They are a bit cryptic but it's made for the automatic installation Network-Manager seems unable to do.
Good luck!

---

### Post by ccrs8 on 2014-05-28
Ubuntu 14.04 just got an update to Network Manager that fixes this issue.  OpenVPN config files are now importable again.

---

### Post by Optimized_Coder on 2014-06-03
> **ccrs8 said:**
> Ubuntu 14.04 just got an update to Network Manager that fixes this issue.  OpenVPN config files are now importable again.

I don't see any recent changes, but yes 14.04 has that option.
Instructions here : [http://askubuntu.com/questions/187511/how-can-i-use-a-ovpn-file-with-network-manager](http://askubuntu.com/questions/187511/how-can-i-use-a-ovpn-file-with-network-manager)

---

### Post by wpwend42 on 2014-06-04
When I try to add my .key file, Ubuntu does not see it. It is not a hidden file. I have never had this problem before.

---

### Post by charlieprime on 2014-10-06
> **Optimized_Coder said:**
> I don't see any recent changes, but yes 14.04 has that option.
Instructions here : [http://askubuntu.com/questions/187511/how-can-i-use-a-ovpn-file-with-network-manager](http://askubuntu.com/questions/187511/how-can-i-use-a-ovpn-file-with-network-manager)

Neither do I see any change to network manager.

Here is an .opvn file I tried to use:

[http://www.vpngate.net/common/openvpn_download.aspx?sid=1412593096570&udp=1&host=61.194.150.7&port=1194&hid=16679&/vpngate_61.194.150.7_udp_1194.ovpn](http://www.vpngate.net/common/openvpn_download.aspx?sid=1412593096570&udp=1&host=61.194.150.7&port=1194&hid=16679&/vpngate_61.194.150.7_udp_1194.ovpn)

network-manager will not pull the key out of it, or allow me to save the configuration if I rename the file .cer or .conf

---

