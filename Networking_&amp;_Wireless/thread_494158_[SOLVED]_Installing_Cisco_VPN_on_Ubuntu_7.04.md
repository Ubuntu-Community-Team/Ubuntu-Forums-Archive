---
title: "[SOLVED] Installing Cisco VPN on Ubuntu 7.04"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by Jaxilian on 2007-07-06
What is the easiest way to install Cisco VPN?

---

### Post by airflow on 2007-07-06
Hi,

connecting to a Cisco VPN concentrator (or ASA/PIX/IOS) is very easy. I just did it yesterday, and was really surprised about the easy user-experience (as someone, who uses this technology every day for years on Windows).

Don't use the orginal Cisco VPN Client for Windows, but use vpnc. Install it via the package-system of ubuntu and don't forget to install the network-manager plugin for it also. Then you can easily create Profiles via the network-manager and connect and disconnect there.

Best Regards,
airflow

---

### Post by Jaxilian on 2007-07-07
> **airflow said:**
> Hi,

connecting to a Cisco VPN concentrator (or ASA/PIX/IOS) is very easy. I just did it yesterday, and was really surprised about the easy user-experience (as someone, who uses this technology every day for years on Windows).

Don't use the orginal Cisco VPN Client for Windows, but use vpnc. Install it via the package-system of ubuntu and don't forget to install the network-manager plugin for it also. Then you can easily create Profiles via the network-manager and connect and disconnect there.

Best Regards,
airflow

Will Cisco profiles work on it? So I can import the pcf-files from the Windows version of Cisco VPN

---

### Post by LostInTheSnow on 2007-07-08
I'm pretty much in the same boat as you. Only a little worse probably because I don't quite know how to import encoded group passwords...

---

### Post by gabe_rosser on 2007-07-09
This used to work fine for me on 6.10 - you can import .pcf files but you may need to decrypt the group password and re-enter it.  I found an online utitlity to do this - you just copy and paste the encrypted version into the website and it outputs the group password!  Sorry, I can't remember the URL now, but try google!

---

### Post by linuksamiko on 2007-07-12
I installed the vpnc-Plugin a long time ago and I can connect to the cisco concentrater but the internet traffic is not sent through the tunnel and I gues it is a network-manager issu. Do you maybe know how to fix this (it seams to work for you quite well).

---

### Post by sunken on 2007-07-14
Hi dude, just installed vpnc and made a config for it /etc/vpnc/default.conf
Text in *italic* is yours to find out

[LIST=1]
[*]install vpnc with synaptic
[*]open terminal, type **sudo pico /etc/vpnc/default.conf**
An example of default.conf:
[B]IPSec gateway *ip.to.vpn.server*
IPSec ID *VPNservergroupname*
IPSec obfuscated secret *cryptedpasswordfrompcffile*
Xauth interactive[/B]
[*]**ctrl+x**
[*]**y**
[*]**sudo vpnc-connect**
[*]enter your vpn user name, **enter**
[*]enter pin code or what ever kind of system you have, **enter**. Now you're inside vpn tunnel
[*]after you're done, **sudo vpnc-disconnect**
[/LIST]

---

### Post by linuksamiko on 2007-07-15
The problem (at least in my case) is not by connecting to the VPN. The Problem is that no traffic is comming through the tunnel.
It doesn't matter if I connect with the network-manager or over the console. I don't get anything.

---

### Post by sunken on 2007-07-15
> **linuksamiko said:**
> The problem (at least in my case) is not by connecting to the VPN. The Problem is that no traffic is comming through the tunnel.
It doesn't matter if I connect with the network-manager or over the console. I don't get anything.

Ok, perhaps a post for that problem then, please supply the output of ifconfig and the errors you recive

The post I did covered how to if you do not know your group password and only have the pcf file.

---

### Post by PCFascist on 2007-07-16
Thanks sunken and airflow... this got me working.

It seems that once I try to connect to something on the internet... it will disconnect my VPN.

---

### Post by Jaxilian on 2007-07-16
> **sunken said:**
> Hi dude, just installed vpnc and made a config for it /etc/vpnc/default.conf
Text in *italic* is yours to find out

[LIST=1]
[*]install vpnc with synaptic
[*]open terminal, type **sudo pico /etc/vpnc/default.conf**
An example of default.conf:
[B]IPSec gateway *ip.to.vpn.server*
IPSec ID *VPNservergroupname*
IPSec obfuscated secret *cryptedpasswordfrompcffile*
Xauth interactive[/B]
[*]**ctrl+x**
[*]**y**
[*]**sudo vpnc-connect**
[*]enter your vpn user name, **enter**
[*]enter pin code or what ever kind of system you have, **enter**. Now you're inside vpn tunnel
[*]after you're done, **sudo vpnc-disconnect**
[/LIST]

Tjena Sunken
I used KVpnc as GUI for vpnc since the above didn't work for me, but I couldn't make the KVpnc to work either. 
from what I read on other posts, the group password needs to be re-entered and I don't have that.

---

### Post by sunken on 2007-07-16
> **flodis said:**
> Tjena Sunken
I used KVpnc as GUI for vpnc since the above didn't work for me, but I couldn't make the KVpnc to work either. 
from what I read on other posts, the group password needs to be re-entered and I don't have that.

Well, that is strange. Both me and Jacob tried this at our Ubuntu's and we could connect. We try to our common company, not to our common customer ;)

Congrats to new family member

Br
Sunken

---

### Post by Jaxilian on 2007-07-17
> **sunken said:**
> Well, that is strange. Both me and Jacob tried this at our Ubuntu's and we could connect. We try to our common company, not to our common customer ;)

Congrats to new family member

Br
Sunken

thanks!
please show me when you get back from your vacation :)

---

### Post by sunken on 2007-07-17
> **flodis said:**
> thanks!
please show me when you get back from your vacation :)

Sure, just did as I described but we can have a workshop, bring your laptop with ubuntu and the info about vpn server... I e the .pcf file.

You have to update this post so all users will understand what we did if we reach a success.

Br
Sunken

---

### Post by Jaxilian on 2007-07-25
Thanks Sunken
VPN is now working for me. The key is the default.conf.file

I had probs first with script error a bit, but I fixed that by completely reinstall vpnc.

---

### Post by sunken on 2007-07-25
> **flodis said:**
> Thanks Sunken
VPN is now working for me. The key is the default.conf.file

I had probs first with script error a bit, but I fixed that by completely reinstall vpnc.

No problems, this is what ubuntu is all about, free and good support.

In your case I think you had a corrupt installation since you missed the script file that I had.

Br
sunken

---

