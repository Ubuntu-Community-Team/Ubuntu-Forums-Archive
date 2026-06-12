---
title: "Compiz Window decorator stopped working"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-03-30
So when I booted into Ubuntu this evening I no longer have any window decorations while compiz is my display manager... I have window decorations turned on in my CCSM and I also have simple-ccsm installed/configured. Any idea where else I might check for this setting? I kinda like my wobbly windows and desktop effects, but for functionality I needed the window decorations.

~Jeff

---

### Post by dusan.saiko on 2009-03-30
I had this problem as well, and searched internet a lot - there could be 1000 reasons for this.
What helped me finally was to completly uninstall all stuff related to compiz including configuration files and reinstalling it. I think there was some conflict in configuration files after some software update.

---

### Post by RedSingularity on 2009-03-30
Yeah i recommend you do a clean install.

---

### Post by Yashiro on 2009-03-30
Just open the compiz settings manager. (Install it if you don't have it. It's called compizconfig-settings-manager or simple-ccsm, depends on your build)

Go to the window decorator plugin. Click the button next to the text string of the window decorator.
This restores the default. Log out, and back in.

This bug is usually caused by the app called fusion-icon.

---

