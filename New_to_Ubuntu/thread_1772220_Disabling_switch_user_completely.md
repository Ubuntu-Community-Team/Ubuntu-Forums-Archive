---
title: "Disabling switch user completely?"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by darknomel on 2011-05-31
Hi all!

I'm in the process of building a locked down desktop for my company based on 10.04.

One of the features I've been working on disabling is switching users. I've disabled it in:

```
gconfg-editor = /desktop/gnome/lockdown
```

But this only seems to disable it from the lock screen menu. If I click on **system - log out** on the menu it still gives me the option to switch users.

Does anyone know how to disable it from there?

---

### Post by dcsoldschool53 on 2011-05-31
> **darknomel said:**
> Hi all!

I'm in the process of building a locked down desktop for my company based on 10.04.

One of the features I've been working on disabling is switching users. I've disabled it in:

```
gconfg-editor = /desktop/gnome/lockdown
```But this only seems to disable it from the lock screen menu. If I click on **system - log out** on the menu it still gives me the option to switch users.

Does anyone know how to disable it from there?

I hope this will help you```
 gconf-editor = apps/indicator session
```Here you can remove log out.

---

### Post by darknomel on 2011-06-01
> **dcsoldschool53 said:**
> I hope this will help you```
 gconf-editor = apps/indicator session
```Here you can remove log out.

Hi,

I tried that and it didn't work :(

What I'm trying to remove is this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=193851&stc=1&d=1306922426[/IMG]

Thanks :)

---

### Post by cracker89 on 2011-06-01
Does this help?

[http://ubuntuforums.org/showthread.php?t=284871](http://ubuntuforums.org/showthread.php?t=284871)

And this should help: 

> **crjackson said:**
> okay I figured this out for Ubuntu...

Terminal>gconf-editor

desktop>gnome>lockdown>disable_user_switching and tick the check box

DONE!

It completely disables user switching. Source >> [http://ubuntuforums.org/showthread.php?t=770963](http://ubuntuforums.org/showthread.php?t=770963)

---

### Post by darknomel on 2011-06-01
> **cracker89 said:**
> Does this help?

[http://ubuntuforums.org/showthread.php?t=284871](http://ubuntuforums.org/showthread.php?t=284871)

And this should help: 



It completely disables user switching. Source >> [http://ubuntuforums.org/showthread.php?t=770963](http://ubuntuforums.org/showthread.php?t=770963)

Both those are disabled already, but I can still log out using the screen above from **system - logout** :(

---

### Post by DinoT1985 on 2011-06-01
see if this helps
[http://ubuntuforums.org/showthread.php?t=700675](http://ubuntuforums.org/showthread.php?t=700675)

---

### Post by dcsoldschool53 on 2011-06-02
> **darknomel said:**
> Hi,

I tried that and it didn't work :(

What I'm trying to remove is this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=193851&stc=1&d=1306922426[/IMG]

Thanks :)

I had looked all around this site [http://library.gnome.org/admin/system-admin-guide/stable/index.html.en](http://library.gnome.org/admin/system-admin-guide/stable/index.html.en), I hope it helps you.

---

### Post by darknomel on 2011-06-06
> **DinoT1985 said:**
> see if this helps
[http://ubuntuforums.org/showthread.php?t=700675](http://ubuntuforums.org/showthread.php?t=700675)

This seemed to have taken care of it :)

---

