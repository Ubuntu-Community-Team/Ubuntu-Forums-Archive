---
title: "Help requested with wireless"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by TDKING on 2010-04-07
hi guys had to uninstall ubuntu and re-install i cant seem to get on my wireless network not only that but ubuntu cant even see my wireless network i only have wireless in my room so having to use laptop for this 
 
can someone please tell me what i need to do to sort this out i need to get this online asap due to course work cheers
 
also dont know if my network card is installed or what the card is can someone help me from what i remember was some thing like bcom driver or something 
 
thanks

---

### Post by theozzlives on 2010-04-07
Post the results of
```
lspci
```
so we can see what kind of wireless you have.

---

### Post by Paqman on 2010-04-07
Go to System > Admin > Hardware Drivers and see if there's a wifi driver you can install. Also check to make sure the wifi isn't turned off, most laptops have a button that will disable wifi.

---

### Post by mangurt on 2010-04-07
Also, look and see if you need restricted drivers.  I know with my Dell laptop, I had to install restricted drivers in order to get my WiFi working.

---

### Post by TDKING on 2010-04-07
hey guys thanks for the help just to confirm that the computer with ubuntu on is not a laptop 
cheers will have ago with what u have told me and i will try get the code anymore help would be brilliant cheers

---

### Post by TDKING on 2010-04-07
tried this but there is nothing there ? 
 
System > Admin > Hardware Drivers

---

### Post by albert s on 2010-04-07
have you tried a hardwired update yet?
this got my wi fi working for me when I had this problem.

---

### Post by mcoleman44 on 2010-04-07
If you can get an etternet connection then try this:
```
sudo apt-get update
sudo apt-get upgrade
```
system>admin>hardware drivers
It should be listed now.

---

### Post by lisati on 2010-04-07
Thread title changed

---

### Post by TDKING on 2010-04-07
just did this System > Admin > Hardware Drivers 
 
and there was a driver there to install and activate 
Broadcom B43 wireless driver but everytime i try to activate it it wont ???? any ideas ?? 
 
 
cheers

---

### Post by mcoleman44 on 2010-04-07
Restart the computer and then try to activate it.

---

### Post by TDKING on 2010-04-07
tried still no luck with it :( anything you can sujest other then hard wiring it ? i dont have a cable long enough to do it so would have to rig the entire system up downstairs 
 
Cheers

---

### Post by TDKING on 2010-04-07
right thought bugger it so i brought the comp downstairs hardwired it in and connected it got the driver to install not sure why it will still not see the network anyone give me a quick talk through this please ? 

Thanks

---

### Post by albert s on 2010-04-07
have you shut down then turned it on again? not just reboot.
then check again if there are any updates available, make sure you click the check for updates box and dont just accept the usual "your computer was updated one hour ago" thingie.
HTH

---

### Post by albert s on 2010-04-07
BTW, are you sure your wifi is not hidden.?

---

