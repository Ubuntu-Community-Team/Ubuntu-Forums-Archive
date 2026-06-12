---
title: "Bios timer not connected bug/error"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by mjp29 on 2009-10-12
Perhaps my laptop was like this before the HD crashed, but I just started noticing the error.

When the hd was crashed and i booted it I read the message that popped up upon booting (message was hard to read because it pops up so quickly upon booting and goes away before one can read and write down the entire message).

I was told by a Geeksquad person that if I replace the HD then the BIOS would then understand that the BIOS is ok.

Well, I replaced the bad HD with a new one and the message still pops up quickly - something about BIOS error  (or BIOS bug or BIOS problem) and also says something like  timer not connected" but again mssg goes away so quickly one can't read it entirely.

But nothing other than this message is a problem - the computer even keeps the correct time and date.

I also just put a new battery in this Dell laptop.  I have read on the net where some Dell models will have an unstable BIOS with a fully charged battery - and my Dell laptop hasn't had a fully charged battery for years until now.

?

---

### Post by mikechant on 2009-10-12
As this appears to be BIOS message it won't be available in any Linux log file etc.
However, you might be able to catch it by filming the screen with a digital camera and then playing back/pausing/stepping the resulting film. Obviously use the equiptment/settings which give you the best frame rate.

---

### Post by fbugnon on 2009-10-12
> **mjp29 said:**
> (...) but again mssg goes away so quickly one can't read it entirely.(...)

I guess you can use the "Pause | Break" key to make the BIOS message pause/stop so you can read it.

---

### Post by HarrisonNapper on 2009-10-12
You might need to hold down Ctrl when you hit Break for it to work.

Also, you probably have two working hard-drives. Check out RAID configuration to get a little bit more storage space (precious on any computer).

---

### Post by mjp29 on 2009-10-12
"mp bios bug 8254 timer not connect to io-apic" is what it says

anyone know what it means?

---

### Post by mikechant on 2009-10-13
There's a currently open Ubuntu bug which appears to match this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/283489](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/283489)

If it's not actually causing a problem (Ubuntu running reliably etc.) then I'd suggest leaving it but checking back on this bug from time to time.

Also, if you google your error message, there is lots of information about this message going back a few years with possible workarounds. But the workarounds might have negative effects so may not be a good idea unless you are getting real problems beyond just the message displaying.

---

