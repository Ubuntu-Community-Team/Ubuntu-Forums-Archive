---
title: "New to Ubuntu need some help"
date: 2010-09-24
forum: New to Ubuntu
---

### Post by Vallijoe on 2010-09-24
So i installed Ubuntu 10.04 LTS, im having trouble connecting to the internet with my Belkin wireless G gaming adapter Ver. 2000 Model no. F5D7330. I have an old dell dimension 4600 it connects through Ethernet and connects to wireless router works good with everything else but cant get it going on Ubuntu and again im a noob to Ubuntu lol so any help is appreciated

---

### Post by spiky001 on 2010-09-24
Hi as you have just installed have you updated it yet, you will need to use a wired connection this might solve the problem otherwise, if that dosn,t work gp to applications/administrations/hardware drivers see if it can find 1 but you will need internet

---

### Post by Vallijoe on 2010-09-24
alright al give it a try and this adapter didn't come with any drivers but al update and be back

---

### Post by SaintDanBert on 2010-09-24
Welcome,
    I'd love to try to help, but I need more details about what you have tried, error messages, log entries, etc.

    Are you saying that your box sees your local lan and the lan cannot talk with the internet? Further, are you waying that other boxes talk with the internet, but this one does not? Are you saying that this box talks to the internet in ways that do not involve Ubuntu?

    Years ago, compilers would read the source code and die at the first problem saying, "syntax error".  Imagine our joy when they would read the whole source file and report "syntax error {details} at line {number}."  It is almost always helpful to provide more information than you think is important.  These forums (fora?) have various postings that speak to question crafting.

I'll check back later?
~~~ 0;-Dan

---

### Post by SaintDanBert on 2010-09-24
> **spiky001 said:**
> Hi as you have just installed have you updated it yet, you will need to use a wired connection this might solve the problem otherwise, if that dosn,t work gp to applications/administrations/hardware drivers see if it can find 1 but you will need internet

I agree that he needs to do the out-of-box update.  However,
I think he says that the box won't talk with the internet. That makes any sort of time-zero update problematic.

If you have some other box that does talk with the internet, you can at least browse for your error messages or log messages to see if you find published work arounds.

Cheers,
~~~ 0;-Dan

---

### Post by Vallijoe on 2010-09-24
im sharing a connection with my laptop to my desktop to install the updates, its updating as i reply, but the belkin gaming adapter it works with my other desktop running windows xp, the adapter connects to my linksys router wireless and gives the adapter internet through Ethernet don't know if i made sense

im back its still not connecting any suggestions?

---

### Post by SaintDanBert on 2010-09-25
Let me see if I understand your configuration:
[list]
[*]something connects your building to the internet: cable modem? ADSL? other? I'll use the telephone term "point of presence" or POP.
[*]your POP has an RJ45, wire net connector for wide area network (WAN)
[*]your WAN port is connected to the Belkin box
[*]Belkin provides wireless and some number of wire net ports (RJ45).
[*]Belkin connects to the internet WAN using some dance -- DHCP or other login
[*]Your workstations connect to Belkin using some dance -- DHCP over wire or wireless
[/list]

I don't know details of this Belkin box. Will it support enough connections for all of the workstations you want running at the same time?  Is your Ubuntu box the only one with troubles?

Boxes in the role you have set the Belkin to fill, typically play a game called "network Address translation" (NAT). On the WAN side, the box has an IP address known to the public internet via your ISP. Your workstations (LAN) talk using one of the private networks like "192.168.xxx.yyy". Using NAT, the box converts your LAN IP conversations to WAN IP conversations.  Because of all the thinking that goes on, it is common to limit the number of unique "lies" the box must manage.  This limit has never troubled my LANs but the limit(s) are often there and bite folks.

One of the details that the Belkin box gives each LAN workstation is its IP address. Other details include a "default gateway" and "name server" addresses.

The command **dig** will tell you if your workstation knows about any name server.

The command **netstat** will tell you if your workstation knows about a default gateway.

If either or both of these are absent, your workstation will see the LAN but will be unable to do much with it.

Cheers,
~~~ 0;-Dan

---

