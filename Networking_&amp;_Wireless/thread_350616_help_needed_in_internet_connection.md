---
title: "help needed in internet connection"
date: 2007-01-31
forum: Networking &amp; Wireless
---

### Post by sandeep_37 on 2007-01-31
i am new to ubunt and linux. My connection is DHCP is a protocol (pppoe). In windows i go to give my ID and password in [www.reliance.co.in](www.reliance.co.in) that i can acess the net. I need not set anything there . I have adsl modem and i also know ip address,subnet,gateway,DHCP,dns,wins values. so how i have to do that in ubuntu .

---

### Post by Floppyjoe on 2007-01-31
Are you connecting to the internet using a Router or directly with the DSL Modem?

---

### Post by sandeep_37 on 2007-02-01
adsl

---

### Post by mips on 2007-02-01
> **sandeep_37 said:**
> adsl
adsl what ? Router or Modem ?

Maye just give us the Brand & Model number, that would be easier.

---

### Post by tagginannie on 2007-02-01
> **mips said:**
> adsl what ? Router or Modem ?

Maye just give us the Brand & Model number, that would be easier.

And is it a USB or [SIZE=-1]Ethernet one? 

Suzy:KS
[/SIZE]

---

### Post by sandeep_37 on 2007-02-01
Ethernet ADSL modem site for that is [www.utstar.com](www.utstar.com) model is UT-300R2 ethernet adsl modem . I have to give user id and password in the [www.reliancebroadband.co.in](www.reliancebroadband.co.in) which will open itself without connecting to net . This is DHCP type  


I done this thing in ubunt see down.

any one help plzzzzzzzzzzzzzzzzzzzzzzzzzz

---

### Post by mips on 2007-02-02
Your best bet is to not use PPPoE on any of your PCs, windows included.

What you should do is to take your UT-300R2 out of *bridged* mode and in to *routed* mode.

This means you do not have to run any additional software on linux or windows (PPPoE). All you will have to do is configure your Ethernet for DHCP or Static IP.

The link you provided for reliance does not work for me.

If you want to do the above and reconfigure your router to work in this fashion let me know and I will help you do it.

We need some information though and your ISP can supply it:
1. VPI=?
2. VCI=?
3. Username=xxxx@yyyyy.zzz.xxx etc
4. Password= *****

Do NOT post 3&4 on the forums, only you need to know them.

---

### Post by sandeep_37 on 2007-02-02
There are only five protocol
1 ppp over ATM(pppoa)
2 ppp over ethernet(pppoe)
3 mac encapsulated routing(MER)
4 IP over ATM(IPOA)
5 Bridging

Now what you want me to do?

plz help me
VPI/VCI      Service              protocol  

0/32          br_0_32                  bridge
8/35          br_8_35                  bridge
0/35          br_0_35                  bridge
8/81           br_8_81                 bridge
14/24         br_14_24                bridge
0/100         br_0_100                bridge
0/33           br_0_33                  bridge
0/40           br_0_40                  bridge

---

### Post by mips on 2007-02-02
Contact your ISP and ask them what is the correct VPI/VCI information. Also ask them about the protocol but I suspect it would be pppoe or pppoa.

---

### Post by sandeep_37 on 2007-02-02
Ya this is pppoe type. i have user guide of ADSL modem ,in that VPI/VCI 0/32 for RFC1483 bridge configuration. see this [http://www.calcutta.bsnl.co.in/dataoneinstall/mu02.html](http://www.calcutta.bsnl.co.in/dataoneinstall/mu02.html)  
[http://www.digidataconnect.com/cust_premise/asdl_cpe.html](http://www.digidataconnect.com/cust_premise/asdl_cpe.html)
[http://www.utstar.com/Document_Library/0045.pdf](http://www.utstar.com/Document_Library/0045.pdf)
[http://www.utstar.com/Solutions/CPE/ADSL_CPE/](http://www.utstar.com/Solutions/CPE/ADSL_CPE/)

---

### Post by saigadu on 2007-11-22
Hey i'm using the same internet connection i.e., [http://www.reliancebroadband.co.in/](http://www.reliancebroadband.co.in/)

Please sort this problem out soon.

If this problem is already been solved, plz tell me procedure.

my email id is [email]dubbakasai@gmail.com[/email]:)

---

### Post by saigadu on 2007-12-22
Hey!!!!!!!!

The problem which was bothering is solved now!. All i did is i've disconnected the system and reconnected the network wire........that's it.......system has configured itself ;)

---

