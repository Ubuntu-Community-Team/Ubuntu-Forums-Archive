---
title: "problem with pidgin...urgent!"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by heyyy on 2009-08-06
i tried to add a hotmail contact to my (msn) live account 
and although the contact can see me i cant see him.why?
i cannot even start a conversation with the particular contact because i dont see him in the buddy list but he can
some help

---

### Post by LowSky on 2009-08-06
sorry i dont have msn account, but try a progrma called **amsn**, its in the repos.

---

### Post by heyyy on 2009-08-06
is there a way to see all the contacts i have in a folder somewhere on system?

---

### Post by heyyy on 2009-08-06
> **LowSky said:**
> sorry i dont have msn account, but try a progrma called **amsn**, its in the repos.

this is out of the subject
i use pidgin and having a problem

---

### Post by wencin on 2009-08-06
maybe you can try this...
in pidgin "buddy list" window, select buddies->show and tick the options you want

---

### Post by abelta on 2009-08-06
Is the problem persistent if you restart your machine?

Anyway, the safest way to debug the problem is firing Pidgin from the command line (command would be pidgin), going through the process of adding your msn account (delete it first to be sure), trying to start a conversation, etc... and see if you get any error message in the command line.

I hope it helps.

---

### Post by heyyy on 2009-08-06
> **wencin said:**
> maybe you can try this...
in pidgin "buddy list" window, select buddies->show and tick the options you want

i've already tried that didnt work
i have other contacts where i can talk to them but i just cant see the specific one
he can see me and start a conversation though

---

### Post by fennec_fox on 2009-08-06
Can you not see any MSN contacts or just a certain individual? They could accidentally have themselves hidden. If it's all of your MSN contacts I can see there being a configuration issue. If it's just one, check if they show up in offline users at all. If they are in offline users find out if you can open a window with them and communicate.

---

### Post by heyyy on 2009-08-06
> **fennec_fox said:**
> Can you not see any MSN contacts or just a certain individual? They could accidentally have themselves hidden. If it's all of your MSN contacts I can see there being a configuration issue. If it's just one, check if they show up in offline users at all. If they are in offline users find out if you can open a window with them and communicate.

no its only on one specific that i cant see anywhere

---

### Post by abelta on 2009-08-06
Could it be that you have accidentally deleted that buddy? Try adding him again: Buddies > Add buddy.

---

### Post by heyyy on 2009-08-06
after some workaround... i restarted the pidgin and gave me the following message:
```
Buddy list synchronization issue in user@live.com (MSN)

theotheruser&#8203;@hotmail.co&#8203;m on the local list is inside the group "Buddies" but not on the server list. Do you want this buddy to be added?
```

i clicked yes
but could someone explain to me what server list is...?

---

### Post by abelta on 2009-08-06
That happens to me when I delete a contact/buddy in Pidgin on one computer (i.e. at work), then get home and start Pidgin and it warns me that the local buddy list is desynchronized with the list at the server. There are two separate buddy lists: one in your local machine and one at the "main" server in Microsoft.

---

### Post by heyyy on 2009-08-06
> **heyyy said:**
> after some workaround... i restarted the pidgin and gave me the following message:
```
Buddy list synchronization issue in user@live.com (MSN)

theotheruser&#8203;@hotmail.co&#8203;m on the local list is inside the group "Buddies" but not on the server list. Do you want this buddy to be added?
```

i clicked yes
but could someone explain to me what server list is...?

and when im clicking yes it gives me: 
```
Unable to add "theotheruser@hotmail.co&#8203;m".

The username specified is invalid.
```

---

