---
title: "Manual Configuration does not work with security"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by ikunat33 on 2008-01-14
I am able to use Network Manager to successfully connect to any network with security as long as it is set to roaming mode. If I try Manual Configuration I am only able to connect to networks without security. I have also tried to use WICD with the same result.
Does anyone else have this problem or any idea what may be causing it. It seems a little odd to me.

---

### Post by zipperback on 2008-01-14
> **ikunat33 said:**
> I am able to use Network Manager to successfully connect to any network with security as long as it is set to roaming mode. If I try Manual Configuration I am only able to connect to networks without security. I have also tried to use WICD with the same result.
Does anyone else have this problem or any idea what may be causing it. It seems a little odd to me.


Check the box in your advanced settings in wicd for your access point that says to automatically connect to the access point and provide it the required access information.

I use wicd and it works great.

- zipperback
:popcorn:

---

### Post by zipperback on 2008-01-14
Attached you will find a screenshot for reference.

- zipperback
:popcorn:

---

### Post by ikunat33 on 2008-01-14
Thanks Guys,

Those are the first things I looked at. All the settings are correct according to the documentation.

---

### Post by zipperback on 2008-01-14
Perhaps you might need to reinstall wicd. Maybe something got messed up somehow.


- zipperback
:popcorn:

---

### Post by ikunat33 on 2008-01-14
Thanks.. already done that as well.

---

### Post by kevdog on 2008-01-14
check out connecting from the command line -- link in my signature.

---

### Post by ikunat33 on 2008-01-19
I appreciate all the ideas.
Here is an update on what happens:

I have 2 networks in the building I need to manage. I have WPA on one but for some reason the other person insists on using WEP despite my demonstration on how easy it is to crack.. I digress....
One uses WEP the other WPA

- I connect to the WPA using DHCP then set up the manual configuration settings.
- I reconnect to the network using the manual configuration settings with no problem.
- I connect to the WEP using DHCP then set up the manual configuration settings.
- I reconnect to the network using the manual configuration settings with no problem.
- I then try to use the WPA router with the manual configuration settings...

At this point I am unable to connect again. I manually release and flush and you name it but in order for the manual settings to work again I have to reconnect using DHCP first. This is the same no matter what I try. I must be missing something but I can not figure out what.
OH... and this is the same in either the network manager that comes with UBUNTU or with WICD

Thanks

:popcorn:

---

