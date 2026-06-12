---
title: "Not Able To connect to the net"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by AKPAKP on 2008-03-29
I'mm not able to connect to the net please help me

I have a external ADSL modem which i'm using with XP to connect ...please help me connect to the net via Ubunt 

Any help is appreciated

---

### Post by fourthofjuly on 2008-03-29
> **AKPAKP said:**
> I'mm not able to connect to the net please help me

I have a external ADSL modem which i'm using with XP to connect ...please help me connect to the net via Ubunt 

Any help is appreciated
which internet service provider are you using?

how do you connect in XP?

---

### Post by AKPAKP on 2008-03-29
BSNL Bradband
connect the lan first then the pppoe connection

---

### Post by fourthofjuly on 2008-03-29
> **AKPAKP said:**
> BSNL Bradband
connect the lan first then the pppoe connection
ok, i guess you may be having your phone line connect to the BSNL modem and a separate cable from the modem goes to your LAN card?

---

### Post by AKPAKP on 2008-03-29
The phone line gets split one goes to the phone & other to the modem...ome wire from the modem goes to the port in the back side of the PC...

internet connection doesnot block my phone ..both can work simultaneously

---

### Post by fourthofjuly on 2008-03-29
> **AKPAKP said:**
> The phone line gets split one goes to the phone & other to the modem...ome wire from the modem goes to the port in the back side of the PC...

internet connection doesnot block my phone ..both can work simultaneously
ok, go to System > Administration > Network

enter your pwd

under connections, check the wired connection, go to properties,

under connection settings select static IP address, 

IP address may be 192.168.1,2 

subnet mask is 255.255.255.0 and gateway will be 192.168.1.1 (or whatever you have in XP)

click OK and under DNS tab add 61.1.97.69 and 61.1.97.71 (or whatever you have in XP) as DNS servers

reboot

---

### Post by AKPAKP on 2008-03-29
done....now

---

### Post by fourthofjuly on 2008-03-29
system > administration > network tools > ping tab

in network address type the BSNL gateway address and ping

if you receive something like "reply from 192.168.1.1" etc., you can start surfing...

---

### Post by AKPAKP on 2008-03-29
what is the bsnl gateway address

---

### Post by AKPAKP on 2008-03-29
i just now using terminal pinged a random ip addr. 192.168.1.76

& got the mssg host unreachable....

---

### Post by fourthofjuly on 2008-03-29
i guess its 192.168.1.1 or whatever you entered earlier

---

