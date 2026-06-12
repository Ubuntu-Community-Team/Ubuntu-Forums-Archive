---
title: "Modem Error :("
date: 2006-09-22
forum: Networking &amp; Wireless
---

### Post by jalanbuntu on 2006-09-22
Could someone please help me to get my modem works?
I've follow the instruction from [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
I've succesful on installing my modem. At first I thought it works, because my modem can dial out and I hear the dialing sound. But every time I try to dial using gnome-ppp or wvdial, it will always stuck with No Carrier problem. Below is wvdial messages when I try to dial,

```
--> WvDial: Internet dialer version 1.55
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT080989999
--> Waiting for carrier.
ATDT080989999
--> Timed out while dialing.  Trying again.
--> Sending: ATDT080989999
--> Waiting for carrier.
NO CARRIER
ATDT080989999
--> No Carrier!  Trying again.
--> Sending: ATDT080989999
--> Waiting for carrier.
NO CARRIER
```

I've add "No Carrier" and "Stupid Mode" setting on the configuration, but it still error :(

Could someone please help me? Thanx before

---

### Post by whizbaby on 2006-09-22
Not sure if this is right, but I think the *carrier* is the provider's computer answering the call to let you authenticate. Are you sure
-the number is right (perhaps try another provider for a single dialin)
-the provider still exists?

---

### Post by jalanbuntu on 2006-09-23
> **whizbaby said:**
> Not sure if this is right, but I think the *carrier* is the provider's computer answering the call to let you authenticate. Are you sure
-the number is right (perhaps try another provider for a single dialin)
-the provider still exists?

Yep, I'm sure either the number is right and the provider still exist. Because I can dial out with same account using another computer. Actually, that's the way I can post to this thread with my current laptop (Ubuntu Dapper). I dialout using another computer (Windows OS) and share the connection to my laptop.

I've been search through this forum and try to get the modem works, but still failed :(

---

