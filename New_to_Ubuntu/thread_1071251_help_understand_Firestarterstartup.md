---
title: "help understand Firestarter/startup?"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by deadmanschest on 2009-02-16
Hi all - did some searches - no joy. Laptop on wireless and ethernet cable connection. Installed Firestarter and it offers one choice of adaptor...

When I start up it doesn't, and if I am on wireless when it last? was open on wired it won't run. Very irritating.

Clusty searches find old threads that say that the firewall runs 24/7, no need to startup the Firestarter gui, it's just a front end to a service that always runs in Ubuntu, and it's only windows newbies that need to see an icon to know that the firewall is working....whatever.

Simple question - Since the Ubuntu documentation advocates installing a Firewall, is or is not a firewall operating regardless of the network adaptor I have in use on startup?

Thanks

dmc

---

### Post by cariboo on 2009-02-16
The firewall in Ubuntu is called iptables , but there are no ports listening on a default installation, so there is no need for a firewall. The prefered gui for iptables is gufw, as firestarter is no longer maintained. To check what iptables rules you have set open an Applications-->Accessories-->Terminal and type:

```
sudo iptables -L
```

For more info on iptables, have a look [here]("http://help.ubuntu.com/community/IptablesHowTo").

Personally I use a Linksys wrt54gs router with a builtin firewall, so I don't feel any need for a second one.

Jim

---

### Post by deadmanschest on 2009-02-16
> **cariboo907 said:**
> The firewall in Ubuntu is called iptables , but there are no ports listening on a default installation, so there is no need for a firewall. The prefered gui for iptables is gufw, as firestarter is no longer maintained. To check what iptables rules you have set open an Applications-->Accessories-->Terminal and type:

```
sudo iptables -L
```

For more info on iptables, have a look [here]("http://help.ubuntu.com/community/IptablesHowTo").

Personally I use a Linksys wrt54gs router with a builtin firewall, so I don't feel any need for a second one.

Jim

Hey Jim - thanks, thats the most concise expl. I have found, and I read a fair bit. I have a NAT enabled wire/wireless router at home, but this laptop is for mobile. I've had some issues with setting up a VPN for mobile use (in windoze) and I figured best to understand some of what's under the hood in U8.10 before getting all twisted up...

Thanks for the links..

cheers

dmc

PS - that your sled dog in the avatar pic?  hehe - I just left Victoria...hehe

---

### Post by cariboo on 2009-02-16
Your Welcome.

Jim

---

