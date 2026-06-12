---
title: "Intel 2915 wireless card. Detected and running but no signal"
date: 2006-08-02
forum: Networking &amp; Wireless
---

### Post by Stex on 2006-08-02
I've just replaced the wireless card in my laptop with an intel 2915 and ubuntu seemes to have picked it up. I can go into my network settings and change all the config but when I go to the ESSID it just can't pick up anything.

I looked into installing the ieee drivers but noticed they're already present in my system anyway and decided not to risk ruining what I got.

Any tips? I came here because of my knack for going and doing things in the complete wrong way and getting myself in a muddle. This is actually my first time modding a laptop but I can't see how I could have gone wrong sliding it in and connecting 2 anteni leads.

iwconfig gives:
```
eth2      radio off  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=off   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

lspci fives:
```
0000:01:01.0 Network controller: Intel Corporation PRO/Wireless 2915ABG MiniPCI Adapter (rev 05)
```

Oh, and I got a computer right next to me that can detect the wireless signal so I'm not just out of range :p

Many thanks
~Steve

---

