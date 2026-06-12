---
title: "trouble with windows 7 share"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-06-12
I have samba installed with the workgroup matching what the window 7 machine has both machine have no fire wall turned on. I can see the windows 7 machine but it will not let me in but using the nautilus file share for a folder on ubuntu the windows 7 machine can see it and talk to it. what am i missing?

---

### Post by cariboo on 2010-06-12
Have you got file sharing turn on in Windows 7? I'm not close to a system running Win7, but if you go to the Control Panel, it should be easy to find.

---

### Post by garvinrick4 on 2010-06-12
> **lance bermudez said:**
> I have samba installed with the workgroup matching what the window 7 machine has both machine have no fire wall turned on. I can see the windows 7 machine but it will not let me in but using the nautilus file share for a folder on ubuntu the windows 7 machine can see it and talk to it. what am i missing?

Windows will not let you in unless Windows has a password installed in it's system. You need to have password turned on in Windows machine in other words. And of course share which ever folders you want to. It is a Workgroup not a Homegroup.

---

### Post by Jerry N on 2010-06-12
> **garvinrick4 said:**
> Windows will not let you in unless Windows has a password installed in it's system. You need to have password turned on in Windows machine in other words. And of course share which ever folders you want to. It is a Workgroup not a Homegroup.

No - a password is not required in Win 7.  On the folder to be shared under sharing options, share with "Specific People".  Then select "Everyone" (unless you want to restrict your sharing) and ADD everyone to the list.  At that point, you can change permissions if you desire.  In Control Panel, select "Network & Sharing" and "Advanced Sharing Options".  This panel will allow you to select what you want to share and you can select "Turn on" or "Turn Off" Password Protected Sharing.  

Jerry

---

