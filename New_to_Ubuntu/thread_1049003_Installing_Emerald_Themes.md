---
title: "Installing Emerald Themes"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-01-24
How do I install emerald themes? I downloaded the theme from gnome's site, and then I imported it to Emerald Themer, but I'm still using Human. I'm also running Compiz Fusion. I have the window decorator checked. If I don't have the window decorator checked then I loose the whole top part of my windows, where the close, minimize, and maximize buttons are. Do I have to do something so Compiz will use my emerald themes?

---

### Post by jimmy the saint on 2009-01-24
Where you activate winow decorations in the compiz control panel there should be a box that is called "command"

replace what is there with "emerald --replace" (without the quotes)

save all of your work and press ctrl-alt-backspace to reload your session and now emerald will be managing your window decorations and your theme can be applied.

---

### Post by binbash on 2009-01-24
emerald --replace will replace metacity with emerald.You can add it to your startup also.

---

### Post by Sup3r3g0 on 2009-01-24
Thanks. It's working now.

---

