---
title: "Is there any way to assign ppp interface on a pptp connection?"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by CyberAngel on 2006-11-18
I want to connect as client on a pptp server, but when I am connecting the default interface that it is created (If no other pptp connection exists) is ppp0.

Is there any way to assign always ppp1 (even if there is no existing pptp connection) on this specific connection?

---

### Post by CyberAngel on 2006-11-18
Found it just if anyone else cares.

there is an option that you can pass in the tunnel file located under /etc/ppp/peers/YourTunnel.

This option is "unit <interface number>"

if you set it like

unit 1

Then the created interface will be ppp1

---

### Post by lonetree on 2008-01-06
Hi,

are you referring this to client side?

regards,

---

### Post by CyberAngel on 2008-01-06
> **lonetree said:**
> Hi,

are you referring this to client side?

regards,

Yes I was referring to the client side but it is also working to the server side but I don`t know how it works for a specific client (specific username).

if you set the parameter ```
unit 4
``` into the file ```
/etc/ppp/pptpd-options
``` all the incoming connections will start have an interface name from ppp4 and above.

I need something like this because of the firewall.
I would like to be able to create different firewall rules for specific ppp interfaces that belongs to specific usernames.
Now I am not able to do something like this yet for the incoming connections....

If you have any suggestions they are all welcome :D

---

### Post by lonetree on 2008-01-06
> **CyberAngel said:**
> Yes I was referring to the client side but it is also working to the server side but I don`t know how it works for a specific client (specific username).

if you set the parameter ```
unit 4
``` into the file ```
/etc/ppp/pptpd-options
``` all the incoming connections will start have an interface name from ppp4 and above.

I need something like this because of the firewall.
I would like to be able to create different firewall rules for specific ppp interfaces that belongs to specific usernames.
Now I am not able to do something like this yet for the incoming connections....

If you have any suggestions they are all welcome :D

Hi CyberAngel,

thanks for your advice. My knowledge is limited. :-(

By the way, are you currently running any pptp server on ubuntu?

regards,

---

### Post by CyberAngel on 2008-01-06
> **lonetree said:**
> Hi CyberAngel,

thanks for your advice. My knowledge is limited. :-(

By the way, are you currently running any pptp server on ubuntu?

regards,

Yes I am currently running a pptp server on ubuntu :)

---

### Post by lonetree on 2008-01-06
> **CyberAngel said:**
> Yes I am currently running a pptp server on ubuntu :)

Hi,

thanks for you reply. May I know which ver of ubuntu are you using to set your pptp server? I am having some trouble with 7.10. 

regards,

---

