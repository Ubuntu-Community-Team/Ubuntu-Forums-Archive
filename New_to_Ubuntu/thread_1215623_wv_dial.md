---
title: "wv dial"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by Shubhang on 2009-07-17
how do i install wv dial. Pse help. am absolutely new to linux. Thanks

---

### Post by rampageoberon on 2009-07-17
> **Shubhang said:**
> how do i install wv dial. Pse help. am absolutely new to linux. Thanks

Hi there, The below code in a terminal will install wvdial.

```
sudo aptitude install wvdial
```

Alternately you can go to System -> Administration -> Synaptic and install from there.

---

### Post by Shubhang on 2009-07-17
Thanks a lot that helped. Next is to install tata indicom dialer. if u could help. thanks

---

### Post by rampageoberon on 2009-07-17
> **Shubhang said:**
> Thanks a lot that helped. Next is to install tata indicom dialer. if u could help. thanks

I'm not sure what the parameters will be for the tatacom device. I take a guess that this is a 3G Huawei device. This is what I used to use on the 3G device that I used. (You can get this info from your provider or from the data stored on the device)

```
[Dialer Pin]
Init1 = AT+CPIN=YOURPIN
Modem = /dev/ttyUSB0
Baud = 9600

[Dialer Connect]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = PHONENUMBER
Modem = /dev/ttyUSB0
Username = YOURUSERNAME
Password = YOURPASSWORD
Baud = 9600
Dial Command = ATDT
Stupid Mode = 1
```

---

### Post by Shubhang on 2009-07-17
That right its a 3g device. Would be greatful if u could tell me what excatly is to be done with the codes u sent

---

