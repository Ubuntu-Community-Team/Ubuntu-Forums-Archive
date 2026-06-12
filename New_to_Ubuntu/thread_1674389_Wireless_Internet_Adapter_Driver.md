---
title: "Wireless Internet Adapter Driver?"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by Honest AMish on 2011-01-23
Good evening!

I'm currently on the brink of deciding whether or not to switch to Ubuntu. My only means of accessing the internet are via a WG111v3 wireless internet adapter, and from the NetGear website, I have been unable to find a Linux supported driver. 

Is there perhaps a Ubuntu-dedicated website that offers an alternative driver, or am I SOL? 

Thanks in advance!

---

### Post by Sleven7 on 2011-01-24
When you boot from the Ubuntu Live cd, does it connect to the internet?

---

### Post by [Snc] on 2011-01-24
> **Honest AMish said:**
> Good evening!

I'm currently on the brink of deciding whether or not to switch to Ubuntu. My only means of accessing the internet are via a WG111v3 wireless internet adapter, and from the NetGear website, I have been unable to find a Linux supported driver. 

Is there perhaps a Ubuntu-dedicated website that offers an alternative driver, or am I SOL? 

Thanks in advance!

Is "System" -> "Administration" -> "Additional Drivers" empty?

I found, that on my laptop a boot from the live USB cannot run wifi, but additional drivers are available, but will not install (on to the live USB), so a clean install with cable connection would solve the wifi problem.

---

### Post by 3rdalbum on 2011-01-24
Try booting up the Ubuntu Desktop CD and running the live session. If your Wifi device works during this session, then it will work in the installed system. Even if it doesn't work on the desktop CD, you might be able to get it working in the installed system by using the Additional Drivers program.

Ubuntu usually comes with the drivers you need - few of us install drivers from a vendor's website.

---

### Post by TBABill on 2011-01-24
The WG111v3 uses the RealTek RTL8187B chipset. If you search the forums for this you'll see many posts of users who got it going. Realtek is well supported and there are plenty of users who can assist if it doesn't just work out of the box. Sometimes a small change will fix it but until you try it live (without installing) to see if it just works out of the box I can't really say. If you're willing to install even if it doesn't work in the live session and then post for assistance you should be up and running pretty quickly.

---

