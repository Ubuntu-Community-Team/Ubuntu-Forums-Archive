---
title: "Wireless connects but no connection (!)"
date: 2014-08-02
forum: Networking &amp; Wireless
---

### Post by zuheyr2 on 2014-08-02
Hello,

I am using chrome Ubuntu, Kubuntu flavor 14.04 on Acer C720. Perfectly working wireless at home (Belgium) is not working in Norway.
The computer says it is connected but neither the browser nor the system update etc find connection... I cannot understand and I am sorry if it sounds nonsense. Thanks for reading! Regards.

---

### Post by Hadaka on 2014-08-02
Hi your current country code is BE for Belguim you may want to
change the country code to NO for Norway, to change the codes
replace the XX with the country you need, 
~~~UPPERCASE~~~
BE = Belgium
NO = Norway
```
sudo sed -i 's/^REG.*=$/&XX/' /etc/default/crda
```
then do.
```
sudo iw reg set XX
```
BOOT

be sure to retain this file so you can eaisly change back
between countries
Here is mine,
```
:~$ cat /etc/default/crda
# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMANIN=US
```

```
:~$ iw reg get
country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
```

---

### Post by zuheyr2 on 2014-08-02
Dear Hadaka,
I cannot thank you enough. I will have to save these in some files and go back to Ubuntu to try but I think it will work.
I am so grateful. 

Kind regards, zuheyr

---

### Post by zuheyr2 on 2014-08-02
Dear Hadaka,
I cannot thank you enough. I will have to save these in some files and go back to Ubuntu to try but I think it will work.
I am so grateful. 

Kind regards, zuheyr

---

### Post by zuheyr2 on 2014-08-02
Hi Hadaka,

No it did not work... Thank you very much to help me more please :) 
Kind regards.

---

### Post by Hadaka on 2014-08-02
Hi, please tell me which country you are in,,,BE or NO ?
then please post the output of..
```
cat /etc/default/crda
iw reg get
```
thanks.

---

