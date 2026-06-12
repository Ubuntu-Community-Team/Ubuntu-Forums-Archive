---
title: "community help  not useful for me so far"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by umairsaeed219 on 2007-06-24
help me guys 
i m trying to install intel 536ep modem on my pc <intel > currenty i am rubnning 6.06 lts (i have also tried to install it on 7.04 but failed there also) i have followed the instructio given on [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto) 
when i acted upon thes instruction and at the end of above page it is written under FINISHING  heading that it does work with wvdial

so i tried it to check whether i have successfuly installed modem or not it says
 
[I]sudo wvdialconf /etc/wvdial.conf
password
editing /etc/wvdial.conf
scanning your serial ports for a modem 
ttyS0<info>:decice or resource busy
modem port scan <*1>:S0 S1 S2 S3
sorrry no modem was detected
is in use by another programme?
do you configure it properly with set serial[/I]

guys you can check how i m suffering because i have noted this log on  paper and then type it in notepad (of windows ) to post it here
 so please help me as soon as possible

also tell me whether it is possible to co

---

### Post by sharke on 2007-06-24
Intel have linux drivers on their website. if vwdial does not work try pppconfig.
Regards
Sharke

---

### Post by umairsaeed219 on 2007-06-25
i have tried both wvdial and pppconf both says modem not found

---

### Post by sharke on 2007-06-25
Are you using /dev/536ep0 for the modem port.
Regards
Sharke

---

### Post by Ayuthia on 2007-06-25
I am not for sure if I can help or not because I have not tried to use the modem on this laptop.  Can you post what you have in your /etc/wvdial.conf file?

---

