---
title: "Need to set 802.11bg card to just 802.11b"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by timcredible on 2007-12-10
I have a level one usb-attached wireless adapter.  It works fine for 802.11g, but I  need to connect to an AP that is only 802.11b, and the iwconfig commands to change that don't work - I get an error messages saying 'operation not supported'.  I'm using whatever came with gutsy, haven't tried ndiswrapper yet because 802.11g works.  Is there a setting in a file or something I can change, or do I need to go the ndiswrapper route?  thanks.

---

### Post by kevdog on 2007-12-10
What driver are you using and what commands are you typing?  Sometimes with ra based chipsets the commands are slightly different. iwpriv statments.

---

### Post by timcredible on 2007-12-10
thanks for the reply.  i haven't installed any drivers - i'm just using whatever comes with the gutsy install cd.

in case this helps, when i check 'iwconfig', I get this:
```

wlan1     IEEE 802.11g  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

the iwconfig commands to change it to 802.11b don't work, i get this error message:
```

Error for wireless request "Set Modulation" (8B2F) :
    SET failed on device wlan1 ; Operation not supported.

```

---

