---
title: "Cannot reach router configuration page netgear wifi"
date: 2015-07-29
forum: Networking &amp; Wireless
---

### Post by coljohnhannibalsmith on 2015-07-29
Hello,

I have a NETGEAR wireless router, that is already configured and working. After I established a
wireless connection I tried to reach the router configuration page by typing [http://www.routerlogin.net](http://www.routerlogin.net),
which is the website listed on the back of the router and I couldn't connect. I also tried typing in
the default gateway, which is [http://192.168.0.1](http://192.168.0.1).  This did not work either.  Following the advice
in the follow article [http://www.wikihow.com/Access-a-Router](http://www.wikihow.com/Access-a-Router) I performed a factory reset and a
power-up reset, neither of which worked.  I have in the past been able to login to the config page
with ease.  I don't know why I can't login now. I am running an APACHE server; perhaps this is in
conflict with my login attempts.  Any help appreciated.

Thanks, Hannibal

---

### Post by TheFu on 2015-07-29
The netgear router at the coffee shop here uses 192.168.1.1.
The only way there would be an issue is if you've accidentally setup the static IP for the Linux machine to be identical to that for the router/gateway.

---

### Post by coljohnhannibalsmith on 2015-07-29
No.  I didn't do that.  I simply ran the code to download and configure the entire LAMP stack.
It was very easy. MySQL and PHP were installed without any user intervention, with the exception
of having to enter an admin password.  On one of my login attempts however, the LAMP test
page came up; so I think this may be part of my problem.

What code can I execute to kill the Apache server?

Thanks, Hannibal

---

### Post by TheFu on 2015-07-29
Teaching you to fish ... based on the last question:
* [https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/)
* [http://linuxcommand.org/lc3_learning_the_shell.php](http://linuxcommand.org/lc3_learning_the_shell.php)

---

### Post by coljohnhannibalsmith on 2015-07-29
Ok, got it:

```
sophie@sophie-Inspiron-1545:~$ sudo service apache2 stop
[sudo] password for sophie: 
 * Stopping web server apache2                                                   * 
sophie@sophie-Inspiron-1545:~$ 

```

It still doesn't work.  I'm trying to connect over the WiFi.  Is this correct?

---

### Post by coljohnhannibalsmith on 2015-07-29
Well, I finally broke down and went to the NETGEAR support page.  It appears that my router has an EtherNet pass-through
and must be connected in this way for proper operation.  I was trying to connect to the router through the WiFi instead.
With the pc connected to one of the pass-through ports, I'm able to reach the web server in the router.  Live and learn.

Thanks, Hannibal

---

