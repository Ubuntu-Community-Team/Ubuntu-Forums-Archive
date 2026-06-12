---
title: "broad band probs"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by navaneethan on 2010-02-18
After installing my ubuntu 9.10 i created my broadband adsl account using the command sudo pppoeconf..
Then i supposed to connect to my friend's broadband which is a dsl connection but i cant connect with it.. even modem is not detecting in the first step of sudo pppoeconf...

---

### Post by dineshs on 2010-02-18
What is the modem IP ?Is it DHCP enabled ? Do you know your broadband username and password? Then better program your modem for an always on connection.If you tell me the make and model of your modem perhaps I can help

---

### Post by navaneethan on 2010-02-18
ya..i am having the username and password DHCP enabled

the problem is after installed the os i configured the broadband for my modem and after it needs to be configured for my friend but i couldn't able to do it for him...how to edit the configuration?? or how to reconfigure for my friend's one

---

### Post by dineshs on 2010-02-18
Normal modems have the IP 192.168.1.1 by default(you can also try 192.168.1.254).So open firefox and type 192.168.1.1 in the address bar.It will ask for a username and password.type admin for both,then enter.Now you can configure your modem.The following link has different modem configurations.
[http://ernakulam.sancharnet.in/ernakulam/bbservice.html](http://ernakulam.sancharnet.in/ernakulam/bbservice.html))
This method allows always on internet and you dont need commands like pppoeconf or pon dsl-provider etc

---

