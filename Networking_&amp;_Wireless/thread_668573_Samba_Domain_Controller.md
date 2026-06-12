---
title: "Samba Domain Controller"
date: 2008-01-15
forum: Networking &amp; Wireless
---

### Post by lenswipe on 2008-01-15
Hi there

i have linux ubuntu Gutsy gibbon 71.0 Desktop edition. I want to make it into a Samba domain controller. So i spoke to the guy who manages my school system (hes very good with this sorta stuff) and he told me that i didnt need ubuntu server for an ubuntu domain controller. And that all i need to do was to edit some config file in /etc/samba and something to do with changing something to say domain controller = as or something like that. Does anyone know how to do it this way?

If so please say and keep it as simple as possible im quite new to ubuntu.

Thanks

-L

EDIT: I wont need alot of security for it as its only for a home network. It will only serve 2 or 3 computers....

---

### Post by metoor30 on 2008-01-15
What type of domain controller are you talking about?  Do you want a legacy Windows NT style DC, a Windows Active Directory DC or a Samba/LDAP solution?  What OSes will be using this DC for authentication?

---

### Post by lenswipe on 2008-01-15
> **metoor30 said:**
> What type of domain controller are you talking about?  Do you want a legacy Windows NT style DC, a Windows Active Directory DC or a Samba/LDAP solution?  What OSes will be using this DC for authentication?


oops sorry forgot to say!

yeah... in the first instance ill just be authenticating ubuntu gutsy 7.1

But at some later point i will be going on to authenticate windows XP PRO


however XP isnt too important just now as i dont have it just yet so for the moment just tell me how to authenticate ubuntu 7.1 gusty


thanks :D

---

### Post by metoor30 on 2008-01-15
Since this is such a small network, what is the reason you want to have centralized authentication (Just curious)?

The thread below is something that would probably work for you, but unless you provide specific requirements, I cannot tell you if it will meet your needs.  Hope this helps.

[http://ubuntuforums.org/showthread.php?t=640760&highlight=samba+ldap](http://ubuntuforums.org/showthread.php?t=640760&highlight=samba+ldap)

---

