---
title: "How to install Novatel Wireless Merlin U740"
date: 2006-09-08
forum: Networking &amp; Wireless
---

### Post by dapissarenko on 2006-09-08
Hello!

I have a Novatel Wireless Merlin U740 PCMCIA card for mobile internet access (via GPRS, UMTS and HSDPA).

How can I install it under ubuntu?

TIA

Dmitri

---

### Post by skaaptjop on 2006-11-06
[http://www.mybroadband.co.za/vb/showthread.php?t=21726](http://www.mybroadband.co.za/vb/showthread.php?t=21726) has some pretty handy Linux posts. I'm about to try and install mine as well ...

---

### Post by martin42 on 2007-01-28
I've got this working in a UK-spec Dell Latitude D620.  Dell ships these laptops with the 3G radio built in, which is cool.  The thing comes with an unactivated Vodafone SIM card
 but it's not locked to that network, so you can shop around for another SIM card.

I've written up some notes at [http://www.net42.co.uk/os/linux/d620_3g_datacard.html](http://www.net42.co.uk/os/linux/d620_3g_datacard.html)

Hope this helps.

---

### Post by dapissarenko on 2007-03-14
Hello!

Thanks all for the links!

> **skaaptjop said:**
> [http://www.mybroadband.co.za/vb/showthread.php?t=21726](http://www.mybroadband.co.za/vb/showthread.php?t=21726) has some pretty handy Linux posts. I'm about to try and install mine as well ...

The first command in this tutorial is

```
/etc/init.d/pcmcia start
```

When I type it in, I get following message:

```
* linux >= 2.6.13-rcl requires pcmciautils instead of pcmcia-cs
```

It seems that I need the *pcmcia-cs* package.

This is a problem, since the only way to get it from the internet is

a) via GRPS/UMTS/HSDPA data card or
b) using Wireless LAN.

a) doesn't work at the moment, and b) will - probably - be equally difficult to achieve.

On my laptop there is a normal (not wireless) LAN port and lots of USB ports, but I don't know where I could use them for accessing the internet. In all internet cafés and at all of my friends wireless LAN is installed.

So, somehow I need to get those package wihout access to the internet.

1) What options do I have? Is there some distribution with all these packages available on a CD or DVD?

2) If yes - which one should I buy?

3) Is this task (configuring a GRPS/UMTS/HSDPA data card) easier in the 6.10 version than in the *Dapper Drake*?

TIA

Dmitri Pissarenko

---

### Post by dapissarenko on 2007-03-20
Hi!

I've downloaded pcmciautils from

[http://packages.ubuntu.com/dapper/admin/pcmciautils]("http://packages.ubuntu.com/dapper/admin/pcmciautils")

and installed it on my machine.

However, the command

```
/etc/init.d/pcmcia start
```

still didn't work (same message as before).

Then I opened the file pcmcia in a text editor (it's a shell script) and then found out that the reason for the error is the fact that my linux kernel version isn't among valid ones. These valid kernel versions are listed in the pcmcia file and my version is not there.

So, it seems to me that upgrading to the latest version of ubuntu is the only solution.

Best regards

Dmitri Pissarenko

---

