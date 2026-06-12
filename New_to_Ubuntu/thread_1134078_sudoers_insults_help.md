---
title: "sudoers insults help"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by Walter Melon on 2009-04-23
I'm not sure if this belongs here or not, but i need some help finding a file.

I edited the /etc/sudoers file and added "insults" after the Defaults line, and it works great.:lolflag: But my question is where is the file that contains the insults?  I would really like to customize the insults and add more if I want.

Thanks in advance

---

### Post by kanikilu on 2009-04-23
I believe the insults are hard-coded into the **sudo** source, so it can't be easily* changed :(

*Notice I said *easily* - you can of course change the source and recompile, but since I rely on sudo all day, every day, that's not really something I personally want to monkey with ;)

---

### Post by Walter Melon on 2009-04-23
> **kanikilu said:**
> I believe the insults are hard-coded into the **sudo** source, so it can't be easily changed :(

:( oh well.  I know I can add my own insult with ```
badpass_message=""
``` but can I add more than one or would it get confused?

Or is it possible to make my own file of insults that it would choose from?

EDIT: yeah, i don't really want to mess around with the source.

---

### Post by Walter Melon on 2009-04-23
bump

---

### Post by naveedmurtuza on 2009-04-23
Hi

How can i Enable insults

tried editing my sudoers file but no luck

---

### Post by JK3mp on 2009-04-23
What issue's did you have nave ? Specifics... ;)

---

### Post by Walter Melon on 2009-04-24
> **naveedmurtuza said:**
> Hi

How can i Enable insults

tried editing my sudoers file but no luck

you can do one of two things. to the line that starts with defaults, add ", insults" or add your own insult by typing badpass_message=""

The final line should look like ```
Defaults	env_reset, insults
``` or ```
Defaults	env_reset, badpass_message=""
```

---

