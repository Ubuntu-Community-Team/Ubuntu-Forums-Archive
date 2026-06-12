---
title: "DNS settings keep changing"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by PaulFXH on 2007-08-02
One of our computers on the home network (Ubuntu) is set to DHCP for the internet connection.
My experience is that I must specify the DNS servers in the network Settings dialog box to get a good browsing performance.
However, this setting is continually re-setting itself back to the router address (192.168.1.254) which dramatically reduces browsing speed (at times it is almost unusable).
Once I reset the DNS servers back to the two addresses provided by the ISP, everything is back to normal -- but only for a few seconds until the settings go back to the router address.

Now, download speeds on this computer are just as fast as on the other computers on this network. This seems to show that the problem is totally associated with very slow DNS performance.

According to the ISP, there should not be a need with DHCP to specify the DNS servers. Well, that's the theory but the practice is annoyingly different.
Any idea what I might do to keep my browsing speed high?

---

### Post by spd106 on 2007-08-02
There is a setting in the /etc/dhcp3/dhclient.conf file that allows you to append dns servers to the list during the dhcp process and won't get overwritten. 

Some people recommend opendns instead of your ISP, there is also this [list ]("http://ubuntuforums.org/showthread.php?p=2000014#post2000014").

---

### Post by PaulFXH on 2007-08-02
Thanks for the reply. This sounds promising.
Can you please confirm for me how the DNS addresses are to be appended to the dhclient.conf file.
Is it as "Option domain-name-servers xxx.xxx.xxx.xxx;yyy.yyy.yyy.yyy"?
Thanks
Paul

---

### Post by spd106 on 2007-08-03
Not really, as it sounds like you want to prioritise the dns server you supply use the prepend statement, otherwise use the append statement. You can have multiple comma separated addresses on the same line. 

e.g.
```

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
[COLOR="Red"]prepend domain-name-servers 192.168.2.1, 10.0.0.101;[/COLOR]
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;

```

If you don't want to receive a dns server from dhcp at all then you can remove the option from the request statement.

There are several other threads on this topic, here is one such example. [http://ubuntuforums.org/showthread.php?t=290788](http://ubuntuforums.org/showthread.php?t=290788)

---

