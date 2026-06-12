---
title: "[SOLVED] How can I get programs to &amp;quot;ask to start&amp;quot; at start up?"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by pluckypigeon on 2008-12-04
I don't know if this is possible but I'd like an option where I can get a question, at log in, asking me if it wants me to start a certain program to run at login instead of it running or not running.

e.g

at login I would like to get the option: "Do you want to start Pidgin?" 

I could click yes or no when I log in depending on how I felt!!

I know this sounds silly but any ideas?

Thanks in advanced!

---

### Post by sdennie on 2008-12-04
If you change your startup programs in System->Preferences->Session to be something like:

```

sh -c "zenity --question --title='Pigdin' --text='Do you wish to start Pidgin'? && pidgin"

```

It should do approximately what you want.  It might be a lot of spam though because there is no way to make those events block so all those dialogs will likely appear at about the same time.

---

### Post by pluckypigeon on 2008-12-04
> **vor said:**
> If you change your startup programs in System->Preferences->Session to be something like:

```

sh -c "zenity --question --title='Pigdin' --text='Do you wish to start Pidgin'? && pidgin"

```

It should do approximately what you want.  It might be a lot of spam though because there is no way to make those events block so all those dialogs will likely appear at about the same time.

Thanks for your reply. 

If I set it surely it's not really spam??:confused:

Anyway I'll check it out and get back to anyone who wants to know... little busy at the mo though!!

Thanks again:p

---

### Post by sdennie on 2008-12-04
Haha.  No, I didn't mean like e-mail spam (or even canned spam) but, instead that if you make 10 programs start in this manner, you'll likely get 10 dialog boxes at roughly the same time asking if you want to start some program.  They may or may not overlap each other or fill the screen.

---

### Post by pluckypigeon on 2008-12-05
> **vor said:**
> Haha.  No, I didn't mean like e-mail spam (or even canned spam) but, instead that if you make 10 programs start in this manner, you'll likely get 10 dialog boxes at roughly the same time asking if you want to start some program.  They may or may not overlap each other or fill the screen.

Again, thank you loads!! It works great.:p

The dialog boxes do overlap each other exactly.

I set it to ask about my sysmonitor and terminal screenlets.

---

### Post by pluckypigeon on 2008-12-05
Any ideas on how I could make a checklist or even a dialog that opens multiple files?

I had a look at "man zenity" and had a go on a few commands but I got a little confused.

Thanks in advance!!

---

