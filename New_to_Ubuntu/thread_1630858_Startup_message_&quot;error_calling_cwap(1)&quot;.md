---
title: "Startup message: &quot;error calling cwap(1)&quot;"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by solor on 2010-11-25
Hi,

I've installed Ubuntu 10.10 for the first time and it all seems ok so far. However whenever I boot up a message appears on screen for about 1s and then goes away:
[B]
16.8889691 asws_laptop: Error calling CWAP(1)

[/B]Anyone know if this is normal? Is this something I should be worried about?
Thanks.

---

### Post by solor on 2010-11-26
Bump, can anyone help?  Thanks.

---

### Post by Rubi1200 on 2010-11-26
Well, a quick Google search did not really turn up anything helpful (except for still being able to boot despite the error message or unless you happen to understand Russian, Italian, French, and some other languages).

The only thing I did find which *might* be worth trying is this:

Boot the computer and when the entry for Ubuntu is highlighted in GRUB press "e" to edit.

Navigate using the cursor to the line that ends with > quiet splash and append acpi=off so it looks like this > quiet splash acpi=off
Then, "Ctrl" + "x" to boot.

Let us know if this makes a difference.

---

### Post by ironmonkeygf on 2011-01-20
Assuming the OP meant asus_laptop instead of asws_laptop, I'm having this issue as well.  Mine's an Asus M6N notebook.

This makes the system hang before CWAP error message shows up.
> acpi=off 

This stops the CWAP error message, but causes shutdown to hang on the splash screen.
> acpi=off apm=off 

I have issues with shutdown anyway.  When I shutdown, the laptop reboots instead.  I don't know if the two are related.

---

### Post by typewriter_chimp on 2011-02-12
I have an Asus M6Ne laptop that was giving the same error during boot. It would continue to boot fine until I logged in via the login screen, at which point it would freeze as soon as the login sound finished.

I tried the solutions suggested above to no avail.

What (seems to have ) resolved the issue for me is to update my bios to 208.

I still get the error couldn't call CWAP(1), but the system seems to boot stably after that.

---

### Post by Clever_Username on 2011-02-12
I've seen a few references to this error from people running 10.10 on laptops. It has something to do with the kernel trying to match objects returned by Init to the specific model of laptop

---

### Post by ironmonkeygf on 2011-02-18
I updated my BIOS from 207 to 214.  That didn't fix my reboot on shutdown issue or the "error calling cwap".


I know some C/C++, but this is my first time looking at Linux source code, so don't read too much into the following observations:

The error message comes from line 1456 of asus-laptop.c when write_acpi_int(asus->handle, "CWAP", wapf) returns a non-zero acpi status.  That can happen from an invalid handle or the acpi_evaluate_object call.

wapf is related to Fn+Fx key controlling WLAN.  The comments indicate that the function needs to be called for some laptops to initialize properly.  My Fn+F2 toggles my WLAN properly, so I'm not going to worry about the error anymore...

---

