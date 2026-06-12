---
title: "[SOLVED] What does this error msg mean?"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by mariane_08 on 2008-12-27
And do I need to worry about it since everything else seems OK?

On boot up just before GRUB theres a brief text error message flashes up
" error...00.000400 appeture greater than 4GB,..Ignoring"

What exactly does this mean?

---

### Post by oilchangeguy on 2008-12-27
> **mariane_08 said:**
> And do I need to worry about it since everything else seems OK?

On boot up just before GRUB theres a brief text error message flashes up
" error...00.000400 appeture greater than 4GB,..Ignoring"

What exactly does this mean?

are you sure you've got the message correct? i copied and pasted it into google, and got nothing.

---

### Post by northern lights on 2008-12-27
> **oilchangeguy said:**
> are you sure you've got the message correct? i copied and pasted it into google, and got nothing.
The OP meant "aperture".

@the OP:

I don't think you need to worry about the message causing problems or being related to actual problems. It sounds like a kernel bug (i.e. the newer kernel communicationg with the BIOS).

More than 4 GB of (Graphics) aperture sound like 2013 rather than 2008 hardware.

Are you using a shared memory graphics device?

If so, try to lower aperture in the BIOS to "remove" the error message.

---

### Post by sdennie on 2008-12-27
If the kernel has decided to ignore it, it's probably safe for you to ignore it too.  My guess is that it's the BIOS reporting invalid values and the kernel is smart enough to ignore it.  A BIOS update may fix the problem but, it's probably not a pressing issue unless you are having some other problems with your machine.

---

### Post by mariane_08 on 2008-12-27
Yes I did post the error msg incorrectly, flashes by so quickly. It should be:

" error  0.004000 aperture greater than 4GB,..Ignoring"

I'm not particularly bothered by it at this point as such. The only slight anomaly that's happening is when I launch Firefox there's sometimes an extremely brief jitter/squigle of colours before it launches. It's so brief, no more than a blink of the eye, and is of little practicle consequence.

Yes my laptop is using shared graphics memory (32MB  I think?) Maybe configure it higher?

---

### Post by northern lights on 2008-12-27
> **mariane_08 said:**
> Yes my laptop is using shared graphics memory (32MB  I think?) Maybe configure it higher?

Couldn't say. Play around with the options your given in the BIOS and see whether they have an effect on the jitter.

Anyhow, this is nothing to seriously worry about.

---

