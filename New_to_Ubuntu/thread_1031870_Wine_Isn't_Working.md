---
title: "Wine Isn't Working"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by faith1215 on 2009-01-05
I have been attempting to run .exe files and so far no luck. I downloaded Daz3d and am trying to run it on ubuntu.

I am pretty new to Linux, so I'm not sure what other information I still need to give. I don't know how to find what version of Wine I'm running or anything else.

I ran:
wine DAZStudio_2.3.3.89_win.exe

Came up with:
wine client error:0: version mismatch 0/378.
Your wineserver binary was not upgraded correctly, or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?

I feel like such a noob. Please - help!

---

### Post by Matthewthegreat on 2009-01-05
to find what version of Wine type

```
wine --version
```

---

### Post by tuxxy on 2009-01-05
How did you install wine and there should be a graphical menu for you to easier open files

---

### Post by faith1215 on 2009-01-05
> **Matthewthegreat said:**
> to find what version of Wine type

```
wine --version
```

Wine-1.1.12

> **tuxxy said:**
> How did you install wine and there should be a graphical menu for you to easier open files

I went to my applications menu and installed it under Add/Remove.

When none of the wine stuff came up, I went into my terminal and did:
```
sudo apt-get install wine
```

Still, nothing as far as GUIs go though. *sigh*

---

### Post by faith1215 on 2009-01-06
I've looked around for additional information on the error I received:
```

wine client error:0: version mismatch 0/378.
```

Still no luck. Any ideas?

---

### Post by The-IRS on 2009-01-06
g

---

### Post by llama320 on 2009-01-06
I'm not sure about your specific problem, but to get to a wine config gui open a terminal and type
```
winecfg
```

if it's the first time you've run the command, it might take a moment to open. From here you should be able to tweak wine until your heart's content

---

### Post by Asday on 2009-05-28
I get the same error when trying "winecfg"

I installed wine from the repositories, then updated it (to attempt to get SketchUp to work) and now it dain't work.

I'm running Jaunty.

---

### Post by achase79 on 2009-05-28
did you add the winehq.org repositories and install from them?

---

### Post by Paqman on 2009-05-28
You Wine install sounds pretty unhappy. Have you tried reinstalling it?

---

### Post by Asday on 2009-05-28
achase:  Yus.  That's the update that made it stop working.

Paqman:  Not to seem impudent, but isn't that advice for windows?  Isn't it the advice that is frowned upon by the community?  "Reinstall."  [EDIT:  Not that I'm not happy that you're happy.]

---

### Post by chrisod on 2009-05-28
Reinstall is usually the first suggestion with Windows. Here it is a last resort :)

---

### Post by Steelmourne on 2009-05-28
If you installed in Add/Remove, then the terminal there will be problems as wine needs any older version uninstalled first. Try re-installing.

---

### Post by sandyd on 2009-05-28
maybe....

```

sudo apt-get --purge remove wine wine-gecko&&sudo apt-get install wine

```
remove wine-gecko if it says it isn't installed

EDIT: btw, don't install from the WINE repositories. The version there is prone to regressions (means bugs) that may cause some programs to have weird problems (MS office for instance doesn't install from WINE 1.1.16 onwards)

---

### Post by Asday on 2009-05-29
I'll try the purge, but I installed from the wine repositories 'cause the canonical repositories had a version that wouldn't run SketchUp.

---

