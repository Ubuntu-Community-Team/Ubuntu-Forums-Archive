---
title: "I want to hide/masquerade my IP address"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by fonggiding on 2007-08-20
I don't know if this is possible. But the quickest way to find out if it is or not is to ask you guys(and girls).
I live in Japan now and have a Japanese IP(naturally) 192.168.1.104 or so. But i get the message,'This service is only available for people in the United States'.
Is there anyway to "trick" it into thinking I am in the US now? I know for instance that with Icewealsel(it's a firefox plugin) I use it to pretend it is IE(shuttering). So What do you think?

---

### Post by lloyd_b on 2007-08-21
Do a google search on "Open Proxy" - such proxies hide your actual IP address (the systems you connect to only see the IP address of the proxy, not your IP address).

You'll need to configure your web browser (or whatever software you're using) to use the proxy instead of connecting to the server directly.

Lloyd B.

---

### Post by netztier on 2007-08-21
> **fonggiding said:**
> I don't know if this is possible. But the quickest way to find out if it is or not is to ask you guys(and girls).
I live in Japan now and have a Japanese IP(naturally) 192.168.1.104 or so. 

This is not a "japanese" IP address, this is an IP address for a "private Internet" as per [RFC1918]("ftp://ftp.rfc-editor.org/in-notes/rfc1918.txt"), from which:

```
3. Private Address Space

   The Internet Assigned Numbers Authority (IANA) has reserved the
   following three blocks of the IP address space for private internets:

     10.0.0.0        -   10.255.255.255  (10/8 prefix)
     172.16.0.0      -   172.31.255.255  (172.16/12 prefix)
     192.168.0.0     -   192.168.255.255 (192.168/16 prefix)

```

So it's probably the address that the DHCP server in your broadband router gave you - to the outside world, it will have a completely different "public" IP address and will already "hide" your internal LAN address (192.168.1.x) behind that public address.

lloyd_b is right, you need some form of external proxy service. Your web browser (or whatever application you're trying to use) will need to send the request to that proxy server which whill then in turn forward your request (using it's own IP address) to the server/service you intend to contact.

best regards

Marc

---

### Post by CowzRule on 2007-08-21
If you're referring to blocking you ip while using peer 2 peer stuff i.e. bittorrent, then have a look at
[http://ubuntuforums.org/showthread.php?t=192559]("http://ubuntuforums.org/showthread.php?t=192559")

---

### Post by fonggiding on 2007-08-21
External proxy huh. Thanks a lot!!! I'll check it out.

Gee, I need to set a side some time to read up about the internet etc.. Thanks for teaching me about ips netztier, Apparently my ip is:
Your IP: 219.160.159.254
Country: (JP) JAPAN 
&#12394;&#12427;&#12411;&#12393;&#65281;

Thanks again!

---

