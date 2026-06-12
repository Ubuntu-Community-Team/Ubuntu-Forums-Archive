---
title: "gtk theme not loading on login"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by ubername on 2009-07-24
Hi
When I login my gtk theme seems to be ignored until I go to System> preferences>Appearance, whereupon all my windows etc acquire the theme. Any clues?

---

### Post by CatKiller on 2009-07-24
What happens if, instead of going to the Appearance tool, you run gnome-settings-daemon?

---

### Post by ubername on 2009-07-25
> **CatKiller said:**
> What happens if, instead of going to the Appearance tool, you run gnome-settings-daemon?


:~$ gnome-settings-daemon

** (gnome-settings-daemon:4073): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:4073): WARNING **: Could not acquire name



Thanks for the response, don't know what to make of the result.

---

### Post by ubername on 2009-07-25
Actually, as well as giving the above messages it set the fonts etc.

Second time, after reboot, it gives

:~$ gnome-settings-daemon

(gnome-settings-daemon:3708): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:3708): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

and sets the fonts etc.

Should I ignore this and put gnome-settings demon in 'startup applications'?

---

### Post by ubername on 2009-07-25
> **ubername said:**
> Actually, as well as giving the above messages it set the fonts etc.

Second time, after reboot, it gives

:~$ gnome-settings-daemon

(gnome-settings-daemon:3708): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:3708): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

and sets the fonts etc.

Should I ignore this and put gnome-settings demon in 'startup applications'?

This seems to have fixed it, thanks

---

