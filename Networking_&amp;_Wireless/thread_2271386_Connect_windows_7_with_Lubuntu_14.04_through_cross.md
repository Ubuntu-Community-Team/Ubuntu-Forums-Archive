---
title: "Connect windows 7 with Lubuntu 14.04 through crossover"
date: 2015-03-29
forum: Networking &amp; Wireless
---

### Post by soprano2 on 2015-03-29
hello,

I use the Lubuntu 14.04 and i can´t connect my window 7 with my pc (Lubuntu 14.04) through crossover. How i configure both pc for i can connect with my folder samba in Lubuntu through my windows 7?

Thanks us,
soprano

---

### Post by Vladlenin5000 on 2015-03-29
Hello and welcome.

First of all Crossover is just a sophisticated and proprietary implementation of WINE and, like WINE, its sole purpose is to be able to run (acceptably) (some) Windows software in Linux.
It has NOTHING to do with what you want to do, network shares between Windows and Ubuntu.

Start be telling us exactly what do intend to do, then we might come up with a good and easy solution.

---

### Post by soprano2 on 2015-03-29
Ok,
First thanks your reply :)


I need transfer many archives the windows 7 to linux. I configure the samba and i can access file samba through normally network. But i plug cable crossover the problems appear...


Sorry my english, i study!
thanks,

---

### Post by Vladlenin5000 on 2015-03-29
So, you mean a crossover Ethernet cable, not the Codeweavers Crossover software?

---

### Post by soprano2 on 2015-03-29
Yes, a crossover Ethernet cable!

---

### Post by Icetoad on 2015-03-30
Hi [**[COLOR=#000000]soprano2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1976617"),



Try giving this a read:
[http://www.howtogeek.com/176471/how-to-share-files-between-windows-and-linux/](http://www.howtogeek.com/176471/how-to-share-files-between-windows-and-linux/)

---

### Post by soprano2 on 2015-03-30
yes, the share with samba i know, but i dont know how connect two pc´s with cable crossover! I want connect two pc with cable crossover and transfer archives for file samba in ubuntu pc!

Thanks,
soprano

---

### Post by Icetoad on 2015-03-30
What is the exact problem you are facing?

Do you think this can help you:
[http://www.ehow.com/how_7208875_connect-ubuntu-windows-crossover-cable.html](http://www.ehow.com/how_7208875_connect-ubuntu-windows-crossover-cable.html)

---

### Post by soprano2 on 2015-03-30
when I plug de cable crossover and execute ifconfig in terminal the message the return is:


etho Link encap: Ethernet HWaddr 00:27:0e:00:f3:90
UP BROADCAST MULTICAST MTU:1500 Metric:1
...


I haven´t ip in eth0, why?
I choose option "share between pc" in network specifies (i don't remember exactly the name of definition). When I plug the cable i havent´t ip in eth0, why?
It is mandatory to set the IP on the plates or the possibility exists that the PC automatically set an IP. In this way it would be easier ...

thanks,
soprano

---

### Post by Icetoad on 2015-03-30
You must set the IP manually in this scenario.

It is possible to obtain IP address automatiacally, but one of the systems must be running DHCP which can assign the IP address to the other machines connected to it.
Kindly follow the instructions given in the link and see if it solves your problem.

---

### Post by soprano2 on 2015-04-03
Hello,


I did the instruction in "http://www.ehow.com/how_7208875_connect-ubuntu-windows-crossover-cable.html" and i can connect two pc for a few seconds but after some of minuts the connection it is off-line. Have to go back to run command "ifconfig eth0 192.168.1.2 netmask 255.255.255.0 up".


Why does this happen?


thanks,
soprano

---

### Post by changingstate on 2015-04-03
Have you stopped the network manager service?

---

### Post by soprano2 on 2015-04-04
> **changingstate said:**
> Have you stopped the network manager service?

I think not, at least not done anything to it.
This is just install Lubuntu

Thanks,

---

### Post by changingstate on 2015-04-05
```
sudo service network-manager stop
```

Try again.

---

