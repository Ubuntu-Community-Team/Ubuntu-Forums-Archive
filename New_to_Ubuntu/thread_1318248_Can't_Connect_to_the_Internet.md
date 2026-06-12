---
title: "Can't Connect to the Internet"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by Shadow21 on 2009-11-07
I'm dual booting Ubuntu 9.10 with Windows XP and I can't connect to the internet in Ubuntu for some reason (I can in XP though).

When I had Ubuntu installed as the only OS on my computer it was able to connect to my router but now since I've dual booted it with XP it can't find any routers for some reason.

How can I make it find and connect to the internet?

---

### Post by blazemore on 2009-11-07
Are you connecting with a cable? or wirelessly?

---

### Post by Shadow21 on 2009-11-07
> **blazemore said:**
> Are you connecting with a cable? or wirelessly?

I'm trying to connect wirelessly.

---

### Post by Tea4all on 2009-11-07
Go to System > Administration > Restricted Drivers. Install the one for your card. Need to be connected to the internet through a cord though.

---

### Post by Shadow21 on 2009-11-07
> **Tea4all said:**
> Go to System > Administration > Restricted Drivers. Install the one for your card. Need to be connected to the internet through a cord though.

I just tried that and it wouldn't even let me connect to the internet when it was wired. I didn't see Restricted Drivers either.

---

### Post by blazemore on 2009-11-08
You connect an ethernet cable from your computer to the router.

---

### Post by Shadow21 on 2009-11-08
> **blazemore said:**
> You connect an ethernet cable from your computer to the router.

That's what I did.

---

### Post by Lateralis on 2009-11-08
Have you updated/reinstalled Ubuntu since you started dual booting?  Or did you install XP after an Ubuntu installtion which was previously working?  That is, is this a different version of Ubuntu that you are using to the one which you knew used to work.  

And for completeness, what does the following give you?

```

sudo lshw -C network

```

---

