---
title: "How to configure port forwarding"
date: 2015-04-14
forum: Networking &amp; Wireless
---

### Post by satimis on 2015-04-14
Hi all,

I'm trying to forward port 80 to internal IP 192.168.0.xxx

Router TP Link
Model TL-WR740N

-> Forwarding
Service Port 80
Internal Port - blank
IP Address - 192.168.0.xxx
Protocol - ALL
Status - Enabled
Common Service Port - HTTP

-> Save

Error```

Error code: 14007
Error: The ports of the remote web management and the virtual server are conflicted.

```

Please help

Regards
satims

---

### Post by michi1983 on 2015-04-15
Please make a screenshot of your router status -> WAN and upload it as attachment in your next comment.
Please use the attachment button in the editor here in the forum and no external hosters.

---

### Post by satimis on 2015-04-15
> **michi1983 said:**
> Please make a screenshot of your router status -> WAN and upload it as attachment in your next comment.
Please use the attachment button in the editor here in the forum and no external hosters.

Hi,

Advice noted.  Thanks

Now I found the cause.  The router default setting takes up this port.  Now I have 2 options;
1) change the default setting listening to port 8080 and forward port 80 to the remote PC which in my case is the guest of KVM running Apache web server.

OR

2) retain the default setting and forward port 8080 to the remote PC.  But I have no idea how to make this change on the guest listening port 8080 instead of 80.  Besides can visitors browse the websites on the server if forwarding port 8080 instead of port 80?

Please advise.  Thanks

Regards
satimis

---

### Post by Doug S on 2015-04-15
> **satimis said:**
> Now I found the cause.  The router default setting takes up this port.  Now I have 2 options;
1) change the default setting listening to port 8080 and forward port 80 to the remote PC which in my case is the guest of KVM running Apache web server.

OR

2) retain the default setting and forward port 8080 to the remote PC.  But I have no idea how to make this change on the guest listening port 8080 instead of 80.  Besides can visitors browse the websites on the server if forwarding port 8080 instead of port 80?I would go with option 1. But yes, visitors could browse the websites with option 2, but they would have to specify the port on the URL, i.e. example.com:8080/bla/bla

---

### Post by satimis on 2015-04-15
> **Doug S said:**
> I would go with option 1. But yes, visitors could browse the websites with option 2, but they would have to specify the port on the URL, i.e. example.com:8080/bla/bla
Thanks

If I change the port default setting on the router would there is any influence?

Regards
satimis

---

### Post by SeijiSensei on 2015-04-16
If the router is grabbing port 80 on the publicly-facing side, I'd disable external access entirely.  The only access to the router's configuration should be from a machine behind the firewall.  It might free up port 80 on the outside.

---

### Post by satimis on 2015-04-16
> **SeijiSensei said:**
> If the router is grabbing port 80 on the publicly-facing side, I'd disable external access entirely.  The only access to the router's configuration should be from a machine behind the firewall.  It might free up port 80 on the outside.
Hi,

Thanks for your advice.

Could you please explain in more detail on your suggested setup?

current local network:
Internet/ISP -> Router -> Intranet -> PCs

In the local network there is no firewall between Internet/ISP (publicly-facing side) and router.  

On router I can set;
Security -> Remote Management
web management port: 80 (which settings is default set by the router manufacturer)

to 81 or any number

But thereafter to connect and login the router for admin I must type [http://192.168.0.xxx:81](http://192.168.0.xxx:81)

Would there is any disadvantage and interference to the local network in changing the web management port: from 80 to 81? 

Thanks

Regards
satimis

---

### Post by michi1983 on 2015-04-17
Not at all, you just have to type the port manually (as you already intended) when you want to access the webinterface of the router.

---

### Post by satimis on 2015-04-17
> **michi1983 said:**
> Not at all, you just have to type the port manually (as you already intended) when you want to access the webinterface of the router.
Hi,

Thanks

Got it done making following changes

1)
Web Management Port: 81 (chaged from 80)
Remote Management IP Address: 0.0.0.0 (default, set by the factory)
-> Save

2)```

ID 	Service Port 	Internal Port 	IP Address 	Protocol 	Status
1	80		80		192.168.0.xxx	ALL		Enabled

```

Reboot router.

Regards
satimis

---

### Post by SeijiSensei on 2015-04-17
Just to clarify what I said before, most routers let you disable web access to the management console from the Internet-facing side.  That will still let you manage it by connecting to 192.168.0.xxx from the internal network, but not let random crackers try to break in from outside.  Moving to port 81 helps with that, but nowhere near as much as disabling remote access.  So see if your router has a specific option to disable external access to the management console. For example, on my router it's under "Remote Administration."

---

### Post by satimis on 2015-04-17
> **SeijiSensei said:**
> Just to clarify what I said before, most routers let you disable web access to the management console from the Internet-facing side.  That will still let you manage it by connecting to 192.168.0.xxx from the internal network, but not let random crackers try to break in from outside.  Moving to port 81 helps with that, but nowhere near as much as disabling remote access.  So see if your router has a specific option to disable external access to the management console. For example, on my router it's under "Remote Administration."
No such an item
(please refers to screeshot_remote_management.png attached)

On;
-> Security -> Advanced Security
Shall I enable "DoS Protection" ?
(please refers to screenshot_advanced_security.png attached)

Thanks

Regards
satimis

---

### Post by SeijiSensei on 2015-04-17
Since your "Remote Management IP Address" is set to all zeroes, the function is disabled.  From section 4.9.4 of the [manual]("http://www.tp-link.com/Resources/document/TL-WR740N_741ND_User_Guide.pdf") for your router,
>  Remote Management IP Address - This is the current address you will use when accessing your Router from the Internet. This function is disabled when the IP address is set to the default value of 0.0.0.0. To enable this function change 0.0.0.0 to a valid IP address. If set to 255.255.255.255, then all the hosts can access the Router from internet.

---

### Post by satimis on 2015-04-17
> **SeijiSensei said:**
> Since your "Remote Management IP Address" is set to all zeroes, the function is disabled.  From section 4.9.4 of the [manual]("http://www.tp-link.com/Resources/document/TL-WR740N_741ND_User_Guide.pdf") for your router,

Your advice noted.  Thanks

Regards
satimis

---

