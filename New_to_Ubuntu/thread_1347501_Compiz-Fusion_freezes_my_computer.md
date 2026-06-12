---
title: "Compiz-Fusion freezes my computer"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by Geraba on 2009-12-06
I was trying Compiz-Fusion features, when I tried to enable Reflection window (something like this). The moment I enabled it, it froze. No keyboard or mouse commands worked, not even ctrl-alt-del.
I had to hard reset my laptop, and when I tried to log again in Ubuntu, it froze the moment I entered my password...
How do I remove that option now?? Or how to remove that Compiz Settings??
Thanks in advance

---

### Post by Geraba on 2009-12-06
I solved my problem....

I tried to use Failsafe-GNOME, but it locked up... I guess it was just bad luck, but anyway...
I booted in recovery mode, entered root prompt, and used:

```
locate reflex
```to find where the config files where...
I went to 

/usr/share/compiz/reflex.xml
/usr/share/gconf/schemas/compiz-reflex.schemas 
and renamed both files to something else... Rebooted, and it worked!
Before this, I also tried to uninstall compiz via recovery prompt... It kinda worked, but when I logged in GNOME, it was REALLY sluggish... And eventually locked up again... Then I re-installed it via apt-get.

---

