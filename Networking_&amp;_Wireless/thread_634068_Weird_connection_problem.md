---
title: "Weird connection problem"
date: 2007-12-07
forum: Networking &amp; Wireless
---

### Post by Coffeeman51 on 2007-12-07
I can't figure this out....I've used Ubuntu easily for the last 4 months...with no problems and then I decided to go back to a dual boot with xp (dont ask...lol)

NOW...neither the the LiveCD nor the installed 7.10 version of Ubuntu will recognize the network...XP works fine connecting (thats where I am now) , I've tried manually putting in the ip etc...but to no avail

my system runs on a foxconn K8S755a with an rtl8139 built in nic
dual booting with xp pro

connection is thru my landlords router with cable dsl

---

### Post by csat on 2007-12-07
It seems to be a realtek bug and you can find about it from Google.  Maybe updating your nic driver would fix it.

---

### Post by Coffeeman51 on 2007-12-08
After some reading and with the hint from above I was able to solve the problem myself...

I remembered that I had done an update on WinXp and the last file had been a RealTek driver update for the nic...so...I did a 'rollback' on the WinXP nic driver...and lo and behold...Ubuntu connected...did all the updates and go it working...

I guess what baffled me was that having WinXP dual booted seemed to mess with the MBR...apparently the nic update went to the boot record and that didnt match with the driver in the linux kernal....so no internet...

---

