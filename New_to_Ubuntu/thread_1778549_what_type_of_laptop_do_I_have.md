---
title: "what type of laptop do I have?"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by Darris on 2011-06-09
I have seen about a billion types of toshiba satellite, each with its own series of letters and numbers.
i would like to know which series of letters and numbers belong to my own

---

### Post by Paqman on 2011-06-09
Flip it over and look for a sticker on the bottom that tells you.

---

### Post by Mariane on 2011-06-09
I was wondering about this post. Maybe s/he means the mac address? 

Mariane

---

### Post by hakermania on 2011-06-09
> **Mariane said:**
> I was wondering about this post. Maybe s/he means the mac address? 

Mariane

I don't think so :/

---

### Post by birkopf on 2011-06-09
> **Paqman said:**
> Flip it over and look for a sticker on the bottom that tells you.

That's the best way. To find out more about your hardware specification install: HardInfo

---

### Post by lisati on 2011-06-09
I can't check at the moment, I'm on Windows. If memory serves correctly, the dmidecode command can tell you.

---

### Post by Mariane on 2011-06-09
hardinfo does not show anything about the second monitor plugged into my laptop. You wouldn't know a fix for that by any chance? 

Mariane

---

### Post by Toz on 2011-06-09
> **lisati said:**
> I can't check at the moment, I'm on Windows. If memory serves correctly, the dmidecode command can tell you.

Yep. ```
sudo dmidecode --type 1
``` will do it.

---

### Post by Darris on 2011-06-15
> **Toz said:**
> Yep. ```
sudo dmidecode --type 1
``` will do it.

Thank you very much.
This is a used laptop and i always read about the problems with toshiba so I felt it would be important to know.
The sticker is all washed out and near impossible to read

---

