---
title: "CA Certificate for public Wi-Fi?"
date: 2013-09-23
forum: Networking &amp; Wireless
---

### Post by Lucas_Fiorella on 2013-09-23
Google hasn't helped me much, I'm trying to access my University's wireless network but it seems to require a certificate. I don't know what certificate I need or how to use it. My University also supports eduroam but it's coverage is very limited.

Any info on how to connect on 12.04.3 LTS would be appreciated

---

### Post by varunendra on 2013-09-24
Welcome to the forums Lucas_Fiorella! :)

The CA Certificate is something supplied by the administration who controls the network. You should get it from your University's IT support or a similar authority. It is usually a .crt file that you save in the Security settings for the connection in Network Manager, as shown in the screenshot below -

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=246467[/IMG]

There is another case where the request for ca-cert can be disabled, but I'm not sure if it works always (the trick may fail, or the network may reject the connection attempt due to lack of the required certificate).

If you can't get the above certificate from authorities, or want to test the workaround anyway, open your connection's keyfile with root access -
```
gksu gedit /etc/NetworkManager/system-connections/<your connection name>
```
..and look for the line that says "**system-ca-certs=[COLOR="#FF0000"]true[/COLOR]**". Change the value from "true" to "**false**" > save > close. Now retry to connect and see if it lets you.

---

### Post by Rsxhawk on 2013-10-17
I recently connected to a wireless dot1x network using an ubuntu 12.04 laptop, but i changed my authentication drop down to Protected EAP (PEAP) since that's what the connection dictates to use.  I typed in my domain user credentials and clicked connect and was presented with an option to either select the CA cert from a file on my computer, OR i could choose to "ignore" and connect anyway.  I chose to ignore and it got me connected right away.  A quick glance at the syslog showed me receiving the certificate our domain controller was providing/pushing to users.  

If your University dictates that you must load the certificate manually I suppose that's fine if that's how the connection is set up, but I'm thinking they're pushing the cert via a Windows 2008 NPS domain policy like we did here.  I'd say verify the "Authentication" type with your IT admins and then try reconnecting and see what happens.

---

