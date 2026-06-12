---
title: "Problem connecting to other wireless networks"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by DenKain on 2008-03-02
I seem to be unable to connect to any wireless network but my home network. I have no idea what to post here (i.e. config files and the like) so I thought that I would post and ask what the community would need to look at to help me in this matter.

---

### Post by DenKain on 2008-03-15
bump

---

### Post by prshah on 2008-03-15
> **DenKain said:**
> I seem to be unable to connect to any wireless network but my home network. I have no idea what to post here (i.e. config files and the like) so I thought that I would post and ask what the community would need to look at to help me in this matter.

lets just start with ```
iwconfig wlan0
```. Please replace "wlan0" with the actual device name for the wireless on your system: if you dont know that, use just ```
iwconfig
``` to find the supported device name.

---

### Post by DenKain on 2008-03-15
```

eth1    IEEE 802.11b/g  ESSID:"dlink"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:15:E9:15:88:22   
          Bit Rate=24 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=55/100  Signal level=-67 dBm  Noise level=-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by ugm6hr on 2008-03-15
How do you connect in Ubuntu - with network manager (the 4 blue/grey vertical bars icon)?

If so, do you have roaming enabled?

Seems odd that you can connect to 1 wifi access point (at home) , but not elsewhere.

Possible issues I can think of:

1. Access point security - e.g. hidden SSID, MAC filtering, WPA etc....
Presumably you have already thought of these.

2. Fixed IP address (rather than DHCP)
This is a problem with Network Manager (NM).

3. 802.11g broadcast only (rather than mixed b/g)
You have a broadcom wifi card, which will only work with 802.11b wifi (unless you use ndiswrapper) in Linux due to driver issues.  If the access point is set to g broadcast only, you will not be able to connect.

---

### Post by DenKain on 2008-03-15
Yes I am using the network manager.

Yes it is on roam.

1. yes I did look into all of that.

2. Since it is on roam it should be using DHCP.

3. I am not sure where to check to see if it is using g broadcast only.

thanks for the current and any future help.

---

### Post by ugm6hr on 2008-03-15
> **DenKain said:**
> 2. Since it is on roam it should be using DHCP.

3. I am not sure where to check to see if it is using g broadcast only.

2. "Roam" is a setting on your computer - "DHCP" is a setting in the access point.  So your assumption may be incorrect.

3. You need administrator access to the access point to check this setting.

The most important question...  where have you tried connecting apart from at home?

---

### Post by DenKain on 2008-03-15
I have set my home router to filter by MAC and it is set to DHCP. I have tried to connect to many open networks (coffee houses and the like) with no luck what so ever.

---

### Post by ugm6hr on 2008-03-15
> **DenKain said:**
> I have tried to connect to many open networks (coffee houses and the like) with no luck what so ever.

Open networks must use DHCP.  They also don't hide SSID.  So it is unlikely to be a problem with NM.

Whether they use b or g (or both) to broadcast - I don't know.  But that is likely to be the problem, I suspect...

Do the networks appear in the list in Network Manager?  Does NM look like it is trying to connect?

---

### Post by DenKain on 2008-03-15
Yes and yes.

---

### Post by ugm6hr on 2008-03-15
> **DenKain said:**
> Yes and yes.

Hmmm.... Then apart from the b vs g issue, I can't think of anything else that would be causing connection issues on an open network...

Anyone else?

---

