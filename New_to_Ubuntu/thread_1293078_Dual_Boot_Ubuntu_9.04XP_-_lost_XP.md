---
title: "Dual Boot Ubuntu 9.04/XP - lost XP"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by charlieapples on 2009-10-16
Hello,

I recently rescued an old laptop with Ubuntu which worked excellently, so I tried it out on my main desktop and installed Ubuntu 9.04 to work alongside XP in its own partition, with GRUB handling the booting.

Sadly, when I try to boot into XP (wish I didn't have to) I get an error "NTLDR Missing" and have to start again.

I have looked on other threads for a solution and see that it may be a problem with the settings in grub's menu.lst, but I really haven't a clue where to begin to work out whether this is actually the case.

I have tried using my XP disk to run fixboot, in the hope that I might at least be able to get back to a single boot XP box, but it made no difference.

Could someone please help, or at least point me in the right direction to help myself.
Thank you

---

### Post by mike555 on 2009-10-16
check these out ... 
[http://www.google.com/search?q=ntldr+missing+fix&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=ntldr+missing+fix&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by charlieapples on 2009-10-16
> **mike555 said:**
> check these out ... 
[http://www.google.com/search?q=ntldr+missing+fix&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=ntldr+missing+fix&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

Thanks mike555  - if nothing else, being referred to a google search will sting enough to make a guy think harder ;)

In case anyone else has the same problem, what I got out of the searches was that you can use grub's edit function to mess around with how it boots up Windows. I found by findling with it that after changing rootnoverify (hd1,0) to rootnoverify (hd0,0) and deleting the map instructions, the boot worked. 

So there, it's simple. Now I have to figure out why...

---

### Post by oldfred on 2009-10-16
The change to your rootnoverify of (hd1,0) to (hd0,0) is changing it from your second hard drive to your first. It is as if when you installed Ubuntu it found windows on your second hard drive. Then you switched them in BIOS and then could not find the windows on the second drive. Ubuntu did not get lost as it uses UUIDs that do not change.

---

### Post by charlieapples on 2009-10-16
> **oldfred said:**
> The change to your rootnoverify of (hd1,0) to (hd0,0) is changing it from your second hard drive to your first. It is as if when you installed Ubuntu it found windows on your second hard drive. Then you switched them in BIOS and then could not find the windows on the second drive. Ubuntu did not get lost as it uses UUIDs that do not change.

Cheers oldfred. Teach a man to fish...

---

### Post by la3875 on 2009-10-16
Take a look at Hermanzone. I've had to repair my MBR a few times and the instructions there are flawless...

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

