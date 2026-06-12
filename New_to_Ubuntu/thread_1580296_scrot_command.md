---
title: "scrot command"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by dzon65 on 2010-09-23
I use scrot to make my screenshots  open automatically with mpaint like this (this is 5 sec delay):
scrot -d 5 '%Y-%m-%d--%s_$wx$h_scrot.png' -e 'mv $f ~/Bureaublad/ & mtpaint ~/Bureaublad/$f'
Bureaublad meaning desktop.
However,what I don't like is that the screenshot's being installed in my desktop folder in advance,no matter if I edited it or not.If I do edit it,it will replace the existing one of course,but that's not what I want.So,what would the command be to open in mtpaint,without storing it?

---

### Post by kerry_s on 2010-09-23
i think you just need to:
scrot -d 5 '%Y-%m-%d--%s_$wx$h_scrot.png' -e 'mtpaint $f'

---

### Post by dzon65 on 2010-09-23
Kerry,long time! Yeah,that does work.Only thing,how do I get it to store it in my desktop folder when I save it.Like this,it's being stored in my home folder.

---

### Post by dzon65 on 2010-09-23
Edit:too soon.It's still being saved in advance,this time in my homefolder.It slipped me first.

---

### Post by kerry_s on 2010-09-23
my guess is it has to be saved somewhere first, mtpaint can't open a file that don't exist.

mtpaint itself can do screenshots, look at "mtpaint --help" maybe do your screenshots with out scrot.

i thnk its "-s"?
```
sleep 5;mtpaint -s '%Y-%m-%d--%s_$wx$h.png'
```

---

### Post by dzon65 on 2010-09-24
Hi k,timezone stuff.Yeah,tried that one before but then I would need something to make it store in a folder automatically when I click save.Now it always needs a name,"save as...png".So those date and png settings don't work with mtpaint -s.Neither did the delay setting.Those scrot commands are the same statler uses.Slitaz does the same,but I'm no sure they're the same commands.Oh well,it was worth a try,going to stick with this.Thanks for the effort and help k.
Regards,J.
Up to the next question.

---

