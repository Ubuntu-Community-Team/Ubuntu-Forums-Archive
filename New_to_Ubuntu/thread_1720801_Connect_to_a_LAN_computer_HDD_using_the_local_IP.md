---
title: "Connect to a LAN computer HDD using the local IP"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by primach on 2011-04-03
Hey guys, i started using Ubuntu 2 days ago and so far it's an awesome experience.
While i was using windows i could access the PC HDD from my laptop just by writing the local IP of the pc on a folder path it was simple ,efficient & fast.
Can i do something like that while using ubuntu on both computers ? i've been searching for the past half hour on google and most guides are kinda complex for a new user just to do something simple like that. 

Thanks in advance!

---

### Post by Dutch70 on 2011-04-03
Hi and welcome to UF

I'm not quite sure what you're trying to do, but you can use remote desktop viewer to access the other computer.

---

### Post by Paqman on 2011-04-03
You can access a drive shared on your network through the Places > Network menu.

If you want it to be mounted automatically on boot instead of having to browse to it every time then you'll need to add an entry to your /etc/fstab file. Let us know if that sounds like what you want.

---

### Post by primach on 2011-04-03
Hey thanks for your replies guys!
> **Paqman said:**
> You can access a drive shared on your network through the Places > Network menu.

that sounds awesome , can you please tell me how can i share my HDD ? i mean how can i change the permissions because when i go to the hdd permissions it says : the permissions could not be determined.

---

### Post by Paqman on 2011-04-03
> **primach said:**
> Hey thanks for your replies guys!

that sounds awesome , can you please tell me how can i share my HDD ? i mean how can i change the permissions because when i go to the hdd permissions it says : the permissions could not be determined.

If it's a Windows share then you can't. Windows doesn't have a proper file permissions system, either on it's own filesystem or its network protocols. That shouldn't stop you from accessing the files on your share though.

If you really need to set permissions on a network share, then you can do so through /etc/fstab.

---

### Post by primach on 2011-04-03
> **Paqman said:**
> If it's a Windows share then you can't. Windows doesn't have a proper file permissions system, either on it's own filesystem or its network protocols. That shouldn't stop you from accessing the files on your share though.

If you really need to set permissions on a network share, then you can do so through /etc/fstab.
I see , i created a shared folder to drag there what i want to share, not that handy but it's better than nothing:P.

Anyway i mark the thread as solved thanks guys!

---

