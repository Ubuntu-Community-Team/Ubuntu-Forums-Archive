---
title: "Old Firefox won't uninstall"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by MarkX on 2010-08-09
Old Firefox won't uninstall (in Lynx). 
Tried synaptic and apt-get remove but whenever I install Firefox 3.6
I still have the old Firefox 3.0.1 (which crashes in Hotmail).
Any ideas?

---

### Post by jtarin on 2010-08-09
You could try ```
apt-get remove --purge <nameofapplication>
```Thiswill remove all your config files too so you might want to backup things you want to keep,bookmarks etc.

---

### Post by MarkX on 2010-08-09
Nope, that didn't work. I uninstalled Firefox as above, then reinstalled it and I still have the old 3.0.1 (which I can't update) with my old bookmarks. 
I suspect that I'm only installing/uninstalling the new one but the menu still keeps pointing at the old one for some reason. The firefox logo in the 'internet apps' menu does disappear when firefox is uninstalled but when reinstalled, clicking the "new" logo brings up the Old Firefox again.

---

### Post by MarkX on 2010-08-10
Anyone please?

---

### Post by jtarin on 2010-08-10
I didn't want to post this but you can doit if your determined. In the terminal enter the command ```
sudo updatedb
```It will run for a minute or so.When finished enter the command ```
locate firefox
```this will find all instances of firefox on your system. Some of these will be icons you can ignore these. Delete all the rest.When you think you have finished run updatedb and the locate firefox to re-check. Then locate mozilla and do the same. This should remove everything firefox related from your install. I would backup  bookmarks to a different folder.

---

### Post by MarkX on 2010-08-10
Thanks but How do I delete them?
 Tried it in GUI but I can't get "permission".

Edit: I think I have somehow fixed the crashing problem of the old Firefox so I'll stay with that as I'm stuck with it anyway.
Not happy with Ubuntu and Canonical though. More utterly pointless changes in Lynx.

---

### Post by MarkX on 2010-08-10
Well, I did it, with your help and by substituting the old Firefox with the new one. Thanks!

---

### Post by jtarin on 2010-08-10
> **MarkX said:**
> Well, I did it, with your help and by substituting the old Firefox with the new one. Thanks!
Cool!:popcorn:

---

