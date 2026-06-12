---
title: "Wirless Card stopped working"
date: 2006-08-11
forum: Networking &amp; Wireless
---

### Post by cgborkgb on 2006-08-11
Hi.  I was connected to my wireless network with no problems.  Didn't install anything or get any new updates.  After hibernation, it just didn't connect.  I go to Sys->Admin->Networking and Default Gateway Device is blank.  So I change it to my wireless card eth1, and exit.  Still no connection.  I check Networking again and the Default Gateway Device is blank again!  Changed it to eth1 again, but it keeps on dropping back to nothing over and over.  Checked Wlassistant, couldn't find any networks including my neighbors.  Checked my router for my wireless card Mac Address, but it doesn't show up.  If anybody could help, I would appreciate it :)

Here is ifconfig
```

eth1      IEEE 802.11b  ESSID:""  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.457 GHz  Access Point: None
          Bit Rate:2 Mb/s   Sensitivity:1/3
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

and here is iwconfig
```

eth1      IEEE 802.11b  ESSID:""  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.457 GHz  Access Point: None
          Bit Rate:2 Mb/s   Sensitivity:1/3
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by cgborkgb on 2006-08-11
Wow!  After two days of not being able to connect, even from right next to my router, it just mysteriously connected.  I don't get it :rolleyes:

---

### Post by cgborkgb on 2006-08-13
Ok, now it's NOT WORKING again.  My router does recognize my wireless card and even says it has assigned it an ip address.  Otherwise, I am still having the same problems as stated above.  Can anybody help?

---

