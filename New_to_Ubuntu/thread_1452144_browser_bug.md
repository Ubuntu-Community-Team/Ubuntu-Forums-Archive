---
title: "browser bug?"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by Samemax on 2010-04-11
Hi, since yesterday my browsers (mozilla firefox and konqueror) are both crashing down after a short time. No matter what webpage. Does someone has an idea what is the cause for this mess and how to fix it?
Greetings!

---

### Post by kellemes on 2010-04-11
> **Samemax said:**
> Hi, since yesterday my browsers (mozilla firefox and konqueror) are both crashing down after a short time. No matter what webpage. Does someone has an idea what is the cause for this mess and how to fix it?
Greetings!

Start your browser from a terminal-window and post the output (in the terminal-window) when the browser crashes.

---

### Post by Samemax on 2010-04-11
ok, and how to start it in the terminal? sorry, am an amateur

---

### Post by EssexEagle on 2010-04-11
> **Samemax said:**
> ok, and how to start it in the terminal? sorry, am an amateur

Just type
```
firefox
```
or
```
konqueror
```
into the terminal and press enter.

---

### Post by r_s on 2010-04-11
I had a similar problem a while back, my browser did not start, I just updated my firefox to 3.6.3 using the repositories and it worked fine since then. For a temporary solution I had to create a new profile.

---

### Post by lovinglinux on 2010-04-11
> **r_s said:**
> I had a similar problem a while back, my browser did not start, I just updated my firefox to 3.6.3 using the repositories and it worked fine since then. For a temporary solution I had to create a new profile.

Creating new profiles is the first logical step to find the problem, but in this case I doubt it will help, because Konqueror also crashes.

I would start by disabling flash and check if the problem persists.

@r_s

If you are using ubuntu-mozilla-daily, then you could experience such crashes with the update to 3.6.4, which seems to be causing problems with flash. This doesn't happen when you run 3.6.4 downloaded from Mozilla.

---

### Post by r_s on 2010-04-11
> **lovinglinux said:**
> 

@r_s

If you are using ubuntu-mozilla-daily, then you could experience such crashes with the update to 3.6.4, which seems to be causing problems with flash. This doesn't happen when you run 3.6.4 downloaded from Mozilla.
yeah I was using ubuntu-mozilla-daily for my updates, thanks for the reply.

---

### Post by Samemax on 2010-04-11
> **kellemes said:**
> Start your browser from a terminal-window and post the output (in the terminal-window) when the browser crashes.

ok, that's the output:

(firefox-bin:2096): GLib-WARNING **: g_set_prgname() called multiple times

** (firefox-bin:2146): WARNING **: Serious fd usage error 14

** (firefox-bin:2146): WARNING **: Serious fd usage error 12
Killed

But the good news are that konqueror is working now already for 10 minutes without crashing.

---

### Post by Samemax on 2010-04-12
By the way: when I'm running konqueror from the terminal now, it works, but refuses sometimes to do what I want to (for example let me write). The termina&#314; displays then:
(<unknown>:3501): Gdk-CRITICAL **: gdk_window_get_origin: assertion 'GDK_IS_WINDOW (window) ' failed

But far more important for me is firefox, so can someone please tell me what the posted errors mean and how to fix it?
I'd be very thankful!

---

### Post by lovinglinux on 2010-04-12
> **Samemax said:**
> By the way: when I'm running konqueror from the terminal now, it works, but refuses sometimes to do what I want to (for example let me write). The termina&#314; displays then:
(<unknown>:3501): Gdk-CRITICAL **: gdk_window_get_origin: assertion 'GDK_IS_WINDOW (window) ' failed

But far more important for me is firefox, so can someone please tell me what the posted errors mean and how to fix it?
I'd be very thankful!

Reinstall xulrunner from "System >> Administration >> Synaptic Package Manager". see if that helps.

---

