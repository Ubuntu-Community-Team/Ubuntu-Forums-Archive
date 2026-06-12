---
title: "Changing default mail in Firefox"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by Tootler on 2009-02-28
When you click on a "mailto" link in Firefox, it brings up Evolution. However I use Thunderbird for my mail, so I want to make that the default in Firefox.

When you go to Edit/Preferences in Firefox, under Applications, the mailto has a drop down menu with "Evolution", "Yahoo mail" and "Use Other..." as the list. I select "Use Other..." and it brings up the file system. Where can I find Thunderbird to set it as my choice for mailto?

TIA

Geoff

---

### Post by smani on 2009-02-28
Look in System -> Preferences -> Preferred Applications: there you can set the default mail client system-wide (for your user account).

---

### Post by lordharsha on 2009-02-28
Go to System->Preferences->Preferred Applications.
Change the Mail Reader to Thunderbird. This should fix the mailto link in Firefox.

---

### Post by Tootler on 2009-03-01
There's usually a simple solution somewhere.

Sorted - for now

Thanks for the help

Geoff

---

### Post by eudemus on 2009-06-04
If you've upgraded from Firefox 2 to Firefox 3, the above may not work. But if so, the following might.

Check out this thread
[http://ubuntuforums.org/showthread.php?t=860010&page=2](http://ubuntuforums.org/showthread.php?t=860010&page=2)

Worked for me when nothing else did.
Basically Firefox 3 doesn't use this "network.protocol-handler.app.mailto" thing any more, but if you've upgraded from Firefox 2, you'll have a load of config data set up for it, which seems to confuse Firefox.

Anyway, that thread tells you how to sort it out.
Cheers,
Eudemus

---

### Post by EssexEagle on 2009-06-04
> **Tootler said:**
> When you click on a "mailto" link in Firefox, it brings up Evolution. However I use Thunderbird for my mail, so I want to make that the default in Firefox.

When you go to Edit/Preferences in Firefox, under Applications, the mailto has a drop down menu with "Evolution", "Yahoo mail" and "Use Other..." as the list. I select "Use Other..." and it brings up the file system. Where can I find Thunderbird to set it as my choice for mailto?

TIA

Geoff


FYI if you want to find Thunderbird in your file system, it's located at /usr/bin/thunderbird.  Indeed, almost all programs are in /usr/bin/ - you can check by typing

```
which thunderbird
```

(or whatever other program you're looking for) into a terminal, and it returns the location of the file which is executed when you run that command.

---

