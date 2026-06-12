---
title: "No luck with VPN so far?"
date: 2008-03-14
forum: Networking &amp; Wireless
---

### Post by larsdk on 2008-03-14
The only thing I use my dualboot for is to use a VPN connection and to be honest, it is pretty annoying having to reboot and change to windows just to get something as "basic" as that to work, so now I have settled my mind that I want to fix it once and for all.

I have installed the gnome networkmanager and tried using the guide provided there (and by using the same info that I would use to set it up i Windows).

Would be so happy if someone could figure out how to successfully deal with this :)

Lars

---

### Post by jeffhollon on 2008-03-14
this should be fairly easy.  All you should need to do is to install Kvpnc from Synaptic.  Once you do this, it will appear in Applications --> Internet.  Just start the program and it can be setup just like Cisco VPN or most any client.  As long as you know your group password, you should be ok.  If using a Cisco VPN concentrator as your gateway to your remote network, and you have the profile, Kvpnc can use that profile to make it work with ubuntu.  This should be a lot more painless than you think or at least than it appears to be.  Good Luck and let me know how it goes, i ran into the same issues when i first started, but it is getting better everyday.

Jeff

---

### Post by larsdk on 2008-03-14
Hi Jeff,

Thanks for you quck reply - Kvpnc seems to be KDE based - is there a Gnome version as well?

Lars

edit: Maybe I should mention that the VPN is a pptp. (MS)

---

### Post by gardara on 2008-03-14
> **larsdk said:**
> Hi Jeff,

Thanks for you quck reply - Kvpnc seems to be KDE based - is there a Gnome version as well?

Lars

edit: Maybe I should mention that the VPN is a pptp. (MS)

most kde (or maby all) applications work as well on gnome :)

---

### Post by larsdk on 2008-03-14
> **gardara said:**
> most kde (or maby all) applications work as well on gnome :)

Thats true, last time i tried a KDE app. just required me to install a lot of extra stuff, which I would rather not do, if it weren't necessary :)

---

### Post by jeffhollon on 2008-03-14
i use gnome with no KDE installed and Kvpnc installed with only a couple of dependencies if i remember correctly.  It will not foul up your system, give it a go

it will handle pptp very easily.  I have been running it for a couple of months with no ill effects

---

### Post by larsdk on 2008-03-14
it's not that i don't want to give it a shot - I definitely will if everything fails, I just feel like the initial solution based on gnome-network-pptp somehow **should** work. I have it configured with all the right information, but **nothing** happens when I connect and wype in my username and password.

---

### Post by tact on 2008-03-14
> **larsdk said:**
> The only thing I use my dualboot for is to use a VPN connection and to be honest, it is pretty annoying having to reboot and change to windows just to get something as "basic" as that to work, so now I have settled my mind that I want to fix it once and for all.

I have installed the gnome networkmanager and tried using the guide provided there (and by using the same info that I would use to set it up i Windows).

Would be so happy if someone could figure out how to successfully deal with this :)

Lars

First of all - nore info needed.   Are you wanting to set up a VPN host?  Or are you simply wanting to  connect to a VPN server?

If the latter - what kind of VPN server are you needing to connect to?  e.g. is it a microsoft VPN server (must use PPTP protocol)?  Is it a cisco VPN server?  etc.etc..

Only with that information can anyone help you.  Forget about installing any KDE or other software yet...

---

### Post by larsdk on 2008-03-14
hi tact,

allright :)

I want to establish a VPN connection to a VPN server, a windowsbased PPTP for the pupose of getting access to some windows shares on that server (in windows I think it's called web folders).

---

### Post by tact on 2008-03-14
If you are needing to connect to a windows VPN server (using pptp) then:
-  install network-manager etc...  (seems u have done this)
- install network-manager-pptp  (you mention gnone-network-pptp...  not right).

Reboot.  

When its all installed correctly... you would see nm-applet in the notification area of the top panel.  Is this present on your system?

When you click on the nm-applet there is a dropdown window showing your available connections and a menu item called "VPN connections".    Is this present on your system?

Click "configure VPN".   When you configure for a microsoft VPN server you MUST check the "Refuse EAP" box on the authentication tab.   All other boxes unchecked.

On the "Compression & Encryption" tab these two boxes should be checked (only!) :
- Require 128 bit MPPE encryption
- Enable stateful MPPE

Thats the only essentials.   On the routing tab you can also set up so that ONLY the traffic you wish to go thru the tunnel will go thru the tunnel.   Thats another lesson for another day.

---

### Post by larsdk on 2008-03-14
and maybe I should also let you know that my IP is static, so I don't get my IP from a DHCP - don't know if that plays any significant role in the VPN...

---

### Post by tact on 2008-03-14
> **larsdk said:**
> and maybe I should also let you know that my IP is static, so I don't get my IP from a DHCP - don't know if that plays any significant role in the VPN...

Nope its not a concern.

---

### Post by larsdk on 2008-03-14
> **tact said:**
> If you are needing to connect to a windows VPN server (using pptp) then:
-  install network-manager etc...  (seems u have done this)
- install network-manager-pptp  (you mention gnone-network-pptp...  not right).

Reboot.  

When its all installed correctly... you would see nm-applet in the notification area of the top panel.  Is this present on your system?

When you click on the nm-applet there is a dropdown window showing your available connections and a menu item called "VPN connections".    Is this present on your system?

Click "configure VPN".   When you configure for a microsoft VPN server you MUST check the "Refuse EAP" box on the authentication tab.   All other boxes unchecked.

On the "Compression & Encryption" tab these two boxes should be checked (only!) :
- Require 128 bit MPPE encryption
- Enable stateful MPPE

Thats the only essentials.   On the routing tab you can also set up so that ONLY the traffic you wish to go thru the tunnel will go thru the tunnel.   Thats another lesson for another day.


I have the nm-applet (I always have had though) and the VPN-addon is present in the menu. I have configured it according to what you have posted. Howabaout "Peer DNS though tunnel" - that one is checked now.

---

### Post by tact on 2008-03-14
> **tact said:**
> Nope its not a concern.

Oops...  gotta take that back.

If you have conifigured your IP address manually for a static IP address that act takes control of that network adapter away from networkmanager.    Your VPN cannot be configured in networkmanager-pptp in this case.

Only devices with "roaming mode" enabled come under the control of networkmanager.

Are you able to enable roaming mode and get your IP address via DHCP?   If a fixed IP address is needed you, AND you have a device that can act as a DHCP server - you could configure for DHCP and have the DHCP server give you a reserved (fixed or static) IP address as needed.

---

### Post by larsdk on 2008-03-14
roaming is not an issue here - my connection only works with the static configuration, no DHCP whatsoever :(

---

### Post by tact on 2008-03-14
> **larsdk said:**
> I have the nm-applet (I always have had though) and the VPN-addon is present in the menu. I have configured it according to what you have posted. Howabaout "Peer DNS though tunnel" - that one is checked now.

Yes leave "Peer DNS through tunnel" checked.

If you do not want ALL your traffic sent down the VPN tunnel (wise) then you also need to set up routing.    Only do this AFTER you manage to get the VPN connection working.  Once all is working then we play with the routing.

---

### Post by tact on 2008-03-14
> **larsdk said:**
> roaming is not an issue here - my connection only works with the static configuration, no DHCP whatsoever :(

Ok then if you have no option but to use a static IP address - you are screwed.  As soon as you take your adapter out of "roaming mode" (which you do when you manually configure static IP address) you remove it from networkmanager's control and so networkmanager-pptp wont work for you.

Sorry.  Cannot help further here.

---

### Post by larsdk on 2008-03-14
but since static IP and the pptp-manager don't collaborate too well, I guess we can forget about this solution?

---

### Post by larsdk on 2008-03-14
does anyone know if the KDE solution would run into the same problem in terms of static IP ?

---

### Post by larsdk on 2008-03-14
Now I have installed KVpnc and used the wizard to enter my details. However it does not work "Remote modem has hung up. Connection was terminated" is the error I get. 

Maybe someone can help to configurate it (since I guess this is the problem)?

---

### Post by The Cog on 2008-03-14
I configured my pptp client using these by hand instructions. I have a static IP. I did it years ago and just copy the files over ievery time I upgrade, so I have never used the recent GUI tools.
[http://pptpclient.sourceforge.net/howto-debian.phtml#configure_by_hand](http://pptpclient.sourceforge.net/howto-debian.phtml#configure_by_hand)

---

### Post by larsdk on 2008-03-17
the manual solution is not really what I am after (even though it might be the only one) and it will be my very, very last solution. But thanks for letting me know, though :)

---

### Post by GZ Expat on 2008-06-16
After reading this post, I finally figured out what my problem was with the VPN connection.  

Simply put, I saved my satic ip settings in Network Manager as a location.  If I need to use the static ip for p2p sharing, I just click on it and do it.  If I need to connect to VPN, I got back into NM and click on the Roaming option...then I can go back to static Ip when I am finished.

Now, I know this doesn't resolve the issues with people that need the static ip for their vpn connection...but, its resolved my issues.  Woot!

---

### Post by ozelot on 2008-06-16
i had similar problem: on **dhcp mode, i need to set fixed dns servers** because of my *lame fvs124g router*. but **for my vpn connections i need normal roaming mode**.
for this i created **2 scripts** that basically exchange 2 system config files and restart network. i need this because **regular i need NOT to get the dns by router** (hangs over time and is slow in some intervals) and if i want to make vpn connection i DO need to get everything in roaming mode otherwise vpn connection doesnt work.
_here are the scripts..._
**VPN MODE:**
sudo cp /etc/dhcp3/dhclient.confROA /etc/dhcp3/dhclient.conf;
sudo cp /etc/network/interfacesROA /etc/network/interfaces;
sudo /etc/init.d/networking restart;

**STANDARD MODE:**
sudo cp /etc/dhcp3/dhclient.confBU /etc/dhcp3/dhclient.conf;
sudo cp /etc/network/interfacesBU /etc/network/interfaces;
sudo /etc/init.d/networking restart;

**interfacesBU** contains:
auto eth1
iface eth1 inet dhcp
**interfacesROA** contains _NO such entry_

**dhclientROA:**
request subnet-mask, broadcast-address, time-offset, routers, domain-name-servers, domain-name, host-name, ntp-servers;
**dhclientBU:**
prepend domain-name-servers MY.DNS.SERVER.ADRESS;
request subnet-mask, broadcast-address, time-offset, routers, domain-name, host-name, ntp-servers;

so i just have to doubleclick the proper script on my desktop an wait a second to have a smooth sail between the two modes. this is so far the only acceptable way to do exactly what i want **without getting [COLOR="DarkRed"][B]mad**[/COLOR] at "network-admin"\\:D/[/B]
i know my scripting is below basic level, but i hope i helps you anyway

---

