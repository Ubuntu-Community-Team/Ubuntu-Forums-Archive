---
title: "Access to Windows shares from internet"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by wjhildreth on 2008-01-02
Hello all,

Please forgive me if I have posted to the wrong message group.

Here is my scenario.

I have set up Ubuntu Server running Zimbra Collaboration Suite for email for a facility I work for. I also have a windows file server that they use to store their main files. I know that I can make the files available to Linux by using Samba. But is there a simpler way that is safe for accessing across the internet?

I have about 4 or 5 users who will need to access their files from home using their Internet connection. Is their a simple and SAFE way of giving these users access to the files from home?

One solution that pops into my mind is maybe LTSP. But the only way I have read to access it is from a Dumb terminal (or thin client) can it be accessed from across the NET? Is there another way to do this? Can you use Xming to access LTSP?

Many thanks for your help and guidance.

Warm Regards,
Joe Hildreth

PS - Non related but notable, My wife has taken the Ubuntu Plunge. She bought herself a notebook from Dell with Ubuntu pre-installed. So far she is loving it. Although there have been a glitch or two.

---

### Post by Predator[23rd] on 2008-01-02
three words: VIRTUAL PRIVATE NETWORK. :D

never did it so I can't say how easy or difficult it is. check [http://openvpn.net/](http://openvpn.net/) for more information.

if your users are capable computer users a much easier tunneling could possibly do the same trick.

---

### Post by wjhildreth on 2008-01-02
Thanks Predator for the link.

A VPN is a possible solution. But you know how users get, give them some they eventually want more. I didn't think about a VPN connection. These guys just left a Citrix environment, I guess that is why I was thinking LTSP. 

I am still open for more ideas if anyone has any.

Regards,

Joe

---

### Post by Predator[23rd] on 2008-01-02
> **wjhildreth said:**
>  But you know how users get, give them some they eventually want more.

I know, they always want more. But is there anything beyond a VPN connection between your couch and your secretary's printer??? :D

---

### Post by Norpingo on 2008-01-06
I have no idea what LTSP is, but regardless I still think VPN is the only way to fly :)

If you go for FOSS your choices are IPsec (OpenSWAN/FreeSWAN), PPTP (PopTop) or SSL-Based (OpenVPN).

OpenVPN is what I use personally. The reason for this is that it's secure enough for most needs, it's relatively easy to setup, and it handles most networking situations without too much trouble. PPTP is as far as I can tell not renowned for it's fantastic security, and IPsec is not always easy to get working in environments where you use NAT. That would include most, if not close to all home networks.

The howto at [http://openvpn.net](http://openvpn.net) is very good, and should get you from A to B without much trouble. It will explain how to get your connection going with everything from the most basic  of security all the way up to 2-factor authentication and all the other trimmings.

The disadvantage of OpenVPN in comparison with the other 2 types (IPsec and PPTP) is that you need to install a client on the Windows machines (Windows has built-in clients for IPsec and PPTP), and that keeping track of client certs can sometimes be a bit of a hassle.

As for the users wanting more - How much more could they possibly want then a connection to the network? If you set VPN up right they will have access to the same stuff they have at work, when they are away from work. That would also include access to Citrix if that should be required.

---

