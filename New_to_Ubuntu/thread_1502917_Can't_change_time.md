---
title: "Can't change time"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by Phil Binner on 2010-06-06
The time on my computer is wrong and I can't change it. When I go into SYSTEM->ADMINISTRATION->DATE AND TIME I am told "Not Authorised to Make Changes". I am the only user on this system. If there is an Administrator it is hidden, and I've tried to change to Administrator with every password I may have entered at some time in the past. No joy.

Any ideas please.

Phil Binner

Death to Microsoft

---

### Post by wojox on 2010-06-06
You should be a member of Admins. You click on the Keys and enter your user name and password and it tells you "Not Authorized to Make Changes" ?

---

### Post by Phil Binner on 2010-06-06
Hi. Thanks for the help, but I don't understand it. I have looked at teh admin group, and I am, in fact, the only member of it. I don't understand what to do from there.

Phil Binner

Death to Microsoft.

---

### Post by wojox on 2010-06-06
What if you right click the Clock Applet in the panel and select Preferences > Locations and Edit your time there?

---

### Post by warfacegod on 2010-06-06
You may want to try putting yourself in your group or root.

---

### Post by Phil Binner on 2010-06-06
Hi Guys, thanks for the help. I'm afraid I'm not technically ept, so you have to be gentle with me. I tried right clicking the clock and following the instructions, but all I could do was say my time zone was equivalent to London. No chance to change the clock. I suspect that putting myself in my group or root is the answer, but what the ***k does that mean in English.

Help is going well, but I'd be grateful for smaller steps.

Thanks

Phil Binner

---

### Post by halitech on 2010-06-06
Have you checked to make sure the time in the BIOS is correct? Is the time zone correct? If it is, you can open a terminal and run
```
sudo date --set 21:08:0
```
obviously changing the time to the correct time for where you are.

---

### Post by Phil Binner on 2010-06-07
OK, that sorted it. Thanks.

---

