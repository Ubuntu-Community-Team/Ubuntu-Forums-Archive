---
title: "Web Server"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by tonyoz on 2009-07-12
I'd like to create a TikiWiki box on my home network which I can then access externally from anywhere else in the world via the Internet. The TikiWiki box will sit behind a router on my LAN. TikiWiki is based on PHP 5 and Apache and MySQL 5 or higher which need to be installed and active prior to installing TikiWiki.

This raises a number of questions. Just wondering if there is an example scenario out there somwhere which takes people through this lot:

1. Any reason I can't use Ubuntu Desktop?

2. If using Ubuntu server can I install the Ubuntu Desktop on the Ubuntu server?

3. Is Webmin the easiest accepted way of doing GUI configuration of Apache?

4. Should I put the Ubuntu box in the router's DMZ to protect the other computers on the home LAN?

5. Should I make the LAN computers feed through to the Ubuntu box on one of two network adapters on the Ubuntu box and then use the other network adapter to connect the Ubuntu box to the ADSL2 modem/router? If so then the other LAN computers would access the Internet through the Ubuntu box.

6. Can I use the Ubuntu box for both TikiWiki and and as a Web server for my Website on the Internet? Presumably Apache would have to be able to deal with both TikiWiki and my website. Don't know if that is possible.

6. Presumably I should port forward something to somewhere?

7. Presumably phpMyAdmin is the accepted way to configure MySQL?

Regards.

---

### Post by indytim on 2009-07-12
See my LAMP server installation short paper for a painless way to install the same in a desktop environment.

[http://www.boomerclan.info/techpaperslx.html]("http://www.boomerclan.info/techpaperslx.html")

IndyTim

---

### Post by -=hazard=- on 2009-07-12
> **tonyoz said:**
> I'd like to create a TikiWiki box on my home network which I can then access externally from anywhere else in the world via the Internet. The TikiWiki box will sit behind a router on my LAN. TikiWiki is based on PHP 5 and Apache and MySQL 5 or higher which need to be installed and active prior to installing TikiWiki.

This raises a number of questions. Just wondering if there is an example scenario out there somwhere which takes people through this lot:

1. Any reason I can't use Ubuntu Desktop?

2. If using Ubuntu server can I install the Ubuntu Desktop on the Ubuntu server?

3. Is Webmin the easiest accepted way of doing GUI configuration of Apache?

4. Should I put the Ubuntu box in the router's DMZ to protect the other computers on the home LAN?

5. Should I make the LAN computers feed through to the Ubuntu box on one of two network adapters on the Ubuntu box and then use the other network adapter to connect the Ubuntu box to the ADSL2 modem/router? If so then the other LAN computers would access the Internet through the Ubuntu box.

6. Can I use the Ubuntu box for both TikiWiki and and as a Web server for my Website on the Internet? Presumably Apache would have to be able to deal with both TikiWiki and my website. Don't know if that is possible.

6. Presumably I should port forward something to somewhere?

7. Presumably phpMyAdmin is the accepted way to configure MySQL?

Regards.


There is no reason for not using ubuntu.

If using ubuntu server yes you can install a desktop envoirment after.

Yes webmin is a good gui and it have all options you need for apache.

Puting an os on DMZ (in general D-Link modems) means that aplications are free to open ports without you to open them from the router.

If you have a modem/router you can connect all the PC you want, it depends on the router capacity

I am not sure if you can use tikiwiki with apache too, never done it, but I gess so...

In general you dont need to portforward because port 80 even on routers stay open (only if you block it manually with a firewall)

You can configure mysql even from comand line but if you install webmin for apache, webmin can configure mysql too. If you are new on this I sugest you Webmin, is easier.

Cheerz

---

