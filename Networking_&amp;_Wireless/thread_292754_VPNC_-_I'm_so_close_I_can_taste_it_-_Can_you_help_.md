---
title: "VPNC - I'm so close I can taste it - Can you help please?"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by JimTDI on 2006-11-04
Hi everyone!  I'm trying to VPN into my work - using VPNC...

got vpnc setup, firestarter installed, and I appear to be able to connect to my work's Cisco concentrator (I see their welcome banner!) but then I am unable to ping the machine I want to connect to either by it's name, or IP address.  In fact, I'm not able to ping anything on their network after I connect.

I'm pretty sure I have a tunnel connection, as I lose all my local internet access while connected with VPNC, same behaviour as when I connect to work using a Windoze box.

Can anyone give me an idea of what to do next - I need to be able to RDP to my desktop at work, then I can dump my local Windoze box and use my new love, Ubuntu!!

Thanks for any help you could give!

---

### Post by JimTDI on 2006-11-05
> **JimTDI said:**
> Hi everyone!  I'm trying to VPN into my work - using VPNC...

got vpnc setup, firestarter installed, and I appear to be able to connect to my work's Cisco concentrator (I see their welcome banner!) but then I am unable to ping the machine I want to connect to either by it's name, or IP address.  In fact, I'm not able to ping anything on their network after I connect.

I'm pretty sure I have a tunnel connection, as I lose all my local internet access while connected with VPNC, same behaviour as when I connect to work using a Windoze box.

Can anyone give me an idea of what to do next - I need to be able to RDP to my desktop at work, then I can dump my local Windoze box and use my new love, Ubuntu!!

Thanks for any help you could give!


well I spent another whole day yesterday - still no go.  Once I see the welcome banner on the server I'm VPNing to - should I be able to launch my Terminal Service Client and connect to a machine on the remote network or at least ping some resource on the remote network by it's IP address from my Ubuntu terminal window??

Am I missing another step - or package/library I should install?  I tried resolvconf - then am unable to even the the welcome banner on the remote VPN server.

Ideas anyone???

---

### Post by JimTDI on 2006-11-05
OK, duh... I feel so stupid.  I turned off the firewall (FireStarter) completely, and now I am able to connect to my remote desktop just fine with Terminal Services.

Now I'll figure out what I need to enable in the firewall so I don't have to leave it turned off...

Just in case this helps someone else... :)

---

### Post by NetworkGuy on 2006-11-05
Start with the IKE and L2TP protocols.  If you still need help after allowing  those ports, check out your messages file in /var/log to see what other ports you will need.

---

### Post by JimTDI on 2006-11-21
> **NetworkGuy said:**
> Start with the IKE and L2TP protocols.  If you still need help after allowing  those ports, check out your messages file in /var/log to see what other ports you will need.

Thanks NetworkGuy!

Can I open the IKE and L2TP protocols using FireStarter - or do I need to edit something/somewhere else.  I took a look at my /var/log/messages but don't see anything there that appears to be related to the firewall when my VPNC connection is blocked.  I am behind a hardware firewall so it's not like I'm wide open, and I know I configured my hardware firewall for VPN/Terminal Services a few years ago for my Windows boxes...

Thanks again!

---

### Post by JRyan on 2006-11-21
Wow, I have been doing the same thing.  ](*,) ](*,) 

Should be good now.

---

