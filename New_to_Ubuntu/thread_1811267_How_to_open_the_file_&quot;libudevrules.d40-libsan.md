---
title: "How to open the file &quot;/lib/udev/rules.d/40-libsane.rules&quot;"
date: 2011-07-24
forum: New to Ubuntu
---

### Post by tinkles on 2011-07-24
How do I open the file "/lib/udev/rules.d/40-libsane.rules"  and add these two lines to it:

# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

I am trying get my brothers scanner to work.

---

### Post by MG&amp;TL on 2011-07-24
Good luck with the scanner.

In a terminal: (Ctrl-Alt-T)
```
sudo gedit /lib/blah/blah/yourfilename/here.
```

It will prompt you for the administrator password, then open gedit with your file. Or at least it should.

Oh yeah, and then save the file, once you've made he alteration.

EDIT: 'gksudo' NOT 'sudo'

---

### Post by MG&amp;TL on 2011-07-24
Oh, btw, if gedit won't open a file for you in future, type:

```
file <full/directory/path/to/file/here/<file>
```

And it will tell you what sort of file it is. Just handy.

---

### Post by philinux on 2011-07-24
That should be 

```
gksudo gedit
```

---

### Post by MG&amp;TL on 2011-07-24
Respect, and I'm not questioning your authority, but why? 'Sudo' works for me...Do follow the good gentleman's advice, I shall edit my post.

---

### Post by oldos2er on 2011-07-24
[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by MG&amp;TL on 2011-07-24
Right...ok, learn something new every day...:)

---

### Post by tinkles on 2011-07-24
this what I get:

hamfreth@hamfreth-laptop:~$ hamfreth@hamfreth-laptop:~$ file </lib/udev/rules.d/40-libsane.rules/<40-libsane>
bash: syntax error near unexpected token `newline'
hamfreth@hamfreth-laptop:~$ bash: syntax error near unexpected token `newline'
> hamfreth@hamfreth-laptop:~$ 
> 
> gksudo gedit /lib/udev/rules.d/40-libsane.rules
> 
> sudo gedit/lib/udev/rules.d/40-libsane.rules
>

---

### Post by MG&amp;TL on 2011-07-24
Ah, sorry, < and > don't mean anything, they're just to demarcate it. Sorry, should have mentioned that. <sorry face>

I put them in to make it clearer, just don't put them in. It's a text file, your file. I know because it exists on my computer.

---

### Post by tinkles on 2011-07-24
this what I get now:

> sudo gedit/lib/udev/rules.d/40-libsane.rules
> $ file </lib/udev/rules.d/40-libsane.rules/40-libsane
> ~$ file /lib/udev/rules.d/40-libsane/40-libsane
> ~$ file /lib/udev/rules.d/40-libsane
> ~$ file /lib/udev/rules.d/40-libsane.rules
>

---

### Post by oldos2er on 2011-07-24
Try ```
gksu gedit /lib/udev/rules.d/40-libsane.rules
``` Note the space between 'gedit' and '/lib'

---

