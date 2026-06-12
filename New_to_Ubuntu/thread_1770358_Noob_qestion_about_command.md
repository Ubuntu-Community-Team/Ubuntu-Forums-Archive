---
title: "Noob qestion about command"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by lordtux on 2011-05-29
[FONT=Arial]Hi I’ve just upgraded to 11.4 and downloaded Compiz. At first it ran well then my desktop icons and folders disappeared. I could access only in terminal by pressing Ctrl + Alt F1. Someone passing told me to try typing this command.[/FONT]
 
[FONT=Arial]rm –rf -~/*[/FONT]
 
[FONT=Arial]The command did work but I was wondering what this command say’s I know the (rm) means remove and (~) means home directory [/FONT]
 
[FONT=Arial]Sorry a noob Question[/FONT]

---

### Post by TeoBigusGeekus on 2011-05-29
This command deletes everything in your home folder.
All your settings, documents, music, bookmarks, etc. are gone.
The conflicting settings that crashed unity are gone now, but what a price to pay...

---

### Post by nitstorm on 2011-05-29
Command break-down

```
rm = remove/delete

-rf (arguments)= recursively and forcefully

~/ = ur home directory location
```


Everything in your home directory gets deleted

---

### Post by heyho on 2011-05-29
Maybe you shouldn't listen to people "passing".

Is this a joke?

---

### Post by sectshun8 on 2011-05-29
the rm -rf mean to force remove.. so that commands looks like its tell it to force remove the contents of that directory???

---

### Post by szabouk on 2011-05-29
how come that command works?

---

### Post by nitstorm on 2011-05-29
> **szabouk said:**
> how come that command works?

Removes all the config files present in the home directory as well..

---

### Post by TeoBigusGeekus on 2011-05-29
> **nitstorm said:**
> Removes all the config files present in the home directory as well..

I think he means the - in front of ~/.
It must have been a typo.

---

### Post by szabouk on 2011-05-29
> **nitstorm said:**
> Removes all the config files present in the home directory as well..

I meant this::

rm –rf -~/*   (seem to have some extra chars..)

and why one wants to do that isn't it a hazard?

---

### Post by szabouk on 2011-05-29
> **TeoBigusGeekus said:**
> I think he means the - in front of ~/.
It must have been a typo.

yes probably you right ;) its just typo but with `rm -rf` is a danger ...

---

### Post by nitstorm on 2011-05-29
> **szabouk said:**
> yes probably you right ;) its just typo but with `rm -rf` is a danger ...


Oops, i missed that -  before ~/ , sorry.
And yes it is a stupid move to delete your home directory...

---

### Post by lordtux on 2011-05-29
I did try it and it work a treat thank you so much for explaining the command.

Thanks again

---

