---
title: "Autostart of openvpn"
date: 2015-09-28
forum: Networking &amp; Wireless
---

### Post by Robbyx on 2015-09-28
I would like to have the vpn connection on when I start Ubunt14.04. I followed the following advice but it does nothing on startup.

[http://askubuntu.com/questions/480859/openvpn-on-ubuntu-14-04-auto-connect-on-startup](http://askubuntu.com/questions/480859/openvpn-on-ubuntu-14-04-auto-connect-on-startup)

I checked the names of my connections:

robins@robins-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr d0:50:99:19:55:52  
lo        Link encap:Local Loopback  
tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
 


I added the following shell script into /etc/NetworkManager/dispatcher.d

#/bin/bash
REQUIRED_CONNECTION1_NAME="eth0"
VPN_CONNECTION_NAME="TUN0"

activ_con=$(nmcli con status | grep "${REQUIRED_CONNECTION1_NAME}")
activ_vpn=$(nmcli con status | grep "${VPN_CONNECTION_NAME}")
if [ "${activ_con}" -a ! "${activ_vpn}" ];
then
    nmcli con up id "${VPN_CONNECTION_NAME}"
fi

I then made the changes per the above url to 

/etc/NetworkManager/system-connections/vpn_ac 

 password-flags=0

and adding

[vpn-secrets]
123xxx=myPassword

and it does not work. I think it may be failing because I have not followed the opening comment in the url

> 
There are a lot of topics concerning this. OpenVPN Auto Connection by putting the conf file to /etc/openvpn just doesnt work. When using the Authentification type "password" an easy way to make it work is:

The only file in /etc/openvpn is: update-resolv-conf


Is the article  saying I should add the conf file to /etc/openpn as well as following the rest of its advice? If so where do I find the conf file?

---

### Post by Robbyx on 2015-09-29
I may have made my question over complex. I was really asking how to auto  switch on openvpn when the computer is started.

I am hoping someone can help me out on the configuration.

---

### Post by Janiporo on 2015-11-25
Exactly same problem here :roll:

---

### Post by The Cog on 2015-11-25
Put the configuration file in /etc/openvpn, e.g. /etc/openvpn/XYZ.conf
That should do the trick, but you can select which VPNs are started automatically by editing /etc/default/openvpn.

---

### Post by Janiporo on 2015-11-25
What is the name of the configuration file, and where do I get it from? do you mean something like renaming my *.ovpn to *.conf and copying to /etc/openvpn ?

I am still struggling to make the password automatic, If I understand correctly, I should put 

[vpn-secrets]
myusername=myPassword

to /etc/NetworkManager/system-connections/vpn_ac

And also add this to that file:
password-flags=0

I do not have that vpn_ac file, do I create it?

---

### Post by The Cog on 2015-11-25
Ah, I don't know about doing it with Network Manager. Sorry. 
I was thinking of the server side (no network manager, no GUI). Our VPN servers have multiple configuration files in /etc/openvpn, the contents are the same as you would put in a .ovpn file if you were using windows.

You could certainly try copying your *.ovpn file to /etc/openvpn/*.conf and see if it works when the PC boots (or use "service openvpn start XYZ") but I don't know how it would interact with Network Manager, or how you would supply the password. At worst you would have to delete the .conf file again and look for a different way to do things.

---

### Post by Janiporo on 2015-11-25
I solved it!  \\:D/

I am going to use XXXX (and blurr) for every name that most likely will not be the same with your setup

Firstly configure at least one VPN connection, that you will use.

Then go with your nautilus with admin rights "sudo nautilus" and choose your default connection, the one you just made, It can be found here: /etc/NetworkManager/system-connections/XXXX

 Open that with double click

Then set the password-flags to 0

then add:

[vpn-secrets]
password=XXXX

and put your password to where the XXXX is.

 At that config file you should see your UUID, we will need that later, copy it.

 It should now look something like this:
[IMG]http://kuvapilvi.fi/k/yvxZ.jpg[/IMG]

Save and add the following to the start-up applications of your computer:

nmcli con up uuid XXXX-XXXX-XXXX-XXXX-XXXX

 uuid is of course the one you copied from the settings file.

Reboot, the connection should come up automatically.

You're welcome ;)

---

### Post by The Cog on 2015-11-25
Nice one!
Glad you sorted it.
You can mark the thread solved using the Thread Tools pull-down menu near the top of the page.

---

### Post by Janiporo on 2015-11-25
I think I can not, since I am not the original poster?

---

### Post by Euanbuntu on 2016-11-23
I run an Ovpn connection to a private server (to clarify I don't run the server, just my connection to it), and I have been looking around for a solution to have the vpn start automatically on boot.

I don't mean to sound ungrateful, but the solution listed here is very messy - not in the way it is executed (I wouldn't know what a messily executed solution was if you put it next to the best executed one in the world), but, from the point of view of someone who is not technically that savvy it is very confusing to have all the solution split into two parts and not have it marked out in very simple monkey-can-do steps.

To clarify - I am exceedingly grateful that someone has taken the time and effort to figure this out, and more so that they have decided to share it here. But could it be put into 1,2,3,4... steps?

E.g. just saying 'put it where your password is' is confusing, how does one 'add a script to something', etc., etc.

I wonder if this, or any other solution has been outlined in more simplified terms anywhere?

---

### Post by howefield on 2016-11-23
Thread closed.

---

