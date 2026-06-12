---
title: "dead keyboard during memtest"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by Daniel1994 on 2009-07-21
I am running memtest on my computer, and it shows "pass complete, no errors. Press esc to exit"
That's all good, but my keyboard is dead:S

Is it dangerous to force-shutdown during a memtest?

---

### Post by Sidewinder1 on 2009-07-21
Perhaps our memtests are different, I'm running Hardy. My memtest runs forever (at least it did in Gutsy, never really tried it in Hardy) and doesn't stop unless I tell it to...
HTH, 
Side

---

### Post by Daniel1994 on 2009-07-21
Yeah, mine keeps running to, but it says underneath "pass complete"

Anyway, now I want to stop it. But how to do that without a keyboard?

---

### Post by Sidewinder1 on 2009-07-21
I know you're saying 'no keyboard', I'd still try: Esc, Ctrl Break, Ctrl c, q, Ctrl-ALT-Del, I frankly don't remember how I stopped mine but it must've been one of the above...Isn't this fun?... :-)

---

### Post by Daniel1994 on 2009-07-21
Thanks for your help, but I've tried all the commands. The keyboard just don't work...
f. ex. I press caps lock, but the indicator doesn't light up.

What I'm really wondering is: Will it damage my computer if I force-shutdown?

PS: I am running on a mac

---

### Post by az on 2009-07-21
> **Daniel1994 said:**
> I am running memtest on my computer, and it shows "pass complete, no errors. Press esc to exit"
That's all good, but my keyboard is dead:S

Is it dangerous to force-shutdown during a memtest?

Maybe your BIOS has USB keyboards turned off?  Anyway, no, it's not at all dangerous to power down during memtest - there are no mounted filesystems.

And memtest will go on forever.  Some memory issues only appear after hours.  For example, one of the later passes writes a specific pattern to ram, waits 30 minutes and then goes back to see of the pattern is still there.  It will repeat that many times.

To do a thorough memtest, you need to let it run for hours.

---

### Post by Daniel1994 on 2009-07-21
Thanks a lot, both of you.

I performed a force-shutdown, and my system is not more broken than it was in the first place:)

Im off to reinstall now

---

