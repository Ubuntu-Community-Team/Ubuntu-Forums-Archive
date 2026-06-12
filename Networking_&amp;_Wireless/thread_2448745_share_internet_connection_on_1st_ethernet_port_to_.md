---
title: "share internet connection on 1st ethernet port to device connected to 2nd ethernet po"
date: 2020-08-13
forum: Networking &amp; Wireless
---

### Post by dwater on 2020-08-13
The only instructions I can find are to share the internet connection on my ethernet connection via wifi (which I am also doing); but my Mac Mini doesn't like the hotspot created by ubuntu on my laptop, so I am now trying to connect it via a 2nd ethernet connection.

Are there any instructions for doing that?

Ubuntu 19.10 on a ThinkpPad T480s

---

### Post by CelticWarrior on 2020-08-13
> [COLOR=#000000][INDENT]Ubuntu 19.10 on a ThinkpPad T480s[COLOR=#222222]

This is the first problem you need to address: Ubuntu 19.10 is EoL. Please upgrade t o a supported release before anything else.[/COLOR][/INDENT]


[/COLOR]

---

### Post by dwater on 2020-08-13
> **CelticWarrior said:**
> This is the first problem you need to address: Ubuntu 19.10 is EoL. Please upgrade t o a supported release before anything else.[/COLOR][/INDENT]

[/COLOR]

Ooh, you seem to be implying that the new version will have a facility for this. Is that correct?

---

### Post by CelticWarrior on 2020-08-13
No, I'm not.

What I'm saying is that you or anybody else *shouldn't*&#8203; use an End of Life release.

---

### Post by SeijiSensei on 2020-08-13
Please post the results of the commands
```

sudo iptables -L -nv
sudo iptables -t nat -L -nv

```
Wrap the results in [noparse]```

```[/noparse] tags for legibility.

---

