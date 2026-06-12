---
title: "Loss of wireless connection when computer is idle"
date: 2007-10-03
forum: Networking &amp; Wireless
---

### Post by SatanzJudge on 2007-10-03
Hi everyone,

I hope you can help me with a strange problem. Whenever my notebook is idle it looses the wireless connection. I'm not talking about standby/suspend mode but actually about idle meaning for example I'm away from the computer for 10 minutes. Of course this is very annoying especially when I'm downloading. As long as I'm using the notebook there's no problem with the connection. After a connection loss I can reactive the connection with KNetworkManager and it works until I leave the computer for another coffee break. The notebook _does not_ go into standby/suspend mode, just the screensaver is active!

I'm using Kubuntu 7.04 with KNetworkManager (v0.1) for network management. Kernel is version 2.6.20-16-generic, KDE is 3.5.6. The notebook has an Intel PRO/Wireless 2200BG card so I'm using the ipw2200 driver. WLAN is secured by WPA.

In BIOS there's no power saving setting for the wireless card.

Any idea what the problem is?

Thanks!

---

### Post by SatanzJudge on 2007-10-03
I've checked some settings:

```
# iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"xxxxx"
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:15:E9:0D:A6:98
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxx   Security mode:open
          Power Management:off
          Link Quality=82/100  Signal level=-48 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:17  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:1

```

```
# iwpriv wlan0 get_power
wlan0     get_power:Power save level: 6 (AC) OFF

```

So power management of the card is disabled. Could there be some daemon which enables power management after a while??

---

### Post by Lambert on 2007-10-03
Before you walk away next time, open up a terminal and type in this command

```

tail -f /var/log/syslog

```

This will show a list of things that are happening with your system. Read through it and post it here and maybe someone can help. You can open that file and read it to see if you see anything. Just recommending the tail option so you only see what is happening during the time you're away.

There's another log that might help.[COLOR="SeaGreen"] /var/log/messages[/COLOR] I believe is the correct file.

---

### Post by SatanzJudge on 2007-10-04
I think this problem is indeed caused by the power saving mode because I can reproduce the issue when I manually set the mode with "iwpriv wlan0 set_power 5".

Now the question is which daemon could cause this (ACPI, powernowd, etc) or if the driver decides to switch to power save even when it's disabled...

---

### Post by SatanzJudge on 2007-10-05
Ok, this doesn't seem to have anything to do with power saving.

I've checked /var/log/messages and noticed a "firmware error" message of the ipw2200 driver. Actually my issue sounds pretty much like [_this_]("http://bughost.org/bugzilla/show_bug.cgi?id=800") bug report.

It does only happen when there's heavy load on the connection (downloads).

I've updated to Kubuntu 7.10 Beta and will verify if the new kernel version (and thus hopefully new ipw2200 driver) fixes this problem.

---

