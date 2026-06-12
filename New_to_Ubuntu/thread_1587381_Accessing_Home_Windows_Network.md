---
title: "Accessing Home Windows Network"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by n00b_1234 on 2010-10-03
Hey everyone,

I am new to ubuntu and trying to access any of my windows network shares.  I went through places > network > workgroup and did not see any of my windows shares.  My windows network name is asdf_1234.  How do i configure ubuntu to access these shares?

---

### Post by spiky001 on 2010-10-03
Have you set the win boxes to share?

---

### Post by kadalashvili on 2010-10-03
Try Places -> Connect to Server, then choose Windows share from the list of options and enter share details.

---

### Post by luvshines on 2010-10-03
Here is a nice guide:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by n00b_1234 on 2010-10-03
I have samba installed and configured with 
workgroup = asdf_1234

but i am still not seeing anything in the places > networking  folder....

---

### Post by Mark Phelps on 2010-10-03
On the MS Windows side, do you have this set up as a Work Group (XP & Vista) or as a Home Group (Win7 only)?  Because, if it's the latter, I don't believe that you can get access to it outside of Win7 -- even XP and Vista can't access Home Groups.

---

### Post by steve-shinn on 2010-10-03
> **Mark Phelps said:**
> On the MS Windows side, do you have this set up as a Work Group (XP & Vista) or as a Home Group (Win7 only)?  Because, if it's the latter, I don't believe that you can get access to it outside of Win7 -- even XP and Vista can't access Home Groups.

Set them all up as workgroups (incl Win 7). I am running XP, Vista & Win 7, and Ubuntu, and they all talk happily. You will need to sort out the firewalls at some stage, and quite possibly the IP tables on the Linux box.

---

### Post by luvshines on 2010-10-04
> **n00b_1234 said:**
> I have samba installed and configured with 
workgroup = asdf_1234

but i am still not seeing anything in the places > networking  folder....

You don't need Samba server setup on the Linux side for accessing your Windows shares. Only thing you need is Samba client and a perfectly working network(DNS, IP's etc)

---

