---
title: "Network Services Run Very Slowly"
date: 2005-08-15
forum: Networking &amp; Wireless
---

### Post by Freddie on 2005-08-15
Hi! I have just installed ubuntu on an old iMac of mine. Everything seems to work fine, except some network services (e.g. webmin and ftp). The go slowly, there will no network activity for around 20 seconds and then a 'burst' (when I was sending/getting files from my ftp server it was up to 5Mb/s). On the computer I am able to browse the web and download files without problems. These problems happen both via lan and the internet. All of my computers are connected to a router and I left it up to DHCP to configure my network for me. It is not my router, as if I turn on ftp sharing on my laptop (Mac OS X) and send a load of junk its way I get constant speeds of 1Mb/s). Does anyone know what is causing this and what I can do to fix this?

---

### Post by heimo on 2005-08-15
This is just a faint guess, but it's best to rule out the possiblity that this is caused by ipv6 - some people are experiencing problems with it (mostly I've seen it related to browsing internet, but who knows).

[http://www.ubuntuforums.org/showpost.php?p=300758&postcount=2]("http://www.ubuntuforums.org/showpost.php?p=300758&postcount=2")
You need to restart after this change.

---

### Post by Freddie on 2005-08-15
I have done that change and will reboot in a min. But I think that it might be a DNS problem, as when I was trying to set up my mail server on my XP box I had to manually add the DNS servers (normally it uses the router for dns, it is not a dns server just acts as one). Something to do with hostnames if I remember correctly. Could this be the same problem?

---

### Post by heimo on 2005-08-15
[QUOTE=Freddie]I have done that change and will reboot in a min. But I think that it might be a DNS problem, as when I was trying to set up my mail server on my XP box I had to manually add the DNS servers (normally it uses the router for dns, it is not a dns server just acts as one). Something to do with hostnames if I remember correctly. Could this be the same problem?[/QUOTE]

Yes, I recall that some people on these forums had problems with /etc/resolv.conf. In that file, you should have your ISPs nameservers (or what ever nameservers you use) listed. For syntax, check man resolv.conf - I believe it's just 
 ```
nameserver ip-address-here
```
Worth checking. You should be able to do same change from network settings in Gnome.

---

### Post by Freddie on 2005-08-15
I did both of thoise things and it is still no better. By the time the main webmin page has loaded (with images) I can have: go to the ubuntu forums, logged in, searched for my topic and be writing a reply beofre it has loaded. I just dont understand it one bit, by does it burst it? (I have rebooted after making the changes). It is unaccptably slow, to the point where it is unuseable. Someone has said that I need to add my networked computers to my hosts file, by I dont understand all the info that I will need for this, I have not tried it from the internet yet (you can test my webmin at [http://84.92.106.157:10000](http://84.92.106.157:10000) I can not test it internally, but tell me how long the logon page takes to load if you could be so kind). Can anyone help me?

I asked my friend to test webmin remotely and he said that it loaded like any other webpage, very quickly (not like the 2 min I get). So it is only an internal problem.

---

