---
title: "How to Secure What You Transmit Over WiFi?"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by ShinHadoken on 2008-07-31
Hey guys,

Lately, I've been pretty security-paranoid. Suppose I'm sitting at Starbucks, where the wireless connection allows **anybody** on. How do I secure/encrypt what I transmit to prevent eavesdropping/packet-sniffing?

Thanks a ton guys!

SH

---

### Post by kevdog on 2008-08-01
Use wpa which encrypts the wireless traffic.

---

### Post by Njem on 2008-08-01
Except that at a coffee shop you're at the mercy of what encryption they have set up, or not, probably not. You of course don't have any shares open at that point. I suppose if you VPN to some other site then all communication to there is encrypted. If that connects you to your work computer and you RDP to control your work computer and let it browse the web, then all your traffic at the coffee shop is to the VPN, encrypted. Otherwise if someone is actually savvy enough to sniff the packets flying between your laptop and the coffee shop wireless, I don't know what you could do.

---

### Post by jerome1232 on 2008-08-01
This is for browser traffic only, kinda of a easy way to encrypt the traffic.

I use SSH to setup a socks proxy. On my windows vista laptop I have openssh installed (works for command line ssh just like on linux)

You would need to have shell access to a computer somewhere out there in the world running a ssh server. (like your desktop at home or something)

```
ssh -CnD 8232 joebob@computer
```
-Cnd 8232   -C is for compression (not needed) n is there becuase we don't actauly need shell access (not needed, D binds to a port, I used 8232 here you can use whatever.

Then go into your favorite browser set it to use a socks proxy on port 8232 (or whatever you choose)

If you goto whatismyip.org it should now show the ip of the machine you ssh'd into not starbucks ip.

This only protects from people in the area from capturing data on the lan side, but that's my main concern for wireless in a unsecured public connection anyways.

---

### Post by ilrudie on 2008-08-01
I would agree with the use of secure protocols like ssh/scp.  Its your best bet.  Setting up an ssh tunnel is a good start or you could set up a VPN.

---

### Post by ShinHadoken on 2008-08-01
Okay, cool. Thanks guys, for all the feedback. Let me put it this way: The three network services I *always use* are 

1.. Internet Browsing (Firefox)
2. Email Client (Evolution)
3. Instant Messaging (Pidgin)

How would I go about securing the traffic of those apps? My hypotheses:

1.. For browsing, set up a SOCKS proxy by SSHing a machine at home
2. Use the above socks proxy OR use a PGP key to encrypt all outgoing email
3. Use the above socks proxy

By the way jerome, is that all I have to do? Just install ssh on a machine at home at set up a connect on a fixed port, or do I need to change some sort of setting or install some special software. You'll have to forgive me, I've never used a proxy except for anonymous browsing via services like [VTunnel]("https://www.vtunnel.com/").

Thanks a LOT guys,

SH

---

### Post by kaffe_02 on 2008-08-01
Here is tutorial on setting up a squid proxy

[http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html)

Is your home IP address static or DHCP?  If its DHCP then its possible it could change, and then youd have to change the IP that your proxying all of your traffic through.

If your browsing to HTTPS sites and using secure pop/imap and your not instant messaging in the clear I dont know that you need to go through setting up the proxy.  But if it makes you feel better go for it.

---

### Post by ShinHadoken on 2008-08-01
Well, not every site I visit has SSL encryption, I think I use secure POP, but not secure SMTP, and I just don't know about my instant messenger. I'll certainly a look at that though.

---

### Post by jerome1232 on 2008-08-01
> **ShinHadoken said:**
> 
By the way jerome, is that all I have to do? Just install ssh on a machine at home at set up a connect on a fixed port, or do I need to change some sort of setting or install some special software. You'll have to forgive me, I've never used a proxy except for anonymous browsing via services like [VTunnel]("https://www.vtunnel.com/").

Thanks a LOT guys,

SH

Well most of those programs can be configured to go through that Socks proxy using ssh.

firefox  - edit>>preferences>>advanced>>settings>>Manualproxy Configuration     Under socks you type in localhost or 127.0.0.1 and specify the port

pidgin - tools>>preferences>>Network>>Configure Proxy>>Manual proxy  and enter the same info

I don't use evolution but it shouldn't be hard to find

I believe the proxy setup is similar on the various applications.
I just like this method because it's very easy to setup, I have a simple batch script on my windows computer that makes connecting the ssh part a double click away.

I would suggest trying various methods to see what suits you.

---

### Post by ShinHadoken on 2008-08-01
So let me make sure I have this straight:

1.. Install SSH on a pc at home.
2. SSH into the pc by "ssh -D 4567 user@myhomepc"

From here, could I go into System > Preferences > Network Proxy and

1. Check the box labeled "Use the same proxy for all protocols"
2. In the box type "localhost" or "127.0.0.1" and specify a port number.

Would that filter *everything* through a proxy? 

Also, is there a way I could maybe put a command in a script and get it to run at boot which would automatically establish the SSH connection I need? 

Thanks for your patience and feedback,

SH

---

### Post by jerome1232 on 2008-08-01
Not quite, 
Since this is an ubuntu computer you should be able to go to System>>Preferences>>Network Proxy  select Manual Proxy configuration, put localhost in for Socks and the port number in the box to the right.

Make sure your apps are set to use gnomes proxy settings it's the "use system proxy" setting, if they don't have that setting (I think they all do) you have to set it in the individual apps.

A good way to test it is to tell them to go through the proxy then kill the ssh session, they should not be able to access internet untill you tell them to not use the proxy.

---

### Post by ShinHadoken on 2008-08-01
Okay, so set it up only under socks at the Network Proxy menu, and then everything should work (after configuring the apps)?

---

### Post by jerome1232 on 2008-08-01
> **ShinHadoken said:**
> Okay, so set it up only under socks at the Network Proxy menu, and then everything should work (after configuring the apps)?

Yup! report back after testing it all out!

---

