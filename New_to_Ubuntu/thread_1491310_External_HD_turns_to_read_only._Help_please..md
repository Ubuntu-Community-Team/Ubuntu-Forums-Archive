---
title: "External HD turns to read only. Help please."
date: 2010-05-23
forum: New to Ubuntu
---

### Post by Buying_Some_Time on 2010-05-23
I've been using my 500GB WD External hard-drive for some time now, but today it won't take any downloads because it gives me a error that says that it's "read only", and I don't know why this is. I have not made any changes to my system, so I have no clue why this happened, can someone please help me? Thanks in advance. :)

---

### Post by Ozymandias_117 on 2010-05-23
What filesystem is it using?

---

### Post by Anxious Nut on 2010-05-23
As fas as i know this happens when a removable media device got unplugged without being unmounted or ejected!

I am not sure if there is another way, but the thing i do when this occurs is that i use Gparted (partition editor) and do the check option. This would check for errors and try to fix them, BUT files might get corrupted, so it is better to back up your stuff before starting the process. If that doesn't fix it, make sure you have a back up and then format it.

As i said, this is the way i do it, and am not sure if this is the only way or even if it is correct in the first place!

---

### Post by Buying_Some_Time on 2010-05-23
> **Ozymandias_117 said:**
> What filesystem is it using?

Fat32

---

### Post by Buying_Some_Time on 2010-05-23
@Anxious Nut: That can't be the problem, I never remove my Ext. HD so I don't see how that could've happened.

---

### Post by Buying_Some_Time on 2010-05-23
Anyone else any any suggestions?

---

### Post by razy60 on 2010-05-23
Hi, have you checked the security(i think it is permissions in ubuntu)settings you should be able to change them.

On occasion i have had this happen normally i remove the drive switch the system off completely then restart switch the drive back on and plug it back in.

The other thing to check what was the last thing you loaded onto it, and how full is it.

Raz

---

### Post by Buying_Some_Time on 2010-05-23
Thanks, razy60. That fixed my problem.

---

