---
title: "Embaded terminal to Desktop (problem)"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by adeee on 2011-02-10
guys i just follows these instructions: [http://ubuntuforums.org/showthread.php?t=202249](http://ubuntuforums.org/showthread.php?t=202249)

and make my embaded terminal to desktop. but there is a strange problem. the terminal is not actually embaded with the desktop see screen shot.
[ATTACH]183134[/ATTACH]

my 
nano ~/.devilspie/DesktopConsole.dsscript is this.
```

(if
        (matches (window_name) "DesktopConsole")
        (begin
                (set_workspace 1)
                (below)
                (unminimize)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "desktop")
                (shade "#ffffff")
                (below)
                (geometry "+50+50")
                (geometry "460x700")
        )
)


```
How to solve top bar problem.?
[COLOR=Red]Remember[/COLOR] i have no compiz and my [COLOR=Red]visual effects[/COLOR] are none.
i already tested this but when i embed it before i dont know how i was solved this problem.
so any idea?
Also how can i make terminal like this. [Semi-transparent with shadows (using Xgl)]("http://img135.imageshack.us/img135/7796/desktopterminal6vw.png")

---

### Post by adeee on 2011-02-10
suggestion please how i solve this problem.

---

