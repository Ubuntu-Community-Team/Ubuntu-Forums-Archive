---
title: "Reboot Ubuntu only with an email?"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by taylor102387 on 2009-07-27
I was just wondering, is it even remotely possibly to reboot Ubuntu with a email saying "reboot"? Ive done this in windows, (even though it sucked) but from the command line, you have to be superuser, and it's dangerous to leave it on a listining port of the email world!

But is it possible (duh, somehow. It's freakin' LINUX) But how?:)

---

### Post by halovivek on 2009-07-28
Really. This is the first time i am hearing this type of idea.
how did you do in windows?

---

### Post by Whiffle on 2009-07-28
If it were me and I was any good at programming, I would probably write a script that runs at boot that checks an email account (say a gmail account specific for the purpose).  If it gets an email with the correct stuff in it (maybe a certain passphrase or something), it triggers a reboot.  You could use sudo to limit it to only being able to reboot, and make the script run as its own user so it can't do anything else on your system.  Its really pretty simple if you break it down, like most/all programming problems.

---

### Post by niteshifter on 2009-07-28
As the saying goes "If you have physical access you can do anything". But I think the OP means without prepping the machine first.

In Windows (and I'm reaching way back memory lane here) one can do this without prepping the machine via embedding VBScript in the email which makes a call to the ShellExecute API which invokes shutdown.exe. This works (usually) because A) Most Win boxen users run at admin level, B) IE is the shell and IE is what renders / parses HTML email.

In a Linux box it's not possible. Even should the mail client keep emails as individual text files (most don't) they would lack execute permission. And even if a whacked-out mail client gave saved files execute permission, we're missing an overly-eager-willing-to-do-anything "executor" (shell) that just executes on it's own - any *nix shell has to be explicitly commanded.

---

### Post by taylor102387 on 2009-07-28
In windows, I set up outlook to scan all emails for a phrase like "pc reboot" and this would trigger a .bat that shuts the computer down. Maybe you could link it up to ssh, so you could run very simple commands, and then do it. Ill have to look into it a little bit more.

---

### Post by binbash on 2009-07-28
> **niteshifter said:**
> 
In a Linux box it's not possible. Even should the mail client keep emails as individual text files (most don't) they would lack execute permission. And even if a whacked-out mail client gave saved files execute permission, we're missing an overly-eager-willing-to-do-anything "executor" (shell) that just executes on it's own - any *nix shell has to be explicitly commanded.

This is very possible with a cron and a little bash scripting.

---

### Post by taylor102387 on 2009-07-28
sweet, and yes, ill prep it first

---

### Post by taylor102387 on 2009-07-28
.

---

### Post by andrew.46 on 2009-07-29
Hi taylor,

> **taylor102387 said:**
> I was just wondering, is it even remotely possibly to reboot Ubuntu with a email saying "reboot"? 

It would perhaps be easier to log on to the computer with ssh and run the shutdown command:

```
sudo shutdown -r now
```

Simply run an ssh demon the computer, setup port forwarding on your router and access the computer with openssh client or putty from windows.

Andrew

---

### Post by taylor102387 on 2009-07-29
Thanks Andrew, but I already have ssh installed, it was just a theory.

---

