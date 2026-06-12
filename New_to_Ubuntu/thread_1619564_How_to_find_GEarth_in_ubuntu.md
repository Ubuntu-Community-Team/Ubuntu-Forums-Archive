---
title: "How to find GEarth in ubuntu"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by navaneethan on 2010-11-11
I my meerkat i have installed google earth package by apt-get and i unable to find it plz help  me
:(

---

### Post by godspeedmav on 2010-11-12
You will be able to see it in **Applications > Internet**. If you don't you could right click on the **menu > Edit Menus > Internet** and see if the box near google earth is *checked* or not.

If you still cannot see it I suggest you remove it, and follow this guide:
[U][B][http://ubuntuguide.net/how-to-install-google-earth-in-ubuntu-10-10-maverick](http://ubuntuguide.net/how-to-install-google-earth-in-ubuntu-10-10-maverick)
[/B][/U]
[COLOR="Red"]**Note:**[/COLOR] if your computer is 32-bit you can start following the guide from, ***"Now let’s start installing:"*** part or if it is 64-bit follow the whole guide.

---

### Post by navaneethan on 2010-11-13
navanee@navanee-Vostro-1015:~$ sudo apt-get install ia32-libs lib32nss-mdns
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ia32-libs
E: Unable to locate package lib32nss-mdns
navanee@navanee-Vostro-1015:~$ 


In that page I couldn't able to install the aboce suite help  me!!

---

### Post by godspeedmav on 2010-11-13
As according to this: 

_[https://launchpad.net/ubuntu/+source/ia32-libs](https://launchpad.net/ubuntu/+source/ia32-libs)_

it is in the **universe** repository.

So, check if your universe repository is enabled by going to **System > Administration > Software Sources > Ubuntu Software (Tab) > Community-maintained Open Source software (universe)**. Tick that box on the left of it, if it is not ticked already.

Also according to this:

_[http://ubuntuforums.org/showpost.php?p=4417385&postcount=914](http://ubuntuforums.org/showpost.php?p=4417385&postcount=914)_ 

Might be because probably the mirror you are using is not up to date. So, try changing the server you use by going to **Ubuntu Software (Tab)** described above, and click **Download from: > Other.. > Select Best Server > Choose Server** for the given best server. 

And make sure your system is upto date by issuing 
```
sudo apt-get update
sudo apt-get upgrade
```
then try installing again.

---

### Post by Dimoutlook on 2010-11-13
Pre built package are on deb follow link to install without all the bad fonts that come with building it yourself

hxxp://packages.medibuntu.org/lucid/googleearth.html 

replace the xx with t

Dimoutlook

---

