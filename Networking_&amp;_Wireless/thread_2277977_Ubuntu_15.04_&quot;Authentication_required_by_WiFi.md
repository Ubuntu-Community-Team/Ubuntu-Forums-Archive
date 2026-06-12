---
title: "Ubuntu 15.04 &quot;Authentication required by WiFi Network&quot;"
date: 2015-05-12
forum: Networking &amp; Wireless
---

### Post by scorpio4 on 2015-05-12
Does anyone know how to bypass this password prompt "Authentication required by WiFi Network"? I have tried everything I know or have read out there, which there is not a whole lot. I currently have my WiFi network passworded through a WPA. With any other device in my household I don’t need to enter the internet password every time I start using it. So why does it require it instead of saving it for every login there after the first. Ive already gone into the settings for the network and set it to automatically login, which it does...if the network is not passworded. Is this an oversight or was this on purpose? It's very frustrating to have to enter my password every time in my own house on my own network even when after waking my computer up from being suspended. Please help!

Thank you all in advance!

---

### Post by Vladlenin5000 on 2015-05-13
Hi and welcome.

Being asked for password to unlock the password keyring is the direct consequence of automatic login, ie, login without being prompted for a user password. Removing that it will connect automatically to any networks previously configured.

---

### Post by scorpio4 on 2015-05-13
Thank you, but I have already disabled the password keyring. Without it I am still prompted with "authentication required by wifi network".

---

### Post by Vladlenin5000 on 2015-05-13
Obviously... If there's no "place" to store credentials then you'll have to provide them whenever needed.
There's already an OS that works pretty much without the security you abhor so much, it's called Microsoft Windows. Give it a try.

---

### Post by grahammechanical on 2015-05-13
I do not have this problem. I have used Network Manager to edit the WiFi connection. On the General tab I have ticked Automiatically connect to this network when it is available. And if I go to the WiFi security tab there is a panel with my password in. The password is disguised by ******** but there is a tick box for Show password.

At the right side of the panel holding the password there is an icon which looks to my mind to be a disk drive with a down arrow on it. Click the icon and 2 menu items will appear. Store the password only for this user & Store the password for all users.

Do you not see that on your system?

Regards.

---

### Post by scorpio4 on 2015-05-13
Thank you! That did the trick. I always saw that little icon, but was not aware that it was a drop down menu. I'm new to Ubuntu or Linux in general and am still in the learning phase.

---

