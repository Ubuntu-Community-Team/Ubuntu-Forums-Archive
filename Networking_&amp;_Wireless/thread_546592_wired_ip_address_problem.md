---
title: "wired ip address problem"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by gishaust on 2007-09-09
Hi,

I have installed ubuntu 7.04 on to a stand alone machine. yesterday when I install ubuntu I was able to install all the updates. I then restarted the machine and surfed the net to see ubuntu in action and it worked fine. I turned the computer off and came back this morning. started the computer and tried the net again and can't get on. I have tried the following the get it to start,
-restarted the router
-looked at the router dhcp table and ubuntu was asigned a ip address
-restarted network connection on ubunutu (says that it is connected)
-ping router (unreachable host)
-sudo iptables -L(all information allowed through)
-sudo iptables -F worked fine


If I look at the ubuntuu  network information it says I don't ip-address but the router  says i have. 


can someone help me please.

Gishaust

---

### Post by gishaust on 2007-09-09
i have some more information

I went to the terminal window and changed the /etc/network/interfaces file to "iface eth0 inet dhcp"
then restarted by /etc/init.d/networking and stop and restart. still won't work

I ifconfig and I get V4 Broadcast running multcast where there should be an ip address from dhcp.


I then tried network tools and it won't respond.It asks for a forced quit. so I restarted and tried it again but all the same things happened.

---

### Post by helgman on 2007-09-09
Right, so ...

1) Your router says that an ip-address has been leased to your machines MAC-address?

2) And **ifconfig eth0** shows you no ip-address? (If so, have you tried **sudo dhclient eth0**?)

3) Do you have a line reading "auto eth0" above the "iface eth0 inet dhcp" line in */etc/network/interfaces*?

Helgman

---

### Post by gishaust on 2007-09-09
thanks for the reply

I have auto eth0 above yes. 
i just checked router and now there is no lease at all.
i just tried "ifdown eth0" and then "ifup eth0". The response was No working leases persisent database -sleeping

---

### Post by helgman on 2007-09-09
So the DHCP is not responding.

If you want to do this by the book, start with making sure that all cables are connected where they should be and that all light that should show some sort of connection shows some sort of connection.

Check that the DHCP-server has available addresses in it's pool (if it's a home router it should have, but you never know).

And if all this checks out, have you tried assigning the address manually just to make sure that you can reach the DHCP-server?

Helgman

---

### Post by gishaust on 2007-09-09
helgman thankyou for your help

It's fix but i am stupid.The router light was showing but when I changed the cable between the ubuntu machine and the router box i got Ip address straight away. So the cable was doing enough to show the light up on the router but was not working. Sorry to waist your time. First rule "work backwards".

Gishaust

---

### Post by helgman on 2007-09-09
No waste of time!

Glad it worked!

Helgman

---

