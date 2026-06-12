---
title: "How do I empty my trash can manually from the CLI?"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by diablo75 on 2010-11-27
I've been attempting to empty my trash can and it just sits there with it's little "count-down" graph pop-up saying "Emptying Trash" but it never moves anywhere and has no ETA.  It's been like this for 20 minutes now; no error messages, and plenty of CPU activity to suggest it's actually thinking about something... but I'm just wondering if it might be snagged for some reason.  So I wanted to attempt to clear it from the CLI.  What's the safest way to do this?

---

### Post by sandyd on 2010-11-27
> **diablo75 said:**
> I've been attempting to empty my trash can and it just sits there with it's little "count-down" graph pop-up saying "Emptying Trash" but it never moves anywhere and has no ETA.  It's been like this for 20 minutes now; no error messages, and plenty of CPU activity to suggest it's actually thinking about something... but I'm just wondering if it might be snagged for some reason.  So I wanted to attempt to clear it from the CLI.  What's the safest way to do this?

```

rm -rf ~/.local/share/Trash

```
be careful, a single typo can knock out your home folder.

---

### Post by sisco311 on 2010-11-27
Well, I guess the safest would be:
```
empty-trash
```
you have to install **trash-cli** first.

The user's trash is usually in ~/.local/share/Trash/, so removing its content should empty the trash:
```
rm -rf ~/.local/share/Trash/
```

For alternative locations of the trash can, check out the freedesktop specs:
[http://www.ramendik.ru/docs/trashspec.html](http://www.ramendik.ru/docs/trashspec.html)

---

### Post by bananas4370 on 2010-11-27
> **diablo75 said:**
> I've been attempting to empty my trash can and it just sits there with it's little "count-down" graph pop-up saying "Emptying Trash" but it never moves anywhere and has no ETA.  It's been like this for 20 minutes now; no error messages, and plenty of CPU activity to suggest it's actually thinking about something... but I'm just wondering if it might be snagged for some reason.  So I wanted to attempt to clear it from the CLI.  What's the safest way to do this?

You can delete the Trash by doing the following in a terminal

```
sudo rm -rf $HOME/.local/share/Trash/*
```

Cheers
Patrick

---

### Post by ironic.demise on 2010-11-27
$HOME is the same as ~/
~/ is the same as /home/$USER/
/home/$USER/ is the same as /home/"your actual username"

---

### Post by sisco311 on 2010-11-27
> **ironic.demise said:**
> $HOME is the same as ~/
~/ is the same as /home/$USER/
/home/$USER/ is the same as /home/"your actual username"
usually... :evil:


By default, a non-system user's home directories is created in /home, but that's not mandatory.


See:
```
man bash | less +/"Tilde Expansion"
man bash | less +2/"Shell Variables"
```

---

### Post by ironic.demise on 2010-11-29
> **sisco311 said:**
> usually... :evil:


By default, a non-system user's home directories is created in /home, but that's not mandatory.


See:
```
man bash | less +/"Tilde Expansion"
man bash | less +2/"Shell Variables"
```

tmi for now, thanks for the heads up though.

---

### Post by diablo75 on 2010-11-30
> **sisco311 said:**
> Well, I guess the safest would be:
```
empty-trash
```
you have to install **trash-cli** first.

This worked perfectly for me.  THANKS!

---

