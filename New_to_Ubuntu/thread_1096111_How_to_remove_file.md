---
title: "How to remove file?"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by Paul T. on 2009-03-14
Hi,
after upgrading graphics driver I now get the following error when running hardware tester:

[I]ERROR: Caught a segmentation fault while loading plugin file:
/usr/lib/gstreamer-0.10/libgstlibvisual.so

Please either:
- remove it and restart.
- run with --gst-disable-segtrap and debug.[/I]

Although I can find the file I'm unable to remove it as I don't have the right 'permissions'?

Please try and keep answers simple as I'm a newbie to Ubuntu, thx.

Paul.

---

### Post by kestrel1 on 2009-03-14
try this```
sudo rm /usr/lib/gstreamer-0.10/libgstlibvisual.so
```
You need to put that in a terminal.

---

### Post by Paul T. on 2009-03-14
Thx Kestrel1 for quick reply, and it worked :D

---

### Post by kestrel1 on 2009-03-14
> **Paul T. said:**
> Thx Kestrel1 for quick reply, and it worked :D
Glad to be of assistance. :D

---

### Post by NewBeeMichael on 2009-03-14
Hi,

If you would like to delete or copy/paste files in the file manager, open Terminal and type:

gkedit nautilus

You need to type your password and you can play around with files as you like.

---

### Post by kestrel1 on 2009-03-14
> **NewBeeMichael said:**
> Hi,

If you would like to delete or copy/paste files in the file manager, open Terminal and type:

gkedit nautilus

You need to type your password and you can play around with files as you like.

That command is actually```
gksudo nautilus
```

---

### Post by starcannon on 2009-03-14
To use Nautilus:
```
gksudo nautilus
```I'm guessing this is what NewbeeMichael meant. 
Ha nevermind Kestrel beat me to it ;)

---

### Post by munishvit on 2009-03-14
> **kestrel1 said:**
> That command is actually```
gksudo nautilus
```

I always use > sudo nautilus
Does gksudo make any difference?

---

### Post by kestrel1 on 2009-03-14
> **munishvit said:**
> I always use 
Does gksudo make any difference?
No it does the same job, but using gksudo gives you a gui type password box.
You could press ALT & F2 together to get the Run Application box up & type ```
gksudo nautilus
```

---

### Post by mvalviar on 2009-03-14
> **munishvit said:**
> I always use 
Does gksudo make any difference?

None. Its just a GUI sudo.

---

### Post by sisco311 on 2009-03-14
> **munishvit said:**
> I always use 
Does gksudo make any difference?

In most cases doesn't, but sometimes is very wrong.

[http://psychocats.net/ubuntu/graphicalsudo]("http://psychocats.net/ubuntu/graphicalsudo")

---

### Post by kestrel1 on 2009-03-14
> **sisco311 said:**
> In most cases doesn't, but sometimes is very wrong.

[http://psychocats.net/ubuntu/graphicalsudo]("http://psychocats.net/ubuntu/graphicalsudo")
Nice link & useful to know.

---

### Post by munishvit on 2009-03-14
Thanks guys. I never knew the difference, [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo) is must see..and Alt+F2 is very handy. 
Thanks again

---

### Post by kestrel1 on 2009-03-14
No problem :D

---

### Post by NewBeeMichael on 2009-03-14
aah, ****... too many commands used today ;-)... of course it's gksudo nautilus :P, sorry...

---

### Post by kestrel1 on 2009-03-14
> **NewBeeMichael said:**
> aah, ****... too many commands used today ;-)... of course it's gksudo nautilus :P, sorry...
Easy mistake to make. Apology not necessary.:)

---

