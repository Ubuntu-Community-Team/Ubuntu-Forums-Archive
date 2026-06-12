---
title: "Awn"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by GodlySoup on 2009-08-28
Is there a way to use Avant Window Navigator without having Compiz? I'm afraid the graphics on this computer just isn't up to speed.

---

### Post by MelDJ on 2009-08-28
why not try installing and running it to see it works?

---

### Post by Perfect Storm on 2009-08-28
I think AWN only can with compiz enable or there will be a big black box around it. You could try some of the other apps that do the same thing like AWN. I know Kiba Dock uses compiz, but I don't know if Cairo Dock do.

---

### Post by Viva on 2009-08-28
> **Artificial Intelligence said:**
> I think AWN only can with compiz enable or there will be a big black box around it. You could try some of the other apps that do the same thing like AWN. I know Kiba Dock uses compiz, but I don't know if Cairo Dock do.

I think that is cairo-dock you are talking about. AWN doesn't show at all without compiz and gives you a warning message.

@OP, what is your graphic card?

---

### Post by oboedad55 on 2009-08-28
> **Viva said:**
> I think that is cairo-dock you are talking about. AWN doesn't show at all without compiz and gives you a warning message.

@OP, what is your graphic card?

How about using gnome-do with the docky option?

---

### Post by Viva on 2009-08-28
> **oboedad55 said:**
> How about using gnome-do with the docky option?

No, it gives you an error that your display is not properly configured.

---

### Post by Paqman on 2009-08-28
You need some form of compositing to get AWN. On Gnome that normally means Compiz, but not necessarily.

I've not messed about with alternate compositing in Gnome, but you could try installing xcompmgr and see if that can get you set up.

---

### Post by luctor on 2009-08-28
Gnome can do compositing by itself.
You have to enable a 'key' in the Gconf Editor.
I'm not at my Ubuntu box at the moment (I'm on my wife's Mac).

just found this link:maybe it works
[http://blogs.gnome.org/metacity/2008/12/16/the-easiest-way-to-turn-on-compositing/](http://blogs.gnome.org/metacity/2008/12/16/the-easiest-way-to-turn-on-compositing/)

---

### Post by echo6 on 2009-08-29
I used to like awn, and I've also tried cairo. Unfortunately I've found them both to be lacking and very buggy!

After spending a lot of time trying to get awn to be consistent I gave up, and after trying cairo and finding similar issues again I gave up.

---

### Post by MasterPoulos89 on 2009-08-29
Metacity has a composite-manager that can be used with AWN. 

type "gconf-editor" in terminal and go to desktop/gnome/sessions/required-components and from there enable metacity. To enable metacity I right click on window manager and select edit key and type metacity. I'm not using Ubuntu right now so I don't know if its different.

Then go to apps/metacity/general and make sure compositing-manager is checked.

Hope this is helpful

---

