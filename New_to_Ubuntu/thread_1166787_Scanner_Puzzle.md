---
title: "Scanner Puzzle"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by expatCM on 2009-05-22
I have an HP Scanjet 3970c.  It used to work with Ubuntu 7.10 but now it does not work …. sort of …

It gives very terrible results with my main machine – pink and yellow colored random borders, partial scans, refusal to scan …. generally all rubbish.

My main machine is a Gigabyte M55S-S3 with an AMD Athlon.  It is running Ubuntu 64 bit 9.04 but the same thing happened with 32 bit 8.10.

If I plug the scanner into an Asus P4533MX – Pentium 4, 32 bit, Ubuntu 9.04 then the scanning is perfect, not a single error.

Could anyone explain to me please how to fix my Gigabyte machine so that I can use the scanner?

---

### Post by HereInOz on 2009-05-22
If the same scanner performs well on the other machine, it does sound like a hardware issue.

It sounds a bit like RAM or chipset or similar.  First up change the RAM if you can, but I wouldn't be optimistic.  It may even be a failure in the USB of the motherboard.

---

### Post by expatCM on 2009-05-23
hmmmm ....  well yes, a hardware issue certainly .... I can try to swap the memory or at least remove / exchange the two modules to leave just one module in place.  

USB controller failure ....  well ... seems unlikely since other USB devices work.  USB port is improbable since the problem appears irrespective of which port is used.  Chipset ...  I would not have a clue what to do about that .....

---

### Post by lkraemer on 2009-05-23
Before you do all that questionable pulling and swapping.......

What about downloading another Distro and trying your HP scanner
on it.  I'd recommend PCLinuxOS 2009.1 as it appears to work fine
with my scanner that is the same as yours, while Ubuntu has some
BUGS.  I've submitted one BUG and just a few days ago I got an
email BUG Report where they are looking into it.  WHEW! that was
early last fall when I was comparing PCLinuxOS TR5 & TR6 before
the 2009.1 Release. (I'm using Ubuntu 8.04 LTS)

Let me know what you find out, when you try a 2009.1 LiveCD!

REF:
[Bug 318083] Re: Xsane .995 & Ubuntu 8.04 LTS BUG

lkraemer

---

### Post by expatCM on 2009-05-24
I did try booting from the CD of two other distros six weeks ago.  I know that PCLinuxOS was one of them.  The problem was replicated on each OS so it most probably is hardware specific but ...... could it not be kernel specific if the kernel components are common to Linux operating systems ....

---

### Post by lkraemer on 2009-05-24
Now, you didn't exactly say, and everyone assumed you were using
the same Power Supply for the scanner for each test.  If you didn't
and you're supply isn't quite up to the current requirements,
I've seen that cause bad scans.

So, is the Power Supply for the scanner the same?  I had a 1 Amp
supply that sorta worked, but when I went to a 3.3 Amp it worked
Great.

lkraemer

---

### Post by expatCM on 2009-05-24
I am using the same scanner power supply.

I am using this power supply when running the scanner with the two different machines .....  different results as described earlier in the thread so I think the problem is computer, rather than scanner related.

I also asked HP to test the scanner ....  and they did.  I do not know what machine they have but it was running XP and they said that the scanner was working correctly in all respects ...

---

