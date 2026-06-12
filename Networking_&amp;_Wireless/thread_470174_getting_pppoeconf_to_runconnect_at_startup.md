---
title: "getting pppoeconf to run/connect at startup"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by Adam590 on 2007-06-10
Through help I've found in the forums, and particularly [[COLOR="Blue"]in this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=187466"), I was able to get my ADSL connection working using pppoeconf. Going through the GUI every time I reboot is a fairly tedious process, so I'm wondering if there is any way to automate it.

Here's what I'm currently doing to connect:


(open a terminal)

sudo pppoeconf
(enter password)

(after the pppoeconf GUI is launched: manually entering only my network password since the username is saved, and otherwise hitting Enter a bunch of times until the GUI closes)

sudo pkill -9 dhclient       <-- *a must, since otherwise my connection drops after a minute or so*
pon dsl-provider

(close terminal)


Then I'm online and stable for the duration. Is there any way to automate this process, or to create/alter some file so that I can at least avoid the pppoeconf GUI?

Thanks.

---

### Post by bilbarra on 2007-06-11
man, i have the same problem, i used some previous releases of ubuntu and all have the same problem this is the one of worst thinks of ubuntu and they never corect, 
[B]
i get this in workaround:[/B]
sudo gedit /etc/network/interfaces

in the end of the file has something like this:
pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf


move that line up like this:
pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf 
auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

hope that work ;)

---

### Post by Adam590 on 2007-06-12
Thanks for the suggestion!

I gave it a shot, but I can't tell that it made any difference - I still have to go through the steps I mentioned before. What effect does it have for you?

---

### Post by rostfrei on 2007-06-13
This solution does not work for me. There is no change and PPPoE still doesn not start on boot, but manually it does. What else can I do?

Best regards,

---

### Post by DoruHush on 2007-06-14
> **bilbarra said:**
> 
pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf

     In that line eth1 should be ethn where n is your network card.If you only have one then **n** should be 0 and ethn become **eth0**.
     So for only one network card on your system the line should look something like that:
```
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
```.
    It might work.:o

---

