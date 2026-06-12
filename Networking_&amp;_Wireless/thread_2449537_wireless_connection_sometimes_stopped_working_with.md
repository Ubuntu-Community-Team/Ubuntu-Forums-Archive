---
title: "wireless connection sometimes stopped working with new ISP"
date: 2020-08-28
forum: Networking &amp; Wireless
---

### Post by monkeybrain20122 on 2020-08-28
Hi,

I am sharing internet with my neighbours via wifi, since about two weeks ago they changed the internet provider and I am experiencing some sporadic disconnection. The wifi is still connected according to network manager but I can't go to any website (on Firefox it says site not found) The quick fix would be to disconnect (from network manager) and then reconnect and it works again. It doesn't happen very often but it is still annoying.

It never happened before with the previous provider. Also it only happens on this laptop (ubuntu 20.04), I have another two: one with Ubuntu  16.04 and another with Kubuntu 20.04 and this doesn't happen.

[Here]("https://pastebin.com/g6f8pMD7") is the output from the wireless-info scripts.

Thanks.

---

### Post by praseodym on 2020-08-29
Lets try
```

sudo iwconfig wlp2s0 power off
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service
```
Also try channel 1 instead of 6

---

### Post by monkeybrain20122 on 2020-08-31
Hi, thanks.

But the laptop is plugged into an AC outlet so I don't think power management is the issue.

---

### Post by monkeybrain20122 on 2020-09-01
These are the error message when it stops from dmesg | tail
```

[60181.243168] wlp2s0: cannot understand ECSA IE operating class, 11, ignoring
[60181.345650] wlp2s0: cannot understand ECSA IE operating class, 11, ignoring
[60181.448153] wlp2s0: cannot understand ECSA IE operating class, 11, ignoring
[60181.550809] wlp2s0: cannot understand ECSA IE operating class, 11, ignoring
[60181.653061] wlp2s0: cannot understand ECSA IE operating class, 11, ignoring
[60181.755415] wlp2s0: cannot understand ECSA IE operating class, 11, ignoring
[60181.858098] wlp2s0: cannot understand ECSA IE operating class, 11, ignoring
[60181.959729] wlp2s0: cannot understand ECSA IE operating class, 11, ignoring
[60182.062665] wlp2s0: cannot understand ECSA IE operating class, 11, ignoring
[60182.165011] wlp2s0: cannot understand ECSA IE operating class, 11, ignoring
```

---

### Post by monkeybrain20122 on 2020-09-05
bump

---

### Post by monkeybrain20122 on 2020-09-12
I disabled ipv6 and apparently it works, for one week I haven't lost connection. Is there any side effect to that?

---

### Post by Frogs Hair on 2020-09-12
I've not seen any problems from disabling ipv6 and doing so solved the same problem for me.

---

### Post by monkeybrain20122 on 2020-09-13
Too soon, it just happens again.

---

### Post by monkeybrain20122 on 2020-09-22
These disconnections happen sporadically, sometimes it work for days with no issues, sometimes it disconnects (but networkmanager always shows connected) several times a day and disable and then enable wifi always works.

so far I have disabled ipv6, set power save to 2 and tried the solution of post #5 [here]("https://ubuntuforums.org/showthread.php?t=2246457"), still disconnecting from time to time. This never happened until they changed the ISP.

---

