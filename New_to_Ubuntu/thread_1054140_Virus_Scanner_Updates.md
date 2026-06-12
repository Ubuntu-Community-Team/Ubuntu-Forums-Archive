---
title: "Virus Scanner Updates?"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by Wovaki on 2009-01-29
Hello

I just downloaded the virus scanner app, and when I ran it I got this message:

> Some distributions do not automatically edit
freshclam.conf and clamd.conf under /etc.
Please edit those before attempting signature updates.

What do I have to do to get it to update signatures?

Thanks

---

### Post by UbuntuNerd on 2009-01-29
did you download and installed "clamav"?

---

### Post by Wovaki on 2009-01-29
I think so...

I typed in "Virus Scanner" in the Ubuntu "Add/Remove" thing.

---

### Post by UbuntuNerd on 2009-01-29
if you did install clamav check out this guide it should explain everything:
[http://my.opera.com/ubuntunerd1/blog/h]("http://my.opera.com/ubuntunerd1/blog/h")

---

### Post by Wovaki on 2009-01-29
Thats all that has to be done?

It says some file has to be edited or something

---

### Post by GepettoBR on 2009-01-29
> **Wovaki said:**
> Thats all that has to be done?

It says some file has to be edited or something

That's a standard warning. It says "some distributions", and Ubuntu isn't one of them. So no problem.

---

### Post by Wovaki on 2009-01-29
Ok
but when I try to update signatures, it says I have to be root.

---

### Post by lazyart on 2009-01-29
I don't run ClamAV because viruses aren't an issue in Linux.  However, to run something as root you must prefix the command with sudo (or gksudo if it is a graphical application).

---

### Post by Wovaki on 2009-01-29
Thanks I got it working.

---

### Post by egalvan on 2009-01-29
> **Wovaki said:**
> Ok
but when I try to update signatures, it says I have to be root.

I installed ClamTK, which is a GUI to ClamAV.
It's available in Synaptic.

After installing it, I opened a terminal and ran
 
```
gksudo clamtk
```

this let me update the files.

regular runs are straight from the menu...

---

### Post by Wovaki on 2009-01-29
will it automatically update signatures?
if so how often?

or do I have to manually do that?

Thanks

---

### Post by egalvan on 2009-01-29
> **lazyart said:**
> I don't run ClamAV because viruses aren't an issue in Linux..

That's right, not an issue in Linux.

But I run clamav to clean up MICROSOFT WINDOWS drives.

Using clamav under Linux gives me very low probability of infecting my work computer.

Peace of mind.

ErnestG

---

### Post by UbuntuNerd on 2009-01-29
check out this link:
[http://sial.org/howto/clamav/freshclam/#s2]("http://sial.org/howto/clamav/freshclam/#s2")

---

### Post by Wovaki on 2009-01-29
Alright,

so without this FreshClam, it has to be done manually?
That doesn't matter to me, I just wanted to know. :)

Thanks

---

### Post by Wovaki on 2009-01-30
Another question:

Do I have to type this into the terminal every time I update the signatures?

Because so far I have been needing to type that in every time, I can't just open the program and click "Update Signatures".

Thanks

---

### Post by doktorrr on 2009-01-30
> **UbuntuNerd said:**
> check out this link:
[http://sial.org/howto/clamav/freshclam/#s2]("http://sial.org/howto/clamav/freshclam/#s2")

Thanks for this link.

---

