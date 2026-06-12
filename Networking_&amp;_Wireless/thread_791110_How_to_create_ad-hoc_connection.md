---
title: "How to create ad-hoc connection?"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by vitorgatti on 2008-05-11
The command **iwconfig ath0 mode Ad-Hoc** returns:
```
root@dragon:/# iwconfig ath0 mode Ad-Hoc
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Invalid argument.
```

And the command **iwlist ath0 event** returns:
```
ath0      Wireless Events supported :
          0x8B04 : Set Frequency/Channel (kernel generated)
          0x8B06 : Set Mode (kernel generated)
          0x8B15 : New Access Point/Cell address - roaming
          0x8B19 : Scan request completed
          0x8B1A : Set ESSID (kernel generated)
          0x8B2A : Set Encoding (kernel generated)
          0x8C02 : Custom driver event
          0x8C03 : Registered node
          0x8C04 : Expired node
```


What does that mean?
I wanna make an Ad-Hoc connection with my PSP... Ubuntu finds and I connect to it, but I don't think it's Ad-Hoc... is there a way to test this connection, like doing a "ping"?

---

### Post by vitorgatti on 2008-05-12
nobody? (up)

---

### Post by mrroland on 2008-05-12
- What chipset does your wireless device use?
- Which driver do you use?

---

