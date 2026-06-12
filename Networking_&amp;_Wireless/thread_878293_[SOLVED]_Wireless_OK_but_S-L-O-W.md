---
title: "[SOLVED] Wireless OK but S-L-O-W"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by mikex on 2008-08-02
Put Ubuntu on my hp laptop and got the wireless working, but something is not right, it is VERY slow. I'm working with two HDs, the original has Vista on it so I can go back to that if this doesn't work out. When I go back to the Vista HD, the wireless is lightening-fast like it always has been. But the Ubuntu installation is so slow it isn't really usable. When connected with a cat-5 cable, the networking is OK.

But if I can't get the wireless speed up I can't use it on the laptop. Again, it connects to the access point fine, but the speed is way too slow to be used.

Any ideas?

---

### Post by cybrsaylr on 2008-08-02
I'm having the exact same problem with my dual booted new Toshiba laptop.
When on Vista the wireless is very fast but when I switch to Ubuntu the wireless slows down almost like dialup at times. When hardwired both OSs are very fast. 
I posted this problem on the thread here a few days back and got no response as yet.

---

### Post by jualin on 2008-08-02
Maybe an IPV6 issue. Write > about:config in your Firefox Address bar and then search for "ipv6" and toggle the status from "false" to "true". This helped me a lot with my internet being slow. Hope this works!

---

### Post by jualin on 2008-08-02
I just noticed I gave you my suggestion in the other thread you created. Forgive me for the double post.

---

### Post by cybrsaylr on 2008-08-03
FWIW jualin helped solve a similar problem in my thread.

Here's how it went:
[http://ubuntuforums.org/showthread.php?t=872114](http://ubuntuforums.org/showthread.php?t=872114)

---

### Post by mikex on 2008-08-03
The IPv6 trick doesn't help me.

When I type iwconfig - it reports that my wireless speed is 1 Mb/s.

Should be more like 54Mb/s! I'm sitting right next to the wireless router. Also I get reports of different speeds sometimes. I don't get these anomalies in Windoze, it's always super-fast anywhere in the house. 

Is the driver to blame for this - where is the best driver located for the Broadcom chipset? Is it the one Ubuntu installs in the restricted driver area?

Has this driver been tested well? 

What else can I do?

---

### Post by mikex on 2008-08-03
This solved it. I recommend everyone try this solution -

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by jualin on 2008-08-03
Glad to hear you got it all working now.

---

### Post by cybrsaylr on 2008-08-03
Glad you solved it.
With the faster speeds I get now, I need Windows even less than before.

---

### Post by jualin on 2008-08-03
> **cybrsaylr said:**
> Glad you solved it.
With the faster speeds I get now, I need Windows even less than before.

Eventually you won't need windows anymore. Most things that you do in Windows you can do in Ubuntu. Even some games with a program called Cedega. :guitar:

---

