---
title: "How do I remove a program?"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by ErrolRay on 2010-06-11
Specifically, I loaded Thunderbird email, and it is not working.  Do I just reload it, or is there someway to add/remove programs such as in Windows?
Thanks.
Also if you could recommend any other email program, I would appreciate it much.
Errol

---

### Post by pricetech on 2010-06-11
System - Administration - Synaptic Package Manager.

That's assuming Ubuntu.  If you have another distro, your steps will vary.

---

### Post by ErrolRay on 2010-06-11
Thanks

Errol

---

### Post by Jahocolips on 2010-06-11
It's also quite simple to view and remove your installed software from... Applications -> Ubuntu Software Center

---

### Post by ErrolRay on 2010-06-11
both ways work to "remove" the program, however if I reload Thunderbird, it comes up with the same settings as the original one that is not working.  There has got to be some folder, file, or something that I need to remove so I can reload Thunderbird, and reinstall everything.
All help is appreciated
Errol

---

### Post by Jahocolips on 2010-06-11
Can you explain exactly what it is you're trying to do?

---

### Post by dookiebowser on 2010-06-11
> **ErrolRay said:**
> both ways work to "remove" the program, however if I reload Thunderbird, it comes up with the same settings as the original one that is not working.  There has got to be some folder, file, or something that I need to remove so I can reload Thunderbird, and reinstall everything.
All help is appreciated
Errol

The community here is very likely to help you troubleshoot your problem, even though it is not Ubuntu related FYI.

I would also like to know about this. I know ubuntu and linux don't work like Windows in the sense that it doesn't have a registry or .ini's in folders that are separate from the application that configure the OS/program. Why doesn't uninstalling it with these methods remove configuration files and settings?

---

### Post by pricetech on 2010-06-11
Because the settings are personal and have nothing to do with the application.

That's the short answer anyway.  Many windows programs behave the same way.

Remove Thunderbird via whichever method you prefer.
Look for a folder in your home directory named ".thunderbird" (without the quotes of course) and delete it.  You'll need to view hidden files to see it. (View - Show Hidden Files)

Install Thunderbird again.  You should have a pristine install ready for you to set up your account.

---

### Post by Zill on 2010-06-11
> **ErrolRay said:**
> ...Also if you could recommend any other email program, I would appreciate it much...
Evolution (email/PIM) is installed by default - why not use that?

---

### Post by Zemblan on 2010-06-11
I believe the command:

```
sudo apt-get purge thunderbird
```

will remove the application and also it's configuration files. The you can reinstall it and it should be in it's default state.

EDIT: Greetings to you Zill, not often I come across a fellow yellowbelly round here :)

---

### Post by ErrolRay on 2010-06-12
Thanks to all for the help.  Pricetech's method worked and is letting me re set it up correctly.
Errol

---

### Post by pricetech on 2010-06-13
Cool.

---

