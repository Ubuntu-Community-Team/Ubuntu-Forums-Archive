---
title: "ubuntu: configure adsl access"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by okoloko on 2010-05-18
Hi, Im trying to configure ubuntu 9.10 for adsl access. In windows I did this using internet explorer "Tools/Internet Options/Connections/Lan Settings/Address", which is [http://adslproxy.sun.ac.za/igmproxy.pac](http://adslproxy.sun.ac.za/igmproxy.pac). Please how can I do this in ubuntu?
 
Thanks in advance.
Inno.

---

### Post by HereInOz on 2010-05-18
Sounds like you want to set up a proxy server.

Easiest way is to go to System > Preferences > Network Proxy, and set the proxy server in there.

Then you need to check in Firefox that it is set to use the system proxy settings - Open Firefox > Edit > Preferences > Advanced > Network > Settings and make sure that Firefox is set to use system proxy settings.

---

### Post by _0R10N on 2010-05-18
If what you want is to just set up an ADSL connection, you can configure it from the DSL connection tab on your Network Manager window.

---

### Post by 3rdalbum on 2010-05-18
Most ADSL modems in the English-speaking world will connect and maintain a connection without any intervention from your computer. As a result you don't use the operating system to configure the connection, you just plug the computer into the modem and you can immediately start surfing.

This sounds like a dumb question, but have you tried just plugging the Ethernet cable into your computer? If it says you're connected but you can't get to any sites, try: [http://www.chrislees.info/ubuntu/opendns.shtml]("http://www.chrislees.info/ubuntu/opendns.shtml")

---

