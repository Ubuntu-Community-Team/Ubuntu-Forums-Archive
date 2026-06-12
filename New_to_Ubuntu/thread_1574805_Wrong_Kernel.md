---
title: "Wrong Kernel?"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by Jolicoeur on 2010-09-14
I noticed that my Ubuntu 10.04.1 has kernel 2.6.31, should I have 2.6.34 installed?  If yes, how do I do this?

---

### Post by Shpongle on 2010-09-14
No its fine , when a new kernel becomes available you will be notified and you can install it via update manager or synaptic

---

### Post by snowpine on 2010-09-14
Please post the output of:

```
uname -a
```

2.6.32 is the kernel for Ubuntu 10.04. The only reason I can think of why you'd have 2.6.31 if you're using the real time (rt) kernel.

Ubuntu 10.04 will never have 2.6.34; 2.6.32 will be the one and only supported kernel until 10.04 reaches "end of life" in April 2015.

---

### Post by Jolicoeur on 2010-09-15
I checked and I do have 2.6.31 should I somehow change it to 2.6.32?  When I boot I have to press esc and choose 2.6.31 because it won't boot 2.6.32.

---

### Post by snowpine on 2010-09-15
Please follow my advice from the previous post and tell us the output of 'uname -a'.

> **Jolicoeur said:**
> I checked and I do have 2.6.31 should I somehow change it to 2.6.32?  When I boot I have to press esc and choose 2.6.31 because it won't boot 2.6.32.

Are you saying you **do** have 2.6.32, but it doesn't work? That is a different question. :) If this is the case, what symptoms/errors do you get when trying to boot 2.6.32?

---

### Post by Jolicoeur on 2010-09-15
This is what shows up:  2.6.31-22-generic #63-Ubuntu SMP Wed Aug 18 22:54:26 UTC 2010 i686 GNU/Linux

It does boot up if I choose 2.6.31 at boot-up.  will not boot up if I choose any other option.

---

### Post by snowpine on 2010-09-15
Did you upgrade from Karmic? 2.6.31 was the Karmic kernel.

If it is working OK then there is nothing to worry about.

If you want help you need to be more specific about what the "other options" are, and what specifically happens when you try to boot them. "It doesn't work" is not enough information for anyone to help you troubleshoot, I'm afraid.

---

### Post by Jolicoeur on 2010-09-15
I upgraded from the previous version, I have 10.4.1 now, it works if I press escape at boot up and then choose 2.6.31.  There is the option to choose 2.6.32, if chosen it won't boot. Perhaps since it does work I should just wait until the next up*date.*

---

