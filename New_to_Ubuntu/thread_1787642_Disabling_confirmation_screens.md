---
title: "Disabling confirmation screens"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by Inodoro Pereyra on 2011-06-21
Hello everybody.
I've been using Ubuntu for about 2 years now, and loving every second, but there is something that started as a minor inconvenience, and has evolved into the single most annoying thing I have to do, ever: the stupid confirmation screens.
If I want to empty the trash, there's the damn thing: "Are you sure you want to empty the trash?" OF COURSE I'M SURE!!! THAT'S WHY I CLICKED ON IT!!!:mad:
Same if I want to restart, shut down, etc.

Is there any way to disable those screens?

Thanks in advance. :)

---

### Post by nomko on 2011-06-21
Okay,
 
Start Gconf-editor.
[COLOR=#0000ff][COLOR=#0000ff][COLOR=black]Go to:[/COLOR][/COLOR][/COLOR]
[COLOR=#0000ff][COLOR=#0000ff][COLOR=black]**/apps/gnome-sessions/options/**[/COLOR]
[/COLOR][/COLOR][COLOR=black]uncheck: logout_prompt[/COLOR]
 
[COLOR=black][COLOR=#0000ff][COLOR=#0000ff][COLOR=black]**/apps/nautilus/preferences/**[/COLOR]
[COLOR=black]uncheck: confirm_trash[/COLOR]
[/COLOR][/COLOR][/COLOR]
[COLOR=black][COLOR=#0000ff][COLOR=#0000ff][COLOR=black]This should do the trick.[/COLOR]
[/COLOR][/COLOR]
 
[/COLOR]

---

### Post by Inodoro Pereyra on 2011-06-21
Thank you Nomko. That took care of the trash and the shut down.
Is there a way to disable the screen for the restart?

---

### Post by Inodoro Pereyra on 2011-06-22
Ok, curiously enough, after the first time, the confirmation screen for the shutdown came back. The one for the trash seems to be gone for good, fortunately.

So I've been looking around in Gconf-editor, and finally found it. Just in case somebody else needs it, go to:

apps/indicator-session
and check: suppress_logout_restart_shutdown

And that's it. :)

---

