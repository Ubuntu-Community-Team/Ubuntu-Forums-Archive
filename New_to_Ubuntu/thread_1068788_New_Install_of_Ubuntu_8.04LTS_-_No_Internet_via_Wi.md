---
title: "New Install of Ubuntu 8.04LTS - No Internet via Wired Connection"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by UKCamaroSS on 2009-02-13
Hello,

I have just installed Ubuntu 8.04 on a new pc that has Windows XP installed on it.

With Xp I can access the internet, download updates etc, but with Ubuntu I can not access the internet.

I am using a wired connection.

Can anyone talk me through some steps to trouble shoot / fix this?

Thanks,:confused:

---

### Post by antonius uno on 2009-02-13
what have you tried so far? can you reach your router via your browser?

---

### Post by UKCamaroSS on 2009-02-13
> **antonius uno said:**
> what have you tried so far? can you reach your router via your browser?

I dont know Linux well, so have not tried anything really.

I read that the wired connection should just work.. wireless might cause issues, but apparently not wired, so I'm totally thrown!

I can not access my router via Ubuntu, but I can via XP.

Serching just now I have found this "lspci" (not sure what it does exactly, but saw it on another thread... part of the output is:

Ethernet Controller: silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 2)

And I have now just searched Ubuntu forums for SiS 191 and found out:sis191 does not work according to the Hardware Support Components Wired Network Card Summary.

So, can I download a driver to make it work - or do I need to get a wireless adapter?

Thanks,

---

### Post by halovivek on 2009-02-13
Are you using the internet connection is auto. or you have to give the manual configuration of the internet? giving the ip address manually?

---

### Post by UKCamaroSS on 2009-02-13
> **halovivek said:**
> Are you using the internet connection is auto. or you have to give the manual configuration of the internet? giving the ip address manually?

Hello,

I have tried it both ways, but still no luck.:confused:

---

### Post by unixeducation on 2009-02-13
Could you please paste the output of the following command here:

```
lspci -k
```

Hope we can help.

---

