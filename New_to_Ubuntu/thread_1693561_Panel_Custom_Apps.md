---
title: "Panel Custom Apps"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by wgwwm34 on 2011-02-23
So I made some panel buttons that execute commands to start and stop my apache server. Well actually they refer to scripts that do that but I'm pretty sure that's irrelevant. The buttons don't work unless I have elevated the user to su through some other method. They include sudo at the front of them so they should prompt me for the su password but they don't. Any ideas why this is? I've tried it with simply commands and also buttons linking to scripts and it's the same either way.

---

### Post by mnerobi15 on 2011-02-23
Just use a regular distro base system and add your own app packages into  a folder to be installed later. That's about the closest you can get  without scripting it in.

---

### Post by Copper Bezel on 2011-02-23
You need to make it gksudo instead. Just sudo only works within a terminal window. With gksudo, you'll get your familiar popup password request when running a script like this.

---

