---
title: "clamav reports dangerous script in libgda"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by nerdy_kid on 2009-08-25
Hi, I just did a scan of my pc, and clamav turned up "/usr/share/libgda-4.0/web/jquery.js: PUA.Script.Packed-2 FOUND"

Is this anything to be concerned about?

---

### Post by philcamlin on 2009-08-25
linux cant get viruses so i d dont know why your really scanning your pc but anyways its most likely a false positive :)

---

### Post by nerdy_kid on 2009-08-28
Linux can get viruses: [http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)
I thought it strange that a dangerous script would turn up in the system.

---

### Post by natravis on 2009-08-28
> **nerdy_kid said:**
> Linux can get viruses: [http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)
I thought it strange that a dangerous script would turn up in the system.

You are correct in saying that Linux can get viruses. Phil was on the right track though because the ability for a virus to damage a Linux based system and one to damage a Windows based system is very different. I think that I agree with Phil about the false-positive, though I am unsure how to test this. Perhaps you should ensure that your system is fully up-to-date and that you have the latest virus definitions in ClamAV. I work at GeekSquad, and some anti-virus utilities get picked up as viruses regularly because of the way that they access the system. Seeing as libgda is a database tool for GNOME, I could see its potential for being mistaken as a virus.

---

### Post by hollerith on 2010-03-01
I got this too.  clamav doesn't like jquery apparently.  All we can do is make sure we have genuine jquery and trust the author, as it would be a great place to hide some malware now.

---

### Post by Sir Jasper on 2010-03-01
Hi,

So far as I am aware you can upload any file (linux or windows) to virustotal for checking against 30 some virus products.

My regards

---

### Post by TurnOfTide on 2010-03-01
Viruses rarely cause damage anyway... that is so 80's. Virus writters are making all the money from spam and botnets and thus, spam. I never ran AV on windows because 1) It consumes resources, which is the same thing malware does, thus imo making resident scanners viruses themselves 2) never got any malware because i didn't go and run every girls dancing on my desktop program i could find

---

### Post by Sir Jasper on 2010-03-01
Hi TurnOfTide,

Which establishment awarded your degree in Computer Science?

I ask because I find your above response amazing, including the 80&#347; reference.

My regards

---

