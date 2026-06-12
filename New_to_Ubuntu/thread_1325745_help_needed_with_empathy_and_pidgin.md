---
title: "help needed with empathy and pidgin"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by miguel_d on 2009-11-13
Hi, i just installed ubuntu Karmic Koala and i when i have some problems with empathy and pidgin. On both of them i can't access my MSN account, on empathy it's says it's and network error and on pidgin says: "server connection error. Notification: connection refused"

Can you help with this?

---

### Post by durand on 2009-11-13
If you only plan on using msn, you could try [emesene]("apt:emesene"). It's a really nice msn client.

---

### Post by miguel_d on 2009-11-13
> **durand said:**
> If you only plan on using msn, you could try [emesene]("apt:emesene"). It's a really nice msn client.

thanks, i tried emesene and this it showed me this error: Connection problem: [Errno 111] connection refused

---

### Post by durand on 2009-11-13
Hmmm, it sounds like an msn server may be down for you :S Does it work with msn messenger? I've had that error before but its always cleared up within a few hours.

---

### Post by miguel_d on 2009-11-13
> **durand said:**
> Hmmm, it sounds like an msn server may be down for you :S Does it work with msn messenger? I've had that error before but its always cleared up within a few hours.

I'll try again tomorrow

---

### Post by miguel_d on 2009-11-14
Tried again today and i had the same error messages on all of them

---

### Post by jrandolph on 2009-11-14
Have you tried aMSN?
Its pretty decent

---

### Post by miguel_d on 2009-11-14
> **jrandolph said:**
> Have you tried aMSN?
Its pretty decent

Tried it now and also gave an error: connection refused :(

---

### Post by miguel_d on 2009-11-14
Also tried to install again empathy and pidgin and it still doesn't work. Anyone have any idea why?

---

### Post by durand on 2009-11-14
For now, you could use a web messenger such as [http://www.ebuddy.com/](http://www.ebuddy.com/) or msn's own one. It could be that your firewall is blocking it but that is really unlikely.

---

### Post by miguel_d on 2009-11-14
> **durand said:**
> For now, you could use a web messenger such as [http://www.ebuddy.com/](http://www.ebuddy.com/) or msn's own one. It could be that your firewall is blocking it but that is really unlikely.

Yeah, i've been using e-buddy. Do you know where i can go see if my firewall is blocking them?

---

### Post by durand on 2009-11-14
Install [apt:firestarter]("apt:firestarter"), then go to System > Administration > Firestarter. Then try using msn. It should say if it is being blocked in one of the tabs. If so, right click and allow it.

---

### Post by miguel_d on 2009-11-14
> **durand said:**
> Install [apt:firestarter](apt:firestarter), then go to System > Administration > Firestarter. Then try using msn. It should say if it is being blocked in one of the tabs. If so, right click and allow it.


also didn't worked, but thanks anyway. The weird thing is that i tried with a my google account and it worked

---

### Post by durand on 2009-11-14
Thats why I think it has something to do with the msn servers in your area. Ebuddy works because its web based so everything goes through them rather than the servers near you.

---

### Post by miguel_d on 2009-11-14
> **durand said:**
> Thats why I think it has something to do with the msn servers in your area. Ebuddy works because its web based so everything goes through them rather than the servers near you.

Yeah, i guess i'll have to wait

---

### Post by bwzz on 2009-11-14
MSN usually uses port 1863
in empathy, you can change the port to 80 or 8080, from  account --> advanced.
it might work if a firewall is blocking port 1863

---

### Post by miguel_d on 2009-11-14
> **bwzz said:**
> MSN usually uses port 1863
in empathy, you can change the port to 80 or 8080, from  account --> advanced.
it might work if a firewall is blocking port 1863

Tried that and didn't worked. Also went to other pc with windows and i could log in perfectly. So i guess it's not the server...

---

### Post by miguel_d on 2009-11-15
Problem solved, well at least with pidgin and emesene. Just had to use HTTP mode instead of the port

---

### Post by bwzz on 2009-11-15
In Windows MSN Messenger will automatically transfer to port 80 if it's original port is blocked.
This means you have to do it manually then.
Please mark [solved]

---

### Post by dcharry on 2009-11-28
Hi, I have the same problem today as my landlord just bought a new router and right afterwards my emesene reported this error, although now we have a solution, I suspect there is something to do with port numbers allowed in router setting?

---

