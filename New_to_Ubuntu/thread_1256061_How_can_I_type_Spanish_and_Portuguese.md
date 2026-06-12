---
title: "How can I type Spanish and Portuguese?"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by ulnpzf on 2009-09-02
I already installed Spanish and Portuguese by "Language Support".
But I couldn't find Spanish and Portuguese in SCIM.
How can I type Spanish and Portuguese?

---

### Post by zvacet on 2009-09-03
In SCIM>fromt end>global setup>on the right side you will see keyboard layout.

---

### Post by ulnpzf on 2009-09-03
> **zvacet said:**
> In SCIM>fromt end>global setup>on the right side you will see keyboard layout.
But if I sutup "Keyboard Layout" as Spanish, I can't use other languages. Because the layout is different.
I use English, Korean, Japanese, Chinese, Russian but they have same keyboard layout.

---

### Post by Bucky Ball on 2009-09-03
How did you set up the other languages?

---

### Post by CatKiller on 2009-09-03
As a slightly left-field suggestion, you can type other characters with the English keyboard layout by using the Compose key. A couple of examples; Compose &#8594; ~ &#8594; n gets you ñ, Compose &#8594; , &#8594; c gets you ç, and so on. I'm not entirely sure which characters you need for those languages, but you may be able to find them in [this table]("http://www.hermit.org/Linux/ComposeKeys.html").

You can define which key is your Compose key in the Keyboard Preferences tool; System &#8594; Preferences &#8594; Keyboard &#8594; Layouts &#8594; Layout Options... &#8594; Compose key position.

---

### Post by Bölvaður on 2009-09-03
This is what you should do (apply what you feel is good):

Right click your panel
Press *Add to panel*...
Filter word: keyboard
Select *Keyboard Indicator*
press *+Add*

Right click on the new icon
Click *Keyboard Preferences*
Click *Layouts*
Click *+Add...*
Pick the keyboard layout you want, then repeat until the list of layouts has all been added.

Click on the most frequently used keyboard layout and drag it to the top of the list

Click *Layout Options*
Click ***Keys to change layout***
Click Right Ctrl


From now on you can press the right control keybutton to switch to the next keyboard layout.

---

### Post by KIAaze on 2009-09-03
> **CatKiller said:**
> As a slightly left-field suggestion, you can type other characters with the English keyboard layout by using the Compose key. A couple of examples; Compose &#8594; ~ &#8594; n gets you ñ, Compose &#8594; , &#8594; c gets you ç, and so on. I'm not entirely sure which characters you need for those languages, but you may be able to find them in [this table]("http://www.hermit.org/Linux/ComposeKeys.html").

You can define which key is your Compose key in the Keyboard Preferences tool; System &#8594; Preferences &#8594; Keyboard &#8594; Layouts &#8594; Layout Options... &#8594; Compose key position.

Ah, thanks, this is GREAT!!! :KS
Even better than the US international layout. At least I don't have to switch between layouts all the time because of quotes anymore.
Now I can wait for the [OLED keyboards]("http://www.artlebedev.com/everything/optimus/") to get cheaper. :P

For KDE users: [http://userbase.kde.org/ComposeKey](http://userbase.kde.org/ComposeKey)
(The euro sign doesn't seem to work, but that's not such a big problem. I mostly need accents, tilda and cedilla.)

---

### Post by guriinii on 2009-10-07
I've used this technique and it worked brilliantly. I struggled for ages with scim but the good people of Ubuntu helped as usual.

I have one small problem though, I can't do the upside down ? and ! If any of you know, please tell me.

---

### Post by CatKiller on 2009-10-07
> **guriinii said:**
> I have one small problem though, I can't do the upside down ? and ! If any of you know, please tell me.

It's in the table that I posted.

Compose &#8594; ? &#8594; ? is ¿. Similarly for ¡.

---

### Post by guriinii on 2009-10-09
¡Muchos gracias CatKiller!

---

