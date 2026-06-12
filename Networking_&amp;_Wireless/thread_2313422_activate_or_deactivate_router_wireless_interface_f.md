---
title: "activate or deactivate router wireless interface from command line"
date: 2016-02-12
forum: Networking &amp; Wireless
---

### Post by alenis on 2016-02-12
I have a TP-LINK TD-W8968 ADSL modem-router. I would like to know if it is possible to activate and deactivate the wireless interface in the router (connected to the PC through an ethernet interface) through command line. At the moment I am able to access the modem router via telnet, but I don't know the commands required to activate/deactivate the interface.
Thanks
Alessandro

---

### Post by Nuno_Abreu on 2016-02-12
It should be this command if you want to disable wireless:
```
sudo ifconfig **wlan0** down
```

But beware: you better check the interface you want to deactivate (if different, substitute the words in **BOLD **in the previous line) by checking some info with this command:
```
ifconfig
```

---

### Post by alenis on 2016-02-12
Thanks. However, this commands acts on the wireless interface of the PC. What I want to do is activate/deactivate the wireless interface of the modem router connected through Ethernet to the PC.

---

### Post by Nuno_Abreu on 2016-02-12
> **alenis said:**
> Thanks. However, this commands acts on the wireless interface of the PC. What I want to do is activate/deactivate the wireless interface of the modem router connected through Ethernet to the PC.
It should be the same process - however, instead of the wireless interface, you should check out for the Ethernet one. But I'm confused - didn't you want to disable the wireless interface instead? Clarify this, please... I'm sorry if I'm being dumb at this point.
Anyway, I assume you should use this:
```
sudo ifconfig **eth0** down && sudo ifconfig **wlan0** up 
```

Feel free to ask any questions!

---

### Post by alenis on 2016-02-12
I would like to do, from the PC, the same that I can do, for example, pressing the WI-FI button on the modem/router. Normally, the modem/router wifi is off. If I want i t on, because, for example, I want to connect to the LAN with a smartphone to which I can't connect an Ethernet cable, I have to turn on the WI-FI on the modem/router. To do that, either I press the WI-FI button on the router, or I connect to the router through a browser, typing in the address of the router (which is 192.168.1.1). I found out that i can also connect to the router through telnet (typing in the command line telnet 11292.168.1.1). So I guess, but maybe I am wrong, that there is a way to activate the WI-FI in the modem/router through command line, e.g. 

telnet <address of the modem/touter> <command to turn wireless on>

But I wonder how to do that exactly.

---

### Post by Nuno_Abreu on 2016-02-12
OK, this one can be tricky! Anyway, what is the brand of the router you're using? I think it depends if the manufacters has software/firmware to allow this, though. The closest approach a colleague of mine got was with this:
[http://bit.ly/1SLBwbq](http://bit.ly/1SLBwbq)

---

### Post by alenis on 2016-02-12
My modem/router is a TP-LINK TD-W8968. I  know how to turn wifi on/off from the http interface. The problem is how to do it from command line, so that, for example, you can create a bash script and a cron job that turns wifi off at a certain hour. This discussion:
[http://stackoverflow.com/questions/5551344/let-telnet-execute-single-command-in-one-line]("http://stackoverflow.com/questions/5551344/let-telnet-execute-single-command-in-one-line")
probably solves how to send a telnet command in a bash script, but I still don't know what is the command to send. And I can't find any documentation in the TP-link site.

---

