---
title: "Help with Private Internet Acess code -- Ubuntu 17.10"
date: 2017-10-30
forum: Networking &amp; Wireless
---

### Post by spencer2 on 2017-10-30
I'm using Ubuntu 17.10 & have Private Internet Access VPN: when I try to access the internet with PIA turned off, I'm not able to connect. I read multiple forums on PIA's site & I think I'm missing the DNS settings in my NetworkManager.conf file. As far as the PIA settings specifically go, I don't have the killswitch enabled, I've tried getting inet working with IPv6 leak on & off, and nothing works. I know that I can turn off PIA & still access because I've done it many times before. Here is the code from NetworkManager.conf file: 

```

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no
```

I think that I need to add:

```
dns=dnsmasq
```

 under "Main", but I'm not enough of a code expert to know if this is correct. If so, where under "Main" does it go & what do I need to change from what is there currently. Any help on this would be greatly appreciated. 

As a side note: ever since the 17.04 to 17.10 upgrade, I've also not been able to shut down my laptop. I'm using an Acer Aspire F15 & my video card is an intel:

```
~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)

```

I've noticed that there are many other people having Nvidia card issues that are causing the same thing (no shutdown): might my lack of shutdown be a similar issue to the Nvidia one? Would the lack of proper shut down be effecting PIA related upgrades? I do have a separate ongoing post about the shut down issue elsewhere, so I'm not really trying to get that issue answered here: its just I've also seen multiple threads related fixing packages & reboots, so just in case that is important context, wanted to throw that in. 

Thank you for any & all help -- it is greatly appreciated. 

ps- while as I noted I'm not great with knowing code right off, I am good at cut & paste with some help & explanation. 
pss- I generally do my upgrades & such through the terminal so I have tried turn off through GUI & various shutdown terminal codes: pretty sure that using "poweroff" instead of "reboot" or "shutdown" is not going to solve my shut down issue (I've been wrong before though, so... ).

---

### Post by spencer2 on 2017-10-30
cancel this: I solved it. For whatever its worth, I ran:

```
-Aspire-F5-571T:~$ sudo dpkg-reconfigure resolvconf
```

clicked through the scary purple pop-up questions, restarted & now I'm connecting & surfing regardless of whether PIA is connected or not. If any of that helps others, good deal.

---

