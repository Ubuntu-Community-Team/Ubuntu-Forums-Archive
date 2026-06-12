---
title: "VPN questions"
date: 2016-11-05
forum: Networking &amp; Wireless
---

### Post by digi84 on 2016-11-05
I hope this is in the right place.  Wasn't sure if this should go under Networking or Software but here it goes.


I have never used a VPN before but everyone tells me I should.  So my question is can anyone recommend a good one for Ubuntu?  Just doing a general web search I came across a few recommendations for Anonymous VPS ([https://www.privateinternetaccess.com/](https://www.privateinternetaccess.com/)).  Has anyone used them?  Are they any good?

A free service would be preferred of course but I know the addage *You get what you pay for* so I don't mind a paid service as long as the price tag isn't too crazy.

Second part of the question is how do you set the VPN up?  Do you just install the client and run it and thats it?  Or is there more to it?

Thanks for any info!

---

### Post by TheFu on 2016-11-06
There are many reasons to use a VPN.  Either to 
a) hide your traffic from your ISP or 
b) make a less open connection when we are at coffee shops, hotels and traveling
are the main ones.

These require different locations for the VPN "end-point" to be effective. Both are useful.

a) cannot be your home.
b) probably should be your home, assuming you want to access files and data stored there.  I'd rather see you do that than use any "cloud" services, actually.

The VPN used is almost always openVPN. That is the software, but commercial services will brand it as something else.  The main things you need to know are
1) don't use pptp, ever.  This has been cracked for years - decades. Almost anyone can see all the traffic inside, in real-time.  pptp is the default tunnel type for 95% of all VPN providers. 

2) Be careful running THEIR client software.  It probably isn't maintained as well as the stock, openvpn client.  Of course, their client will have all the settings made to use THEIR VPN service (at least the default pptp one), so it will be easier.  *Easy* isn't usually the same as *secure*.

3) Always test your VPN connections. Verify the type of VPN you want is being used. Make certain the traffic is all encrypted and that DNS isn't leaked. You want all DNS traffic to go down the VPN tunnel too.  You'll probably need to get wireshark working for this, but it really is necessary. After all, a false sense of security when it doesn't actually exist is a really bad thing.

4) You might want to pay for any commercial VPN service using a fake name, fake location, and gift credit card. After all, if you are trying to hide and it is trivial to trace your traffic to an IP and to a provider and to your name, what good is that?  Plus, VPN providers tend to deal with some shady people. Do you want them having your real credit card data?

Lastly, I probably would have posted this in the *Security* sub-sub-forum. :)

---

### Post by digi84 on 2016-11-06
Sorry all of this is a bit over my head, lol.

> 
These require different locations for the VPN "end-point" to be effective. Both are useful.

a) cannot be your home.
b) probably should be your home, assuming you want to access files and  data stored there.  I'd rather see you do that than use any "cloud"  services, actually.

The only computer I use is the desktop at home.  So do I want the end-point to be home, or should it not be home?

> 2) Be careful running THEIR client software.  It probably isn't  maintained as well as the stock, openvpn client.  Of course, their  client will have all the settings made to use THEIR VPN service (at  least the default pptp one), so it will be easier.  *Easy* isn't usually the same as *secure*.

So is there a third party or Linux/Ubuntu client I should use for managing VPN?

> 3) Always test your VPN connections. Verify the type of VPN you want is  being used. Make certain the traffic is all encrypted and that DNS isn't  leaked. You want all DNS traffic to go down the VPN tunnel too.  You'll  probably need to get wireshark working for this, but it really is  necessary. After all, a false sense of security when it doesn't actually  exist is a really bad thing.

where can wireshark be obtained through?  I checked Synaptic and there is alot of wireshark stuff, not sure what I should get.  

wireshark
wireshark-common
wireshark-dev
wireshark-doc
wireshark-gtk
wireshark-gt

Also, how do I test my VPN connections?  Is that done through the client or wireshark?

> 4) You might want to pay for any commercial VPN service using a fake  name, fake location, and gift credit card. After all, if you are trying  to hide and it is trivial to trace your traffic to an IP and to a  provider and to your name, what good is that?  Plus, VPN providers tend  to deal with some shady people. Do you want them having your real credit  card data?

Yeah, I was planning on doing a pre-paid credit card to pay for it.  Still not sure what paid service I should go with though.  Is the one I liked in OP a decent one?  It offers PPTP, OpenVPN and L2TP/IPSec(Yes, don't use PPTP, but it has OpenVPN which is what I want, yes?).  If not is there one in particular you would recommend?


Finally...

> Lastly, I probably would have posted this in the *Security* sub-sub-forum.

*In Homer Simpson voice*  DOH!




Thanks again for your reply!

---

### Post by TheFu on 2016-11-06
> **digi84 said:**
>  The only computer I use is the desktop at home.  So do I want the end-point to be home, or should it not be home?


If you are only at home, then I suspect you don't trust your ISP.  A VPN from your home TO your home would be pretty worthless. I suspect you want an exit point someplace else, for some reason?


> **digi84 said:**
>  So is there a third party or Linux/Ubuntu client I should use for managing VPN?
  I try to stay with software from the official Canonical repos. But that software must be compatible with whatever provider you select.  You'll need to configure it - usually that means editing config files with a text editor.  [https://help.ubuntu.com/lts/serverguide/openvpn.html](https://help.ubuntu.com/lts/serverguide/openvpn.html) - you only care about the client-side if you use an external provider.  That provider should have sufficient instructions to let you configure it yourself.
There is also this [https://askubuntu.com/questions/460871/how-to-setup-openvpn-client](https://askubuntu.com/questions/460871/how-to-setup-openvpn-client) if you are using a desktop.  I prefer the server/CLI methods, since most of my systems are servers - no GUI.

If you use client software from the VPN provider, then you must trust it not to screw up your system and not to be out of date and unpatched.  If you manually install any software outside the repos or using a trusted PPA, then YOU MUST MANUALLY look for and update any of that software to avoid security issues.  

Of course, there are many differing opinions on this aspect.

> **digi84 said:**
>  where can wireshark be obtained through?  I checked Synaptic and there is alot of wireshark stuff, not sure what I should get.  

wireshark
wireshark-common
wireshark-dev
wireshark-doc
wireshark-gtk
wireshark-gt

[https://askubuntu.com/questions/700840/how-to-install-wireshark-on-my-dell-with-ubuntu-14-04](https://askubuntu.com/questions/700840/how-to-install-wireshark-on-my-dell-with-ubuntu-14-04)  You'll probably need some slight training on wireshark for that tool to be of use. This isn't a "install and click 1 button tool" - sorry. Most of the skill in using it comes from the operator, you.  I wouldn't suggest that my mother use wireshark - she doesn't have the background for that to make sense. OTOH, I don't let Mom have sudo access either.

Network sniffing stuff: [https://www.irongeek.com/i.php?page=security/AQuickIntrotoSniffers](https://www.irongeek.com/i.php?page=security/AQuickIntrotoSniffers)


> **digi84 said:**
>  Also, how do I test my VPN connections?  Is that done through the client or wireshark?

You have to make a VPN connection, then use wireshark (usually from a different machine) to watch all the network traffic and verify that there isn't **any** leakage outside the VPN connection.  Any leakage means the VPN isn't doing what it should.



> **digi84 said:**
>  Yeah, I was planning on doing a pre-paid credit card to pay for it.  Still not sure what paid service I should go with though.  Is the one I liked in OP a decent one?  It offers PPTP, OpenVPN and L2TP/IPSec(Yes, don't use PPTP, but it has OpenVPN which is what I want, yes?).  If not is there one in particular you would recommend?


Supporting a protocol doesn't mean it is configured to actually use it. Chances are that pptp is the default and to do anything else means you'll manually have to disable that one and enable the one you want.  IPsec is the best of those options, provided the keys used are non-trivial (20+ random characters). Actually a 2048-bit key would be better.  Keys are effectively uncrack-able by using network protocol analysis, but passwords are extremely crack-able because most people/systems don't allow long enough passwords to be useful in a meaningful way.  Less than 16 characters is a joke, BTW.

---

