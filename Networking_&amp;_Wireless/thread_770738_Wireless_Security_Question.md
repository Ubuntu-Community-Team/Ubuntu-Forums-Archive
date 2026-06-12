---
title: "Wireless Security Question"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by jmemm37 on 2008-04-27
I don't know if this would be a bug in the 8.04 OS but I noticed something about my wireless on my Toshiba laptop. Everything else seems to be working fine at the moment with my 8.04 Wubi install but this one thing. First of all I need to say that whoever came up with Wubi is a genius!!! I am totally amazed that this installs just like any other program within the Windows OS. I need to run Windows because I am going to college for computer technology online and my college uses Windows Internet Explorer only for the majority of its course content delivery. But, I loved Ubuntu from the 6.06 LTS OS and am glad that 8.04 can install this way. Ok, now to my issue at hand.

I have noticed that when I configure my wireless, I can surf the net fine:) The only problem is that when I power my laptop down and restart at a later time, I need to go back in and reconfigure. When I go into wireless properties, i notice my original PSA security key has many more characters added to the ones I inputted the first time I configured it. This happens EVERY time I restart my computer:( Does anybody else experience this???

Also, will Ubuntu ever work correctly with Hibernate and Suspend modes???

Any answers would be greatly appreciated.

---

### Post by Monicker on 2008-04-27
Is this WPA PSK?  If so, that is normal.  The ascii passphrase you enter is converted to another format which is actually used by wireless.


Run the following command from a terminal to get a bit more info on the process:

```
man wpa_passphrase
```

---

### Post by jmemm37 on 2008-04-27
Thank you for your reply. It is WPA. What I don't understand though is why do I have to keep deleting the passphrase that is created and reenter my security key in order to bypass being told I can not access the page which happens no matter what page I try to access?

---

### Post by jmemm37 on 2008-05-03
I now am stumped. I have to keep reseting my PSA wireless security key in order to access the Internet wirelessly from my laptop. On top of this, when I change my router's security to WEP-128bit, I then try to reconfigure my wireless on my laptop and it does not allow me to enter all 13 pairs of hexbit characters. In the past when I ran Dapper, I would set my WEP to 64 bit but, since my laptop is not the only computer on my home network, I don't want to run just 64bit WEP. Can anyone who is well abreast wireless security within Linux help me?](*,)[-o<:cry:

---

