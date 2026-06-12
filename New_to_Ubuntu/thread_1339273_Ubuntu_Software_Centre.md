---
title: "Ubuntu Software Centre"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-11-27
One of the things I was looking forward to using in 9.10 was the new Ubuntu Software Centre as a replacement for Add/Remove Applications, Synaptic Package Manager and Software Sources.

I've just upgraded from 9.04 but the three of them are still in my menu list, and all look exactly as they did in 9.04. What is more, there is no Software Centre in my System>Administration menu, although Add/Remove Applications tells me that it's installed.

Can anyone figure out what might be wrong?

---

### Post by lovemylady on 2009-11-27
[COLOR=Magenta]Use ubuntu?

Go upper corner click very left on "anwendungen" dunno in english and in the dropdown menu at last there is software center even if synaptics is better :p to find what you need ^^ 


easier explination click left upper corner on ubuntu logo and dropdownmenu last entry.. :rolleyes: ^^[/COLOR]

---

### Post by Roger Allott on 2009-11-27
> **lovemylady said:**
> [COLOR=Magenta]Use ubuntu?

Go upper corner click very left on "anwendungen" dunno in english and in the dropdown menu at last there is software center even if synaptics is better :p to find what you need ^^ [/COLOR]
No, it's not there. The translation of "anwendungen" is "applications", and Software Centre is definitely not listed in my menus.


> **lovemylady said:**
> 
[COLOR=Magenta]easier explination click left upper corner on ubuntu logo and dropdownmenu last entry.. :rolleyes: ^^[/COLOR]

That's Add/Remove Applications.

---

### Post by ajgreeny on 2009-11-27
I think Add/Remove has been replaced by Software Centre, so it may be that your update has either replaced Add/Remove with SC, and you have not noticed, or that for some reason there is no SC on an update as compared with a clean install.

Apart from that I have no idea.  Personally, I always use synaptic in any case, even on my clean install of karmic.

---

### Post by Roger Allott on 2009-11-27
> **ajgreeny said:**
> I think Add/Remove has been replaced by Software Centre, so it may be that your update has either replaced Add/Remove with SC, and you have not noticed, or that for some reason there is no SC on an update as compared with a clean install.


It would seem that people are having difficulty reading my OP. So I'll repeat it.

If the upgrade had replaced Add/Remove with SC, then Add/Remove wouldn't be in my menu list and SC would be there. But Add/Remove **is** in my menu list and SC isn't.

There definitely is an SC in an upgrade, because it's shown as being installed in Add/Remove.

---

### Post by jbalazs on 2009-11-27
> **Roger Allott said:**
> No, it's not there. The translation of "anwendungen" is "applications", and Software Centre is definitely not listed in my menus.




That's Add/Remove Applications.

It's listed as Ubuntu Software Centre

---

### Post by Roger Allott on 2009-11-27
> **jbalazs said:**
> It's listed as Ubuntu Software Centre

Well, perhaps it would be if it was listed at all!

---

### Post by jbalazs on 2009-11-27
> **Roger Allott said:**
> Well, perhaps it would be if it was listed at all!
Try System>Preference>Main Menu>Applications

on the right side make sure the Ubuntu Software Center is check marked

---

### Post by Roger Allott on 2009-11-27
> **jbalazs said:**
> Try System>Preference>Main Menu>Applications

on the right side make sure the Ubuntu Software Center is check marked

It's not there to be available for check marking.

---

### Post by themusicalduck on 2009-11-27
Firstoff try typing ```
software-center
``` into a terminal to see if it'll run.

If it will, then you could just create a new menu entry with that as the command.

---

### Post by jbalazs on 2009-11-27
> **Roger Allott said:**
> It's not there to be available for check marking.
 you may have to remove and reinstall it trough Synaptic Package Manager

---

### Post by Roger Allott on 2009-11-27
> **themusicalduck said:**
> Firstoff try typing ```
software-center
``` into a terminal to see if it'll run.

If it will, then you could just create a new menu entry with that as the command.

Thanks. That's got it working. I'm still baffled as to why it wasn't there by default. Oh well.

---

### Post by lovemylady on 2009-11-27
[COLOR=Magenta]Strange by me it was there by default.. installed with wubi or so? sine i installed fully on my notebook more or less ^^[/COLOR]

---

