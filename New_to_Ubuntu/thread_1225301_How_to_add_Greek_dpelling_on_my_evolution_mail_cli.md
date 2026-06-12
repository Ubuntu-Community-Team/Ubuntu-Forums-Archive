---
title: "How to add Greek dpelling on my evolution mail client"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by altkon on 2009-07-28
I am using Evolution (Suse 10.1) as my e-mail client. Under Preferences/
Composer Preferences/Spell Checking, I have three dictionaries but the
Greek dictionary is not included. How can I add the Greek dictionary so
that Evolution can do the spell checking. Under OpenOffice the Greek
dictionary is present and it does spell checking in Greek.:(
Thanks

---

### Post by y-lee on 2009-07-28
I am not on a linux machine so i can't test this but anyway hopefully this will work, Evolution uses aspell for it's spell checking so you need to install the gnome-aspell, aspell and aspell-xx packages for the dictionaries (where XX is your locale, for example aspell-en for US English or aspell-fr for French, etc.) I would think gnome-aspell and aspell are already installed, so you need to find the greek language dictionary. It is called something like aspell-el and hopefully you ahould be able to find it in the repos, but if not look on [aspells site]("ftp://ftp.gnu.org/gnu/aspell/dict/0index.html").

---

### Post by altkon on 2009-07-28
I did find the "aspell-el" both under "Synaptic Package Manager" and on "aspells site".
I managed to download and install it with"Synaptic Package Manager" so as to add the Greek language and check the box after hitting Evolution Preferences> Composer Preferences > spell checking.
However when I tried to create a new mail with Greek context, the spell checker did not work , instead showed spelling is complete.

When I tried to download the "aspell-el 0.50.3 tar.b22" folder from the aspells site, an error occured and refused to install.
In conclusion all my efforts without result..:(
Thanks for you guidance.
Regards,
AA

---

### Post by y-lee on 2009-07-28
> **altkon said:**
> I did find the "aspell-el" both under "Synaptic Package Manager" and on "aspells site".
I managed to download and install it with"Synaptic Package Manager" so as to add the Greek language and check the box after hitting Evolution Preferences> Composer Preferences > spell checking.
However when I tried to create a new mail with Greek context, the spell checker did not work , instead showed spelling is complete.

Ok it sounds like it was successfully installed here. Are you sure the spell check wasn't working? Did you misspell a few words on purpose to make sure? If nothing was misspelled it will show the spelling check as complete. Test it to be sure.

> **altkon said:**
> When I tried to download the "aspell-el 0.50.3 tar.b22" folder from the aspells site, an error occured and refused to install.
In conclusion all my efforts without result..:(
Thanks for you guidance.
Regards,
AA

Ok I am not sure why or what happened here without more information. What was the error message exactly? It may be that it wouldn't install because it already was installed or because you downloaded a dictionary for a version of aspell you do not have, notice they have dictionaries for 2 different versions of aspell at the above link. 

Since synaptic has the greek dictionary in the repos I would suggest you stick with the version there. If it is still not working try opening synaptic and reinstalling it.

---

### Post by altkon on 2009-07-29
I have reinstalled aspell-el with synaptic, on Evolution client.2.22.3.1
As you had suggested I misspelled  a few words in Greek language,
but still the same... when I pres F7 a pop image comes up telling me "no misspelled words".
Whereas spelling checker works fine with English text.
However I have digged out a bug concerning the same case involving Evolution Mail program.
[https://bugs.launchpad.net/ubuntu/+source/gnome-spell/+bug/10713](https://bugs.launchpad.net/ubuntu/+source/gnome-spell/+bug/10713)

Believe nothing can be done..
Appreciate your further comments.

---

### Post by y-lee on 2009-07-29
> **altkon said:**
> However I have digged out a bug concerning the same case involving Evolution Mail program.
[https://bugs.launchpad.net/ubuntu/+source/gnome-spell/+bug/10713](https://bugs.launchpad.net/ubuntu/+source/gnome-spell/+bug/10713)

Believe nothing can be done..
Appreciate your further comments.

Yeah I found the same bug report yesterday so I suspect this problem is not easily fixed. Hopefully in time the developers will fix the problem. If you really need greek spell check to work in your e-mail client you can try using another one such as thunderbird or whatnot. thunderbird is nice, I used it for years, tho I don't know if it supports greek language spell check. I suspect it does. Other than that I suppose you could write your greek letters in another application.

If you have a Launchpad account or are willing to file one you could post your problem on the launchpad bug report you linked to above.

---

### Post by altkon on 2009-07-29
I will rather stick to evolution writing my Greek context using the OO.Word processor which can handle the Greek spelling checker.
Besides that I will patiently wait for the developers to fix the problem.
Thanks anyway for your guidance and assistance.

---

