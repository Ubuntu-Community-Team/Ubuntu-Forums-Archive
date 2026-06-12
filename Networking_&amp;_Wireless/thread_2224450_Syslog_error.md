---
title: "Syslog error"
date: 2014-05-16
forum: Networking &amp; Wireless
---

### Post by Tanel_Tammik on 2014-05-16
Hello,

after each 2 minutes the following lines are added to my syslog file:

```
May 16 16:25:25 keevitaja-dell wpa_supplicant[895]: wlan0: CTRL-EVENT-SCAN-STARTED 
May 16 16:25:29 keevitaja-dell wpa_supplicant[895]: nl80211: send_and_recv->nl_recvmsgs failed: -33

```

Is it a bug or is it supposed to happen?

running 

```
DELL E5420
ubuntu 14.04 lts 3.13.0-24-generic

                description: Wireless interface
                product: Centrino Advanced-N 6205 [Taylor Peak]
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 34
                serial: a0:88:b4:16:09:9c
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-24-generic firmware=18.168.6.1 ip=192.168.1.68 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn

```

---

### Post by grahammechanical on 2014-05-16
Does Ubuntu 14.04 give you a wireless connection to your router? What do you think is a bug?

> wpa_supplicant[895]: wlan0: CTRL-SCAN-STARTED

OR 

> wpa_supplicant[895]: wlan0: nl80211: send_and_receive->nl_recvmesgs failed: -33

Are you getting these messages when you are connected wirelessly to a router? Do you have a wireless connection set to automatically connect but with the router switched off or not in range?

Regards.

---

### Post by Tanel_Tammik on 2014-05-16
oh sorry, yes this is relevant information.

i have no problems with my connection. during these error messages i am connected to my router and have no problems what so ever.

i just noticed the errors in the log files, and figured if there should be messages about the connection after every 2 minutes.

so it is ok and not a bug?

---

### Post by chaghi on 2014-05-25
I'm also seeing this. Is very annoying. It seems harmless in the sense that there is no problem with my wifi connection, but it spams syslog in a way that makes very difficult to find anything else there.

I've reported this as bug [lpbug]1323089[/lpbug]. It would be nice if someone else confirms the bug.

---

### Post by SeijiSensei on 2014-05-26
I see it in my logs, too.  I confirmed the bug at Launchpad.

---

### Post by levik666 on 2014-08-10
Hi all,
I was wondering when this issue is resolved?

---

### Post by cubix-system78 on 2014-11-03
[WinEunuchs2Unix (ricklee518)]("https://launchpad.net/%7Ericklee518")             wrote             on 2014-08-18:

"Oops  this has been going on since 2009 and a developer did respond that it  is simply for roaming in corporate environments with multiple access  points to connect to.  If you only have one AP at home go into network  manager, select "Edit Connection", highlight your AP / wlan0 and click  "Edit".  Then click the down arrow next to BSSID  which is blank.  Then  select the mac address that was hidden before.

 My apologies for linking this to an 802.11n problem.  Once bitten twice shy I guess...."




It seems to be a solution.

---

