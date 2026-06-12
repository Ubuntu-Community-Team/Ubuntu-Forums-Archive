---
title: "synaptic wrong password"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by cmcanulty on 2011-03-27
I have a very simple password and starting today synaptic won't accept it. I can only open synaptic from terminal. How can I fix this. I found several posts on google about this but no solution.

---

### Post by sisco311 on 2011-03-27
> **cmcanulty said:**
> I have a very simple password and starting today synaptic won't accept it. I can only open synaptic from terminal. How can I fix this. I found several posts on google about this but no solution.

Make sure that gksu's *authentication mode* is set to sudo:
```
gksu-properties
```

---

### Post by aaaaalex on 2011-03-27
Are you saying that after you keyed in your password into the authentication dialogue it just goes back to asking it?

If you simply (X) the authentication dialogue you will find the authentication has strangely happened in the background. 

I am sure there is a bug report for taht somewhere - if it happens to me (sporadically and only on one system) i simply do that for the time being.

---

### Post by sisco311 on 2011-03-27
> **aaaaalex said:**
> 
I am sure there is a bug report for taht somewhere - if it happens to me (sporadically and only on one system) i simply do that for the time being.

Yep: [lpbug]649939[/lpbug], but that's a bug in policykit. As far as I know, synaptic still uses gksu.

---

### Post by cmcanulty on 2011-03-27
I have a single letter password that works fine except starting this afternoon it says incorrect for synaptic works in software center can I reinstall synaptic or would that cause a disaster?

---

### Post by aaaaalex on 2011-03-27
Did you try changing the password? AFAIK anything should be allowed but then again that may not be very far. 

I highly doubt that a reinstall of synaptic would fix this. Any ideas sisco?

---

### Post by cmcanulty on 2011-03-27
I got it back! I took a chance and used the Ubuntu Tweak restore utility and it undid whatever the problem was. I have been backing up with that for a while but never tried using it before. Thanks I will mark as solved.

---

