---
title: "RDP from Internet to both a windows AND a linux pc (ubuntu)"
date: 2014-02-11
forum: Networking &amp; Wireless
---

### Post by Giovanni_Stoto on 2014-02-11
I am connected to Internet via ADSL.

I have 2 PCs: a Dell laptop with Windows 7 and a Samsung Netbook with Linux Mint 16 MATE

I also have a 3rd laptop I use for testing the remote connection: this laptop can be connected either on the same home LAN (that is on the router) or to the internet (by using a wifi connection to the neighbor's wifi adsl router).

I managed to correctly configure the Win PC for remote desktop, either from the same Lan at home or from Internet.
What I did was to set a static IP for the Win PC, on the router forward port 3389 to this static IP, get a host name xxx.dlinkddns.com from dyndns (configured with the public address of the router), configure dns service on the router.

No rocket science... All is working fine: the 3rd laptop can rdp to the Win pc either when on the same lan (using the static ip address) or from Internet (using the xxx.dlinkddns.com host name). No need to specify any port in the rdp connection as I am using the standard 3389 port (correctly forwarded on the router).

I want now to do the same exact thing for the Linux netbook.
I set a static ip for the Linux pc (different from the Win pc). I installed tightvncserver and then xrdp. I forwarded port 5900 on the ruter to the static ip of the Linx pc.

The xrdp.ini file looks like this


```
[globals]
bitmap_cache=yes
bitmap_compression=yes
port=3389
crypt_level=low
channel_code=1
max_bpp=24
#black=000000
#grey=d6d3ce
#dark_grey=808080
#blue=08246b
#dark_blue=08246b
#white=ffffff
#red=ff0000
#green=00ff00
#background=626c72

[xrdp1]
name=sesman-Xvnc
lib=libvnc.so
username=ask
password=ask
ip=127.0.0.1
port=-1

[xrdp2]
name=console
lib=libvnc.so
ip=127.0.0.1
port=5900
username=na
vpassword=ask

[xrdp3]
name=vnc-any
lib=libvnc.so
ip=ask
port=ask5900
username=na
password=ask

[xrdp4]
name=sesman-any
lib=libvnc.so
ip=ask
port=-1
username=ask
password=ask

[xrdp5]
name=rdp-any
lib=librdp.so
ip=ask
port=ask3389

[xrdp6]
name=freerdp-any
lib=libxrdpfreerdp1.so
ip=ask
port=ask3389
username=ask
password=ask

[xrdp7]
name=sesman-X11rdp
lib=libxup.so
username=ask
password=ask
ip=127.0.0.1
port=-1
xserverbpp=24
```


Now... using my 3rd pc I can rdp to the Linux netbook when connected on the same LAN by using the static ip of the Linuc pc...

... BUT ...

how do I connect to the Linux netbook from Internet? I cannot use xxx.dlinkddns.com as this leads me to the Win pc.

Am I missing something? I thought that maybe I need a second host name in dlinkddns, but this makes no sense, as this is configured on the public address of the router, and on the router you can configure only one ddns service.

I tried appending port 5900 to the host name (xxx.dlinkddns.com:5900) but this gives me a connection refused.

Thanks for any help
thegios

---

### Post by Giovanni_Stoto on 2014-02-12
Am I the only one not getting an answer here? o.O

Ayhow, I solved the problem by myself, as I understood that the port to be changed was the one under [globals] and not under [xrdp1] so the xrdp.ini now looks like this

[globals]
bitmap_cache=yes
bitmap_compression=yes
port=3390
crypt_level=low
channel_code=1
max_bpp=24

[xrdp1]
name=sesman-Xvnc
lib=libvnc.so
username=ask
password=ask
ip=127.0.0.1
port=-1


whete I set the port to 3390, different from the default 3389 used by my Windows pc. Now I can rdp to the linux pc using

xxx.dlinkddns.com:3390

Still I have a small problem: when I connevt it seems I create a new session: as a matter of fact I get a new empty desktop and, weird enough, I have a chrome window opening on the linux machine.

How can I make sure I connect to the same open session and see the same applications running? I tried what is suggested somewhere here and on other blogs: set under [xrdp1] section the port to 5901 instead of -1, but in doing so I get a connection refused.

---

