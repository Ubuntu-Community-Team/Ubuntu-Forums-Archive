---
title: "What in Firefox Browser is stopping the use of Extra formatting in the Forums?"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by mikodo on 2010-04-07
Hello everyone,

I recently reinstalled Karmic (only OS on the desktop) and was pleased to find that I could use the Extra Formatting again ie. Code boxes, underlining etc. in the forums. I had lost the ability to do that down the road with the previous install. Now, a week after the new install, none of these features work again.

I believe it has to do with the Firefox Preference or Add-ons, I have installed, that is blocking them.

Has anyone had this difficulty, and can quickly tell me what it might be. Rather than me shutting each Preference off and removing each Add-on, one at a time, and trying the Extra Formatting repeatedly? It would save me some time, if anyone knows.

Thanks.

---

### Post by Temposs on 2010-04-07
I'm not sure what's causing it, but if you delete the .mozilla folder in your home folder, then that will reset all of your settings, and it may fix your problem.

---

### Post by mikodo on 2010-04-07
> **Temposs said:**
> I'm not sure what's causing it, but if you delete the .mozilla folder in your home folder, then that will reset all of your settings, and it may fix your problem.
Thank you for the reply

```
I did as you suggested.

```
It was one of the Add-ons that was deleted by removing the .mozilla file. I believe all I had was: Better Pivacy; AdBlock plus; No Script; WOT; TACO. _I have try each one_ _at a time_, _to see _which is the **problematic**_ one_.

_Thanks._

---

### Post by lovinglinux on 2010-04-07
I just released an extension that can apply bbcode formatting to forum posts, among other things, like saving posts as quotes and pasting them from the context menu. See [http://ubuntuforums.org/showthread.php?t=1447098](http://ubuntuforums.org/showthread.php?t=1447098)

It works even if the bbcode buttons don't appear in the forum editor.

BTW, you could start Firefox in safe mode instead of deleting all your settings. See [COLOR="Sienna"]**Troubleshooting**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by mikodo on 2010-04-07
> **mikodo said:**
> Thank you for the reply

```
I did as you suggested.

```
It was one of the Add-ons that was deleted by removing the .mozilla file. I believe all I had was: Better Pivacy; AdBlock plus; No Script; WOT; TACO. _I have try each one_ _at a time_, _to see _which is the **problematic**_ one_.

_Thanks._
```
Well, it took some doing, I narrowed it down to the NoScript Add-on in Firefox. Even though I white listed ubuntuforums.org in Noscript, it still is the one that is blocking the ability to use Extra formatting in Ubu forums. Too bad too, it is one that I like a lot.
```

```
Well that did it! Adding the yahooapis.com as a white listed address in NoScript fixed the problem. Now, I can have my cake and eat it too. (Ubuntu Foruns with full functionality and use NoScript).
```

Thank you everyone.

Mike

---

### Post by gvoima on 2010-04-07
You also have to allow yahooapis.com if you have noscript installed. 
Because the site uses some javascript functions provided by it.

---

### Post by lovinglinux on 2010-04-07
> **mikodo said:**
> Well, it took some doing, I narrowed it down to the NoScript Add-on in Firefox. Even though I white listed ubuntuforums.org in Noscript, it still is the one that is blocking the ability to use Extra formatting in Ubu forums. Too bad too, it is one that I like a lot.

Add ubuntuforums.org to NoScript allow list. If that doesn't work, you might need to lower NoScript blocking settings. I use NoScript and I block almost everything, even stuff from allowed sites and it works fine.

> **gvoima said:**
> You also have to allow yahooapis.com if you have noscript installed. 
Because the site uses some javascript functions provided by it.

I forgot about that, which is probably the problem.

---

### Post by mikodo on 2010-04-07
> **gvoima said:**
> You also have to allow yahooapis.com if you have noscript installed. 
Because the site uses some javascript functions provided by it.

Problem fixed. Thank you.

Mike

---

