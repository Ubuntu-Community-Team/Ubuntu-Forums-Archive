---
title: "gpic/lxde"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by dzon65 on 2010-03-02
Does anyone know how to set gpicview as default picture viewer in lxde?

---

### Post by s.fox on 2010-03-02
Hello,

I think something like this is what you need to do.

```
xdg-mime default gpicview.desktop `grep &#8216;MimeType=&#8217;  /usr/share/applications/gpicview.desktop | sed -e &#8217;s/.*=//&#8217; -e &#8217;s/;/  /g&#8217;`
```
Information sourced from [here ]("http://blog.lxde.org/?p=50")



-Silver Fox

---

### Post by dzon65 on 2010-03-02
Just back.Well,it should,at least that's what I found googling on it,but it doesn't.The mime type can't be found (some problem with xdg-mime).For some reason,can't seem to set default progs.Gave minimal/lxde a try on an old pc and I've got an lxde session option on my main.Same results.Perhaps the iso is a bit corrupted.I'll burn another one and see what it gives.On my main using minimal ubuntu with an lxde session though,so that cannot be  a iso problemIt's a petty though,that for a leightweight like lxde,takes a bunch of configuring to make it work.(default progs,desktop icons etc...).In the mean time,I'll consider the thread closed.Thanks for the tip.
Kind regards,J.

---

### Post by kerry_s on 2010-03-02
just right click on the pic-> open with-> open with another program, then select the program & check the box.

---

### Post by dzon65 on 2010-03-03
Kerry?That's a gimp job,wright?Lol.Wish it were that simple,but don't have that option.Checked the other pc.Take a look.

---

### Post by dzon65 on 2010-03-03
And trying to set it in gpic's settings doesn't work either.

---

### Post by kerry_s on 2010-03-03
> **dzon65 said:**
> Kerry?That's a gimp job,wright?Lol.Wish it were that simple,but don't have that option.Checked the other pc.Take a look.

nope, thats a pic from my debian lxde install. i have no idea why its missing from yours. :lolflag:
let me jump on that computer & look around,i'll get back to you.

---

### Post by kerry_s on 2010-03-03
i don't know what to tell you, i have that option for everything, files, shells scripts, configs, etc...

---

### Post by dzon65 on 2010-03-03
Well,stuck in the same don't-know-what-to-say.Works in every windowmanager,filemanager,whatever manager.......but not in lxde.This is the latest release (as far as I know),perhaps there's something missing,I don't know.
Wouldn't bother too much though,I'll live.Anyhow,thanks for the replies.
Kind regards,J.

---

