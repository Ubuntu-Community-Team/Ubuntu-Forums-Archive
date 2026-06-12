---
title: "Ubunbtu update issue"
date: 2011-08-20
forum: New to Ubuntu
---

### Post by Nikhil Kenvetil on 2011-08-20
Hi
 
I went into the Update Manager and updated 10.04 to 10.10, but when i go to About Ubuntu,it still shows 10.04.. did i go wrong somewhere??

thanks in advance 

moreover i see two options at the bootscreen, Ubuntu 2.6 and 2.6. They differ, however, by some points at the end.. like some .33 and .26.. i hope i am makin sense..

---

### Post by fabricator4 on 2011-08-21
> **Nikhil Kenvetil said:**
> [COLOR=black][FONT=Verdana]Hi[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]I went into the Update Manager and updated 10.04 to 10.10, but when i go to About Ubuntu,it still shows 10.04.. did i go wrong somewhere??

thanks in advance 

moreover i see two options at the bootscreen, Ubuntu 2.6 and 2.6. They differ, however, by some points at the end.. like some .33 and .26.. i hope i am makin sense..[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR]

It sounds like 10.04 LTS.  What is the result of 

```
uname -a
```

Chris

---

### Post by Sef on 2011-08-21
> i see two options at the bootscreen, Ubuntu 2.6 and 2.6. They differ,  however, by some points at the end.. like some .33 and .26.. i hope i am  makin sense..

Yes, .33 is an update from .26. .33 has some security fixes that .26 does not have.

---

### Post by Nikhil Kenvetil on 2011-08-21
> **fabricator4 said:**
> It sounds like 10.04 LTS.  What is the result of 

```
uname -a
```

Chris
thnx.. i'll let u know about that ASAP.. which won't be at least 2 hours from now, as i am not carrying my laptop..

---

### Post by Nikhil Kenvetil on 2011-08-21
> **Sef said:**
> Yes, .33 is an update from .26. .33 has some security fixes that .26 does not have.
thnx for the reply Sef.. so does that mean i am on 10.10? but also, there is another issue.. on my boot screen, it shows both of them, 2.6.x.x.x.33 and 2.6.x.x.x.26.. how do i get rid of the latter? pardon the xs.. i am not sure how many numbers are there

---

### Post by Old_Grey_Wolf on 2011-08-21
Kernel 2.6.32-33 is not 10.10 it is the current Kernel for 10.04.

---

### Post by Nikhil Kenvetil on 2011-08-23
> **Nikhil Kenvetil said:**
> thnx.. i'll let u know about that ASAP.. which won't be at least 2 hours from now, as i am not carrying my laptop..
hey.. sorry about the deyaled response.. this is what i got after i typed uname -a: 
 
**Linux M 2.6.32.33-generic#72-Ubuntu SMP Fri Jul 29 21:07:13 UTC 2011 x86_64 GNU/Linux**

---

### Post by kyletstrand on 2011-08-23
> **Nikhil Kenvetil said:**
> hey.. sorry about the deyaled response.. this is what i got after i typed uname -a: 
 
**Linux M 2.6.32.33-generic#72-Ubuntu SMP Fri Jul 29 21:07:13 UTC 2011 x86_64 GNU/Linux**

Doesn't sound like it updated.  If you go back to your update manager, do you still see the update to 10.10 option?

---

### Post by fabricator4 on 2011-08-23
> **Nikhil Kenvetil said:**
> hey.. sorry about the deyaled response.. this is what i got after i typed uname -a: 
 
**Linux M 2.6.32.33-generic#72-Ubuntu SMP Fri Jul 29 21:07:13 UTC 2011 x86_64 GNU/Linux**

Yes, as already stated that is the current kernel for 10.04 LTS.

To remove old kernels, open synaptic package manager under System -> Administration and delete them.  The easiest way I've found is to select "status" and "installed", then type 2.6.32 in the search box.  All versions should then be listed, and you can mark the old ones for removal.

Do not remove the current kernel (2.6.32-33) as well or you will not be able to boot at all.  Many people also like to leave the previous kernel there just in case the system is broken and they need to boot into it.  Personally, if the system seems OK after a few days I'm happy to delete all but the current one.

You could try the update again if it's still offered, but do make sure your important data is backed up.  While the upgrade is much more reliable than it used to be, there's still a chance of something going wrong.  The likelihood of this happening seems to be directly proportional to how heavily configured your system is.

Personally, I recommend downloading the ISO and re-installing because it's much faster, however this does not keep all the installed programs etc.

Chris.

---

