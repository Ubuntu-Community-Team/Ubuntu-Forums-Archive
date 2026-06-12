---
title: "Apt-get and removing unnecessary packages"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by Dubslow on 2011-01-03
All right, so I removed 'evolution' after installation of Ubuntu, but while going through the Update Manager today, I found it was trying to upgrade 13 packages specifically for evolution that I don't want or need. I manually removed two, but have been trying to find a way to remove the rest with one command. I tried

sudo apt-get purge evolution

but that only removed the .conf files and not the other packages. Then I tried

sudo apt-get  autoremove

That only gave me "0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded."
I also tried

sudo apt-get purge $(deborphan)

but that removed three other libraries, but none of the remaining 11. autoclean and clean didn't even give outputs, and didn't remove the 11 remaining. Does anybody know what I can do to get rid of these? I can remove them individually, but that seems inelegant and tedious.

---

### Post by Foxheadz on 2011-01-03
Try ```
 Sudo apt-get purge evolution
```

---

### Post by Dubslow on 2011-01-03
Dude, I already tried that. Did you read my post at all? For good measure, I tried again, and still didn't work.

---

### Post by Chrissd on 2011-01-03
Tried ```
sudo aptitude search evolution
```

That will show what packages with evolution are installed (marked with an i in the left hand column) and you can remove them from there.

---

### Post by Foxheadz on 2011-01-03
Oh sry I guess i skipped that line... I'm not sure but im guessing maybe the libraries are needed for something else. So I don't really know a fix, but instead of running ```
sudo apt-get remove "name"
``` you can do ```
sudo apt-get remove "name1" "name2" and so on
```

---

### Post by Dubslow on 2011-01-03
Sorry for the snappy  response, foxheadz. I got a list of the packages and tried copy pasting that into the command you suggested, but when I hit enter, it wanted to remove like 20 packages, and only four from the list. Among the suggested removals was ubuntu-desktop and various gnome stuff.

Chriss, most of the packages it lists are p's, but a few are i's and less are v's. Is there a command to remove the ones marked i, or did you just mean manually?

Thanks

---

### Post by Foxheadz on 2011-01-03
From what i know no but then again im not an ubuntu genius. So yeah from what i know you have to do it the good ol' way

---

### Post by Chrissd on 2011-01-03
I was thinking of just copy and paste. You could use Synaptic instead, which is just a matter of a few clicks.

I imagine it's saying that a part of ubuntu-desktop will be removed, meaning that something that was installed along with it will be rather than everything will be removed.

Check exactly what it says before removing it.

---

### Post by I'mGeorge on 2011-01-03
> **Dubslow said:**
> All right, so I removed 'evolution' after installation of Ubuntu, but while going through the Update Manager today, I found it was trying to upgrade 13 packages specifically for evolution that I don't want or need. I manually removed two, but have been trying to find a way to remove the rest with one command. I tried

sudo apt-get purge evolution

but that only removed the .conf files and not the other packages. Then I tried

sudo apt-get  autoremove

That only gave me "0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded."
I also tried

sudo apt-get purge $(deborphan)

but that removed three other libraries, but none of the remaining 11. autoclean and clean didn't even give outputs, and didn't remove the 11 remaining. Does anybody know what I can do to get rid of these? I can remove them individually, but that seems inelegant and tedious.

what are you looking for it's a combination between purge and remove like this

```
apt-get --purge remove evolution
```

---

### Post by oldos2er on 2011-01-03
It's safe to remove every evolution package except one, evolution-data-server-common, which has dependencies that when removed would break Gnome. Easy to do this in Synaptic.

---

