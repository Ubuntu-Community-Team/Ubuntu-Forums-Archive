---
title: "Cannot connect to specific Wi-Fi (home network)"
date: 2020-10-20
forum: Networking &amp; Wireless
---

### Post by roguejedi2 on 2020-10-20
Hello fellow Ubuntu users.

I just managed to install Ubuntu and I have a curious issue. I cannot seem to connect to my home router's Wi-Fi. I tried connecting to my phone's hotspot and that works fine.

I updated and upgraded the system. Restarted and all that. Also I tried troubleshooting by changing the wireless settings on my router to WPA2-PSK and AES (apparently this fixed the problem for another user).

Many thanks in advance.

---

### Post by CelticWarrior on 2020-10-20
> [COLOR=#000000]I cannot seem to connect to my home router's Wi-Fi.[/COLOR]

Please always describe exactly what's happening.
Can you "see" the network or not?
If you can and select it what happens next?

---

### Post by roguejedi2 on 2020-10-21
> **CelticWarrior said:**
> Please always describe exactly what's happening.
Can you "see" the network or not?
If you can and select it what happens next?

My apologies for not being detailed enough.

Yes, I see the network. I insert the passcode for it and then nothing happens. Actually it asks for the passcode again and it's not able to connect.
The passcode I put in is 100% correct.

---

### Post by morrownr on 2020-10-21
Hmmm... been there, seen this... 

The times that I have seen this is when, well, let me give you an example:

My router is set to AC only and I try to connect with a wifi adapter or card that is only capable of N. The same thing would happen on 2.4 GHz if the router is set to N only and your wifi adapter or card is only capable of G. Maybe this gives you something to try.

It might be helpful if you go to the Sticky called "Before posting in Networking and Wireless" and follow the instructions. That would help shed some light on your system.

---

### Post by roguejedi2 on 2020-10-23
> **morrownr said:**
> Hmmm... been there, seen this... 

The times that I have seen this is when, well, let me give you an example:

My router is set to AC only and I try to connect with a wifi adapter or card that is only capable of N. The same thing would happen on 2.4 GHz if the router is set to N only and your wifi adapter or card is only capable of G. Maybe this gives you something to try.

It might be helpful if you go to the Sticky called "Before posting in Networking and Wireless" and follow the instructions. That would help shed some light on your system.

Still haven't sorted the issue out... I followed the steps from the sticky post.
Another interesting thing I noticed is that I can connect to the 5Ghz network but not to the 2.4Ghz. I need to connect to the latter for a better range.

Do you have any other ideas?

---

### Post by chili555 on 2020-10-23
What is unique about your home network?

```
nmcli device wifi list
```Just show us your networks and redact the MAC addresses like this xx:

```
IN-USE  BSSID              SSID                   MODE   CHAN  RATE        SIGNAL  BARS  SECURIT>
        xx:37:E9:44:23:xx  DIRECT-X7-FireTV_69ab  Infra  1     130 Mbit/s  89      &#9602;&#9604;&#9606;&#9608;  WPA2   >
*       xx:2B:B0:DC:45:xx  GBR1                   Infra  1     405 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA2   >
        xx:2B:B0:DC:45:xx  GBR5                   Infra  149   405 Mbit/s  69      &#9602;&#9604;&#9606;_  WPA2   
```

---

### Post by roguejedi2 on 2020-10-27
> **chili555 said:**
> What is unique about your home network?

```
nmcli device wifi list
```Just show us your networks and redact the MAC addresses like this xx:

```
IN-USE  BSSID              SSID                   MODE   CHAN  RATE        SIGNAL  BARS  SECURIT>
        xx:37:E9:44:23:xx  DIRECT-X7-FireTV_69ab  Infra  1     130 Mbit/s  89      &#9602;&#9604;&#9606;&#9608;  WPA2   >
*       xx:2B:B0:DC:45:xx  GBR1                   Infra  1     405 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA2   >
        xx:2B:B0:DC:45:xx  GBR5                   Infra  149   405 Mbit/s  69      &#9602;&#9604;&#9606;_  WPA2   
```

There you go.

```
IN-USE  BSSID              SSID              MODE   CHAN  RATE        SIGNAL  BARS  SECURITY  
        xx:DA:C4:9B:BC:xx  2tigarilabucata   Infra  4     195 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2 
        xx:DA:C4:9B:BC:xx  --                Infra  4     195 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2      
*       xx:DA:C4:9B:BC:xx  3tigarilabucata   Infra  36    270 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2
```

The network I'm trying to connect and am unable to do so is ***2tigarilabucata***.

---

### Post by CelticWarrior on 2020-10-27
Set it to WPA2-AES instead of the mixed mode.

---

### Post by roguejedi2 on 2020-10-27
> **CelticWarrior said:**
> Set it to WPA2-AES instead of the mixed mode.


Did that. Still no change...

---

### Post by morrownr on 2020-10-27
Some things to try:

Router:

- Set the channel to 1 or 6 or 11, don't use Auto. Choose the least congested channel.
- Set the bandwidth to 20.

Computer:

- Use "Forget Connections" on all existing interfaces so as to get a fresh start.

Reboot everything. See what happens.

---

