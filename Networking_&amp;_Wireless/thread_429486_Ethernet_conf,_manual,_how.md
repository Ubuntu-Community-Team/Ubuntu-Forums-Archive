---
title: "Ethernet conf, manual, how?"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by merike on 2007-05-01
I used Edgy's alternate installer because the other one didn't work for me. Autoconfiguration at install failed. How do I configure it now? What should I check?

Already used ifconfig eth0 up and enabled connection.

Last time, when I used usual installer, it worked out-of-box. So I need to repeat whatever it does at install.

---

### Post by mojoman on 2007-05-01
> **merike said:**
> I used Edgy's alternate installer because the other one didn't work for me. Autoconfiguration at install failed. How do I configure it now? What should I check?

Already used ifconfig eth0 up and enabled connection.

Last time, when I used usual installer, it worked out-of-box. So I need to repeat whatever it does at install.

I'm not sure I get what you need to do but if you're just going to do the configuration you probably should have a look at the relevant files for this.

/etc/network/interfaces contains the basic iinformation such as IP, netmask etc. It can also be used to automatically launch the connection.

/etc/resolv contains your DNS servers.

Is this what you're after? If it is, and you need examples, let me know. Otherwise, you might need to give some more information.

On a side note, have you considered Feisty?

/mojoman

---

### Post by merike on 2007-05-01
I'm trying to get ethernet working, basically :). Usually installer configures regular stuff for ethernet to work. Last time when I installed that regular stuff was all I needed, after install ethernet just worked.
However this time installer failed to do that. And my ethernet doesn't work. It shows up in ifconfig and all, but I can't ping.
Those files you referenced, what are they supposed to contain?
I tried feisty week ago, some applications didn't work as expected so I went back to Edgy.
It would be great if someone could comment what installer does when it comes to wireless devices, since I need to get that working in the end as well.

---

### Post by mojoman on 2007-05-01
> **merike said:**
> I'm trying to get ethernet working, basically :). Usually installer configures regular stuff for ethernet to work. Last time when I installed that regular stuff was all I needed, after install ethernet just worked.
However this time installer failed to do that. And my ethernet doesn't work. It shows up in ifconfig and all, but I can't ping.
Those files you referenced, what are they supposed to contain?
I tried feisty week ago, some applications didn't work as expected so I went back to Edgy.
It would be great if someone could comment what installer does when it comes to wireless devices, since I need to get that working in the end as well.

Well, my /etc/network/interfaces contain this information:

```
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.0.4
netmask 255.255.255.0
gateway 192.168.0.1

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth0

```

Basically, the IP-address, netmask and gateway (I got static IP behing my router). It also states that eth0 (my primary connection) should be launced automagically on startup. 

My etc/resolv.conf looks like this:

```
search bredbandsbolaget.se
nameserver 81.26.228.3
nameserver 81.26.227.3
```

Try cat to have a look at the files in the terminal, i.e. 
```

cat /etc/network/interfaces
```

and
```

cat /etc/resolv.conf
```

If you need to edit them, just substitute cat with sudo and your favorite editor, e.g. 
```

sudo gedit /etc/resolv.conf

```

You should have the relevant information from your Internet Service Providor (ISP).

Get back if this doesn't work.

/mojoman

Edit: As far as wireless in concerned, it's pretty much the same but you also add some WEP-key or whatever else you use. I can get back with some examples of this too.

---

### Post by merike on 2007-05-04
Sorry for lack of response, university takes all my free time.

What my interfaces (without lines commented out) contain:
```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth0

iface dsl-provider inet ppp
provider dsl-provider
```

Shouldn't I have ath0 as wireless device aswell? I used to have ath0 and wifi0 in ifconfig.

And I don't have resolf.conf at all :O.

---

### Post by merike on 2007-05-04
Added resolv.conf and edited interfaces to have ath0 and wifi0. Ifupped both. I also have madwifi restricted drivers for 2.6.17.11. Installed wifi-radar and I'm able to see available networks.
However, when I double-click any one of them, nothing happens. In fact when I first open wifi-radar it shows disconnect button where should actually be connect button. Now what?

---

