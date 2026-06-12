---
title: "stubborn network"
date: 2005-08-23
forum: Networking &amp; Wireless
---

### Post by one_ro on 2005-08-23
Guys,

After 5 or 6 hours of painfully trying everything I know, I have to ask for yor advice (again).

Basically, a smooth Kubuntu 5.04 installation on a Toshiba Satellite Pro laptop; a static IP, perfectly set networking parameters (gw, dns, /etc/network/interfaces, /etc/resolv.conf, netstat -nr, etc. etc. etc.).

I can ping myself, I can ping the gw, I can ping the dns... I just can't access the Internet ...  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,) 

The trick with [FONT=Arial]ifdown eth0[/FONT] and [FONT=Arial]ifup eth0[/FONT] (which solved my problem in the past) doesn't help me anymore...

Everything I do seems futile. Do you have another trick or tip in the sleeve? I'd be very grateful.

Thanks in advance,
Adrian

---

### Post by lol on 2005-08-23
what do you mean by : >  I just can't access the Internet 

That you cannot ping any other IP address than yours, the gw and the dns? or just that you cannot browse the net? We need more information to be able to help you here...

---

### Post by one_ro on 2005-08-24
[QUOTE=lol]what do you mean by : 

That you cannot ping any other IP address than yours, the gw and the dns? or just that you cannot browse the net? We need more information to be able to help you here...[/QUOTE]

Hi and good morning (here)
I think both: I can't ping any other external address *and* I can't browse the Internet.
Thanks for your reply; what other information should I provide?
Adrian

---

### Post by lol on 2005-08-24
Maybe you could provide the content of /etc/network/interfaces and the result of the command 'route'... the fact that you can ping the DNS or your gw seems to prove that the network is correctly setup and that it is a routing issue, but I am not really sure about this.

---

### Post by one_ro on 2005-08-24
[QUOTE=lol]Maybe you could provide the content of /etc/network/interfaces and the result of the command 'route'... the fact that you can ping the DNS or your gw seems to prove that the network is correctly setup and that it is a routing issue, but I am not really sure about this.[/QUOTE]

I suspect an IP conflict (I used my 4 years old IP, probably someone else on my internal network did something stupid). Changing the IP solved it. Gosh I lost one day just to change an IP... sigh.
Anyways, thanks again.
Cheers,
Adrian

---

