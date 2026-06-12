---
title: "Powertop Completely Locks Computer"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by mnttnlyzr on 2010-09-19
Something I'm doing?

I installed Powertop as any other program, opened terminal and typed "sudo powertop".

The powertop dialogue opens for the five seconds that it takes measurements and then the whole computer locks up and I have to press and hold the power button because that's the only button that'll do anything.

No other programs running.

I can type "powertop" in the terminal and it won't lock up; it only locks when running as su.

I've uninstalled and reinstalled twice. No dice.

Any tips appreciated. I found one "lock" bug report that was filed in March of this year and only one person experiencing, with no help there.

---

### Post by kerry_s on 2010-09-19
becareful with that, the wrong settings can fry your board, happened to a friend of mine.

---

### Post by Henk Poley on 2010-09-20
You should subscribe to the powertop mailinglist and report the bug to the powertop devs directly: [http://lists.lesswatts.org/mailman/listinfo/discuss](http://lists.lesswatts.org/mailman/listinfo/discuss)

It shouldn't touch very dangerous stuff, this is probably a kernel bug somewhere.

---

