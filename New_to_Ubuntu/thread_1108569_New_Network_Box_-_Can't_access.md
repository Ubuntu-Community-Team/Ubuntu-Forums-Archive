---
title: "New Network Box - Can't access"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by Pondoro on 2009-03-27
I installed Ubuntu on my third (oldest) PC. It immediately found the shared folders on my two Windows PC's. This was with a Net Gear wired router. Worked great. I bought a new Linksys router and hooked it up. The two Windows PC's still see each other but now the Ubuntu machine cannot open the shared folders on the other machines. I see "Microsoft Network" and when I open it I see "Home." This is just like before, but now I cannot open "Home."

Any ideas what I need to do to connect to the shared spaces?

I am able to go through the router to the internet just fine but I cannot open shared folders on the other machines.

Thanks

---

### Post by spcwingo on 2009-03-27
Run this command in terminal:

```
sudo apt-get install samba smbfs
```

After that add the Win machines to your hosts list.  The easiest way to do this is to open system>admin>network, then unlock, enter your password, and click the "hosts" tab.  Click add and enter the information for your win machines.  It helps to go through your router setup and assign the machines that will be hosting shares a static IP address.  This will prevent them from receiving a different IP address so you won't have to worry about accessing shares in Ubuntu again unless something goes terribly wrong.

---

### Post by Pondoro on 2009-03-27
I did the command. I go to system/admin/network tools - where and how do I "unlock"? I don't see it...

---

### Post by spcwingo on 2009-03-27
> **Pondoro said:**
> I did the command. I go to system/admin/network tools - where and how do I "unlock"? I don't see it...

Not network tools, just network.  ;-)

---

### Post by superprash2003 on 2009-03-28
try opening this way [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by Pondoro on 2009-03-28
There is no system/admin/network, only network tools. But I rebooted all the computers plus the network box and now the Ubuntu machine sees the shared areas! So all is well.

---

