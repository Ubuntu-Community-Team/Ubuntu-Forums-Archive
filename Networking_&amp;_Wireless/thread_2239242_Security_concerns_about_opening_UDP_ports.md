---
title: "Security concerns about opening UDP ports"
date: 2014-08-12
forum: Networking &amp; Wireless
---

### Post by rbrown3 on 2014-08-12
Greetings:

   I am looking at a video streaming system that uses WebRTC (among other streamng technologies). The makers of this system, which is called Kurento, in their installation instructions, say that in order for the system to work, I have to open *all* UDP ports. Apparently this system opens a random port in order to service video requests, and the creators do not restrict which ports it will open.

   I am concerned about the security of a system with UDP ports fro 1024 -> 65k open. Could someone tell me just how compromised such a system would be? What are the security risks of using software like Kurento?

---

### Post by SeijiSensei on 2014-08-12
I wouldn't touch it myself.  Why can't they design their software to use a pre-defined port, or allow you to specify one yourself?

---

### Post by ian-weisser on 2014-08-12
> **rbrown3 said:**
> I am concerned about the security of a system with UDP ports fro 1024 -> 65k open. Could someone tell me just how compromised such a system would be?

It depends upon what you mean by an 'open' port.

The lifecycle of a process reading/writing using a port is generally to bind(), listen(), read(), write(). There is no 'open' or 'closed' for applications. So to 'open' a vast number of ports is gibberish. The application itself uses ports directly.

However, 'open' and 'closed' ports *do* have meanings for firewall (iptables). An 'open' port means the packet is accepted past the firewall...regardless of whether or not an application is listening on that port. If nothing is listening, the packet is ignored anyway.

So the instructions seem to be for your firewall.
How does that differ from Ubuntu's default firewall?

```
$ sudo iptables -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```
It doesn't. Ubuntu's default firewall settings are already to accept all packets in that range ('open')

My recommendation: SeijiSensei is right. I wouldn't install it. Using random ports over such a large range seems a poor design.

---

### Post by rbrown3 on 2014-08-12
[SIZE=3]
SeijiSensei and ian-weisser: Thanks to both of you for your replies. 

ian-weisser: if I am reading your reply correctly, it sounds like the default Ubuntu firewall is already configured to allow the full range of UDP ports by default. Am I understanding you correctly? If I am, then my problems with Kurento are not what the Kurento folks have been telling me they are. Not that this matters, it sounds like their design is poor if they use such a wide range of UDP ports for their video. I may have to consider looking at (or creating) other technologies to meet my needs. 

Can anyone suggest a good video project that is better designed, provides a simplified API for WebRTC functionality, and can play and record video?

Also: I would like to refer the Kurento forum participants to this Topic, for their information and edification.  Does anyone have any objections to my doing so?
[/SIZE]

---

### Post by ian-weisser on 2014-08-12
> **rbrown3 said:**
> [SIZE=3]it sounds like the default Ubuntu firewall is already configured to allow the full range of UDP ports by default. [/SIZE]

Yes, it is.
But that doesn't mean that future default firewalls will.
Nor that users won't change their firewall settings, unintentionally breaking Kurento functionality if it cannot detect the closed ports.

---

