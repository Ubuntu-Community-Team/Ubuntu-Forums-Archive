---
title: "[SOLVED] Nagios: check_snmp"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by ghemeon on 2008-06-19
Just installed Nagios and want to use check_snmp

I did a apt get net-snmp install and it worked fine
Yet the snmp is still not working

From reading it says I need to get net-snmp-utils .. where do i get this from?

---

### Post by tcpip4lyfe on 2008-06-19
Try this article:
[http://www.debuntu.org/how-to-monitor-your-servers-with-snmp-and-cacti](http://www.debuntu.org/how-to-monitor-your-servers-with-snmp-and-cacti)

This is one I used when I setup all mine. It's a hell of a lot easier then using snmpconf.  On a side note after you get your nagios setup, check out cacti.  I use nagios and cacti to monitor about 20 servers and a couple routers and switches and it works great.

---

### Post by ghemeon on 2008-06-19
worked .. thanks

---

### Post by ning_ning on 2008-06-27
> **tcpip4lyfe said:**
> Try this article:
[http://www.debuntu.org/how-to-monitor-your-servers-with-snmp-and-cacti](http://www.debuntu.org/how-to-monitor-your-servers-with-snmp-and-cacti)

This is one I used when I setup all mine. It's a hell of a lot easier then using snmpconf.  On a side note after you get your nagios setup, check out cacti.  I use nagios and cacti to monitor about 20 servers and a couple routers and switches and it works great.

how to know snmp server is running ?

---

### Post by tcpip4lyfe on 2008-07-08
> **ning_ning said:**
> how to know snmp server is running ?

snmpwalk -v 2c -c public localhost

---

### Post by vixo12 on 2009-02-17
Friends:

Hello, i am from Santiago of Chile, I would like to implement Nagios snmp. I already have Nagios installed, but where in the plugin check_snmp? What do you like? and What else do you need?

please you help

thank you!!!:p

---

### Post by ikki_72 on 2009-08-29
> **vixo12 said:**
> Friends:

Hello, i am from Santiago of Chile, I would like to implement Nagios snmp. I already have Nagios installed, but where in the plugin check_snmp? What do you like? and What else do you need?

please you help

thank you!!!:p

Make sure nagios-snmp-plugins is installed and it is usually located in /usr/lib/nagios/plugins

---

### Post by Jago6060 on 2009-09-05
> **ikki_72 said:**
> Make sure nagios-snmp-plugins is installed and it is usually located in /usr/lib/nagios/plugins

Or if you're using a 3.x version of nagios, they're in /usr/local/nagios/libexec

---

### Post by snyper82 on 2009-10-02
I'm missing the check_snmp plug-in, I have installed the nagios plug-ins 1.4.14, anyone know how to install this plug-in?
I also have nagios 3.2 installed

---

### Post by Jago6060 on 2009-10-02
> **snyper82 said:**
> I'm missing the check_snmp plug-in, I have installed the nagios plug-ins 1.4.14, anyone know how to install this plug-in?
I also have nagios 3.2 installed

You should have check_snmp with the default compile.  If not, you can google "check_snmp" and probably download it, then recompile the plugins

---

