---
title: "How much swap space for 4GB RAM?"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by Tokiopop on 2011-01-26
I've heard various things, from needing double the RAM you have to almost nothing. 

I do want the ability to suspend/hibernate, so I guess I need 4GB. But do I really need double my RAM? 

Thanks.

---

### Post by Ocxic on 2011-01-26
1.5x current RAM(so 6GB for you), this will allow all data in memory to be saved to disk when hibernating, and a little left over just in case.

---

### Post by cgroza on 2011-01-26
If you do not need hibernation 0 MB.
EDIT: I saw that you need hibernation. 4.5 GB would be fine because your system will not swap at all, no need to waste space.

---

### Post by stmiller on 2011-01-29
The 'double your ram' thing was back in the 128MB ram days.

There is no need for swap larger than 2GB max. :)

Cheers,

---

### Post by uRock on 2011-01-29
I usually do 2GB of Swap no matter haw much RAM a machine has. 

I have used up 4GB RAM and 2GB Swap to where the system just locked up. All you have to do is run Wireshark while torrenting.

---

### Post by Rab22 on 2011-01-29
I do 2x until 4GB of memory, then I continue with just 6GB.

I've never seen a need for 8GB yet.

---

### Post by HermanAB on 2011-01-29
Common guys, don't confuse the issue.  The OP wants to use hibernate and suspend, so he needs at least 1.5x RAM for /swap, since the system needs to write RAM and the system status to disk and it uses the swap space for that.

---

### Post by Rab22 on 2011-01-30
> **HermanAB said:**
> Common guys, don't confuse the issue.  The OP wants to use hibernate and suspend, so he needs at least 1.5x RAM for /swap, since the system needs to write RAM and the system status to disk and it uses the swap space for that.

Yes, I agree. Sorry, wasn't trying to confuse anyone :)

---

### Post by thenickrulz on 2011-01-30
I would say 5-6

---

