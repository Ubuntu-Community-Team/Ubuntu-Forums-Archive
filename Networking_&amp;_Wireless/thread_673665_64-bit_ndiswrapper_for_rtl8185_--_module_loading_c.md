---
title: "64-bit ndiswrapper for rtl8185 -- module loading craziness!"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by abeppu on 2008-01-20
Hi -- 

I'm running 64 bit Gutsy, and have a realtek 8185L wireless card.  Like a lot of other people, I found that the native r8180 driver works for unencrypted networks but the whole system freezes up when I try to connect to an encrypted network (e.g. my home network).  So I decided to try ndiswrapper.  I downloaded the most recent stable release of ndiswrapper, and compiled and installed without issue (or at least without error messages).  I downloaded a 64-bit XP driver for my card from the realtek site, and installed it into ndiswrapper -- so "ndiswrapper -l" returns
> 
net8185x64 : driver installed
     device (10EC:8185) present (alternate driver r8180)


Now the problem is that it seems like I might not be able to load ndiswrapper.  Doing 
```

sudo modprobe -v ndiswrapper

```
just hangs.  Opening another terminal and doing
```

lsmod | grep ndiswrapper

```
shows that ndiswrapper is loaded -- but I'm not sure, mainly because there's no sign of wlan0 when I open network-admin.  Is it loaded or not?  If it isn't, what do I need to do to load it, and if it is, what do I need to do to get my wireless up and running?

Thanks in advance for your help.  Also, I'm relatively new to this -- so please, in your responses, go slow, and don't assume I know anything!

---

### Post by jeffus_il on 2008-01-21
Search the forum for solutions, maybe you can use the native driver, always preferable, I found this:
>  Re: Need help removing RTL8180 driver and replacing with ndiswrapper for WPA [Dapper]             
                                                              I used to have a 8180... the trick with it was you had to set the password before the essid name on the interfaces file, but that was for wep... I never used wpa. You can still try anyway.

---

