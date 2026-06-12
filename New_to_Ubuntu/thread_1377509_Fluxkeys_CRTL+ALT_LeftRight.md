---
title: "Fluxkeys: CRTL+ALT Left/Right"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by Psumi on 2010-01-10
I want to set CRTL+ALT Left to previous workspace and CRTL+ALT Right to next workspace, but when I go to fluxkeys and put down control and mod1, it doesn't work.

Control mod1 Left for previousWorkspace doesn't work.
Control mod1 Right for nextWorkspace doesn't work either.

---

### Post by ibninja on 2010-01-11
Try in system->preferences->keyboard shortcuts switch workspaces laft/right is under window management almost at the bottom. I don't know whether fluxkeys would give a different result somehow, but keyboard shortcuts worked for me.

---

### Post by Psumi on 2010-01-11
> **ibninja said:**
> Try in system->preferences->keyboard shortcuts switch workspaces laft/right is under window management almost at the bottom. I don't know whether fluxkeys would give a different result somehow, but keyboard shortcuts worked for me.

Mini.iso doesn't have keyboard shortcuts, I must use fluxkeys. Anyway, I use openbox now.

---

### Post by ibninja on 2010-01-11
add
```
Control Mod1 Right :NextWorkSpace
Control Mod1 Left :PrevWorkSpace
```
to ~/.fluxkeys/keys
I think that should make the shortcuts work.

---

