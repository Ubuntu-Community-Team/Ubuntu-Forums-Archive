---
title: "smtp sniffer"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by rosegal on 2009-12-02
sniffex is a source code used to capture tcp/ip packets, can it be used to capture smtp protocol? if yes, can i use the original code or must i modify it to capture smtp protocol? i dont know how to modify sniffex.c ...Please i need help in this area..thanks..

---

### Post by andrewc6l on 2009-12-02
I'm guessing you could use it to look at SMTP. You might want to install Wireshark instead (apt-get install wireshark, I think) - that application can monitor a lot (including SMTP, which is just TCP/IP over port 25) and has a fairly nice graphical view.

---

### Post by The Cog on 2009-12-02
Another vote for wireshark. It's brilliant! It's in the repositories so you can install it using Synaptic. 

To be able to capture packets, you have to run it as root. Press Alt-F2 and enter the command **gksu wireshark** which warns you that running as root is dangerous - ignore that warning.

---

### Post by freak42 on 2009-12-02
smtp is an app layer protocol that resides one level above tcp and actually uses tcp beneath it. so yes you can sniff smtp stuff with a tcp/ip sniffer

hth

---

### Post by rosegal on 2009-12-03
i m getting this message everytime i start to sniff...'' Couldn't get netmask for device eth0: eth0: no IPv4 address assigned '' i am using mobile broadband for net supply,does this cause the problem..How to solve this problem?

---

### Post by ukripper on 2009-12-03
post output of belwo command:
```
iwconfig
```

need to check which interface is active.

---

### Post by rosegal on 2009-12-26
hi there...i m using a broadband connection,and my active interface is ppp0..i have tried assigning ip address since i always receive the message as above saying thr is no ipv4 assigned..after running sniffex again,the above msg didnt appear but i cant sniff anything though...why is it so?anyone with the answer?...thanks...

---

