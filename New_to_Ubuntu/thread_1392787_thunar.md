---
title: "thunar"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by dzon65 on 2010-01-28
Anyone know  how to set thunar as default file manager instead of nautilus?Tried several options,none worked.
Thanks in advance,J.

---

### Post by J V on 2010-01-28
```
gconftool-2 --set --type string /desktop/gnome/session/required_components/filemanager "thunar"
gconftool-2 --set --type string /desktop/gnome/applications/component_viewer "thunar %s"
```Should work, enjoy...

Edit: Probably wrong, if you just google "set thunar default manager" you would get an answer, looks like you didn't try hard enough :|

---

### Post by dzon65 on 2010-01-28
Like I said,tried several,none worked,as does this one.
It IS set,however,after log out/in nautilus's still ruling.

---

### Post by J V on 2010-01-28
[https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager) ?

---

### Post by dzon65 on 2010-01-28
Yep,been there.No go.

---

### Post by warfacegod on 2010-01-28
[http://assente.altervista.org/it/use_thunar_as_default_gnome_file_manager]("http://assente.altervista.org/it/use_thunar_as_default_gnome_file_manager")

Another option would be to remove Nautilus entirely.

---

### Post by dzon65 on 2010-01-28
Could do that but some applications won't run.For example,clicking "computer" won't open if nautilus is removed.

---

### Post by warfacegod on 2010-01-28
Use the Configuration Editor and go to:

desktop> session> required_components> filemanager> right click> select Edit key> change value to thunar from nautilus

---

### Post by dzon65 on 2010-01-28
> **J V said:**
> [https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager) ?

Tried it once more and.....it worked,but.Thunar will open files exept for some that seem to be nautilus bound.

---

### Post by Leppie on 2010-01-28
install xubuntu-desktop :P

---

### Post by dzon65 on 2010-01-28
> **warfacegod said:**
> Use the Configuration Editor and go to:

desktop> session> required_components> filemanager> right click> select Edit key> change value to thunar from nautilus

Warface,did that (see attachment),but that doesn't do much.

---

### Post by dzon65 on 2010-01-28
> **Leppie said:**
> install xubuntu-desktop :P
Thanks but I prefer the ubuntu one.It's weird,did a minimal install on a different pc with thunar as file manager and it opened everything (if I recall well).

---

### Post by Leppie on 2010-01-28
> **dzon65 said:**
> Thanks but I prefer the ubuntu one.It's weird,did a minimal install on a different pc with thunar as file manager and it opened everything (if I recall well).
well, there is a way to do it. but it's not working seamlessly. i tried once with pcmanfm in ubuntu, but i think that these complete de's like gnome and kde are a bit like windows. depending too much on internal components which cannot really be removed/replaced.

---

### Post by warfacegod on 2010-01-28
> **dzon65 said:**
> Warface,did that (see attachment),but that doesn't do much.

I looked at the attachment and you weren't in quite the same area that I suggested. It doesn't matter though, I est the key to mandatory and it isn't working. Did you try the link I posted?

---

### Post by dzon65 on 2010-01-29
Well,as this is the full ubuntu install,might wanna change it to a minimal and add whatever I like.I think in the full package too many things depend or overrule others.

---

### Post by warfacegod on 2010-01-29
> **dzon65 said:**
> Well,as this is the full ubuntu install,might wanna change it to a minimal and add whatever I like.I think in the full package too many things depend or overrule others.

Yeah, that makes sense. Worth a try at the very least.

---

### Post by Leppie on 2010-01-29
the gnome desktop will always install with nautilus as default :(

---

### Post by dzon65 on 2010-01-31
Yep,but it's still possible to change file managers,windowmanagers...Itt's just that,for example,running openbox as windowmanager works just fine.As wanting thunar as file manager only works partially.

---

### Post by dzon65 on 2010-01-31
> **Leppie said:**
> the gnome desktop will always install with nautilus as default :(

Like I said before,did this minimal install once.Installed gnome-core and some other gnome stuff and thunar as filemanager.Pretty sure it opened every menu.
Should be getting an old pc in a couple of days.I'll do the exact same install to make sure,I'll let you know.

---

