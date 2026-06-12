---
title: "Why is my laptop beeping?"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by gymophett on 2009-04-19
I have a Dell Inspiron 5100. It's been put away for a while, and now I'm trying to fix it. Whenr I turn it on, it just beeps, constantly! I tried installing Ubuntu 8.10 on it but it wont work, it creates an error, and the live cd runs extremely slow.
Did some of the ram burn out? How can I know for sure what is wrong with it? I would love to fix it!
Thanks for ya'lls help! :)

---

### Post by halitech on 2009-04-19
does it start beeping as soon as you turn it on or does it take a little bit for it to start? 

to test the ram, you could try running memtest86+ from the boot menu on the live cd.

---

### Post by Therion on 2009-04-19
> **gymophett said:**
> I have a Dell Inspiron 5100. It's been put away for a while, and now I'm trying to fix it. Whenr I turn it on, it just beeps, constantly!
Why was it put away in the first place, was it not acting normally?  When you say you're tyring to fix it do you mean a previous problem or do you mean you're trying to fix the beeping and current poor performance issues?

Is there a pattern to the beeping (e.g. long beep followed by a short, or two shorts and then a long beep, etc.), or is it one long continuous beep or what?  The reason I ask is because my first suspicion is that you're hearing POST-code beeps.  POST-code beeps are indicative of something in the hardware profile not passing POST (Power-On Self-Test), and frankly, that's never good.  

If I were you I'd probably get on the horn with Dell support and go straight to the source.  I've built a lot of PC's but trying to diagnose a notebook that's not passing POST would be way beyond me, unless you want to try experimenting by removing one stick of RAM at a time and things like that...

My suggestion:  Call Dell.  It's probably what you'll wind up doing anyway.

---

### Post by Iowan on 2009-04-19
Constant beep, or POST series of beeps?

---

### Post by llamabr on 2009-04-19
While trouble shooting, you can disable the beep by doing:

```
sudo rmmod pcspkr
```

---

### Post by Volt9000 on 2009-04-19
I don't think it's a POST beep error because if it is, then the computer wouldn't boot up past the POST to begin with.

I'm thinking maybe one of the keys are physically stuck. It may not look stuck on top, but the mechanism underneath is fixed to the "pressed" position.
Of course if this were the case, if you were to open up something like Text Editor you should see the key appearing over and over again, unless it's a "soft" key such as Ctrl or Alt.

With the computer off, try pressing each key on the keyboard. Press it down quite deliberately and release it. Do this for every key and if this is the problem then maybe the key will get unstuck.

---

### Post by Wiebelhaus on 2009-04-19
> **Volt9000 said:**
> I don't think it's a POST beep error because if it is, then the computer wouldn't boot up past the POST to begin with.

I'm thinking maybe one of the keys are physically stuck. It may not look stuck on top, but the mechanism underneath is fixed to the "pressed" position.
Of course if this were the case, if you were to open up something like Text Editor you should see the key appearing over and over again, unless it's a "soft" key such as Ctrl or Alt.

With the computer off, try pressing each key on the keyboard. Press it down quite deliberately and release it. Do this for every key and if this is the problem then maybe the key will get unstuck.

If the OS loads , I"d unplug the keyboard and see if it continues.

---

### Post by Volt9000 on 2009-04-19
> **sx66gns said:**
> If the OS loads , I"d unplug the keyboard and see if it continues.

Considering this is a laptop, that's probably not very easy to do. ;)

---

