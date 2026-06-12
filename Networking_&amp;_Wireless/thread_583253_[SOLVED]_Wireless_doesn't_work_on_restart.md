---
title: "[SOLVED] Wireless doesn't work on restart"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by gr3gg0r on 2007-10-20
I'm using an hp dv6449us laptop with a broadcom 43(21?) wireless adapter.  I used ndiswrapper and install an xp wireless driver (same one I use with XP) and the wireless works great, sees all the connections and connects fine.  But...  When I restart the computer, Network Manager doesn't recognize the wireless adapter anymore.  I have the go into ndiswrapper and uninstall and reinstall the inf file to get it working again.  What could be causing this and how can I fix it??

---

### Post by gr3gg0r on 2007-10-20
oh, and I just installed a fresh copy of gusty gibbon.  Wireless didn't work at all in fiesty.

---

### Post by ddrichardson on 2007-10-20
You need to do the following from the command line:
```
sudo -s
echo ndiswrapper >> /etc/modules
exit
```
Then it should work when you reboot.

---

### Post by HokeyFry on 2007-10-20
one solution to my ndiswrapper problems is that i always compile from source. this has solved many an issue between wireless and linux for me. thats how i got wireless working in feisty too

ddrichardson's solution though sounds like it will fix the problem

---

### Post by gr3gg0r on 2007-10-20
thanks guys, i appreciate the responses.  And yes, ddrichardson solution worked.  I'm now happily using wireless for the first time in any linux distro.  :)  It looks like this might be windows' final farewell.  :)

---

### Post by ddrichardson on 2007-10-20
Happy days - can you mark the thread as solved to help others?

---

### Post by kal1 on 2008-06-26
hi 


I tried but this doesn't work for me.
when i reboot my machine, wireless doesnt work, but
if i make any changes to the wireless settings suppose if I change password type to a different thing like wep(ascii) and again if I change to its original type say wep(hexadecimal) then it will work.

what could be the problem???

pls guide me to rectify

---

