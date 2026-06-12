---
title: "Help with system testing"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by s1wood on 2010-09-28
Since my computer is going through a bad patch of freezing again I ran system testing and it crashed at xrandr_cycle each time. I have read the report and get the following result but I don't know what to do next - it doesn't react to pressing Y for further info, is there some way I can follow this up?
[SIZE=1]xrandr_detect_modes[/SIZE][SIZE=1] fail [/SIZE]  [SIZE=1]
[/SIZE][SIZE=1]xrandr_cycle[/SIZE][SIZE=1] fail [/SIZE]  [SIZE=1]
[/SIZE][SIZE=1]compiz_check[/SIZE][SIZE=1] pass [/SIZE][SIZE=1]  Gathering information about your system...   Distribution:          Ubuntu 10.04  Desktop environment:   GNOME  Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)  Driver in use:         intel  Rendering method:      AIGLX  Checking if it's possible to run Compiz on your system...   Checking for texture_from_pixmap...               [ OK ]  Checking for non power of two support...          [ OK ]  Checking for composite extension...               [ OK ]  Checking for FBConfig...                          [ OK ]  Checking for hardware/setup problems...           [WARN]  Something potential problematic has been detected with your setup:  Warning: PCI ID 8086:2562 detected.   Would you like to know more? (Y/n)   [/SIZE][SIZE=1]glxgears[/SIZE][SIZE=1] fail [/SIZE]
On the first run it did pass on the detect-modes and glxgears, This is the result of a 2nd check, I restarted with REISUB when it crashed.

regards,

Susan

---

### Post by andrewthomas on 2010-09-28
I would try this ppa.  Read the instructions on the page before adding.

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by s1wood on 2010-09-28
Is that safe? It looks a bit radical. I'd hate to stop the thing working altogether.

Susan

---

### Post by andrewthomas on 2010-09-28
If it doesn't help you can always use the ppa-purge command.

---

### Post by s1wood on 2010-09-29
Thanks for trying, but if that is the answer I think I shall have to live with the problem, that looks more complicated than I care to risk getting involved in ."First, do no harm!"

regards,

Susan

---

### Post by tlhodgson on 2010-12-24
I just ran system test in Ubuntu 10.10. The program started up just fine, but it has been running now for about 4 hours. All it says is "gathering information from your system." There is no option to cancel, and it won't let me close it. What's wrong, and what do I do to stop it?

---

