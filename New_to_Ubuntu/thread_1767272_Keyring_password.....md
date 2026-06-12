---
title: "Keyring password....?"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by OllieGab on 2011-05-25
Whenever I log in I get (something like):
'Your keyring password didn't activate at log-in'
So I enter my password and then I get **another** 'Your keyring...'

Is there any way I can disable this? It's quite annoying!
Or **at least**, make me fill it in just once!?

Cheers

---

### Post by I2k4 on 2011-05-25
Delete.

---

### Post by I2k4 on 2011-05-25
I actually like the idea of a password login at boot, as I have in XP, but find this one a bit of a pest in putting up two keyring PWs at each boot - one for DSL and one for Mail-Notifier, regardless of using the same Pw.  It is probably something similar that is triggering your double Keyring - two separate functions being activated after booting.

Anyway, although I'm using still it now, I successfully got rid of it on a previous install by using the Synaptic Package Manager, searching "Keyring" and completely uninstalling the "Gnome-Keyring" with it.  I'm similarly new, and can't help about the multiple Keyring dialog boxes - there are much better experts here.

---

