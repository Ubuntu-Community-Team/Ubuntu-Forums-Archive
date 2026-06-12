---
title: "Copying my fonts over"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by baxna on 2009-04-14
[FONT="Franklin Gothic Medium"][SIZE="3"]Hello all, quick question... what would be the proper syntax for a terminal command to copy a whole directory of fonts from my windows partition over to my /usr/share/fonts/truetype folder? I suppose that's the right folder to copy them to?[/SIZE][/FONT]

---

### Post by SunnyRabbiera on 2009-04-14
well it depends, do you have just 1 user on your system or many?

---

### Post by baxna on 2009-04-14
I have quite a few. I suppose it involves typing something including "sudo cp *.ttf"?

---

### Post by pmlxuser on 2009-04-14
i guess the right syntax would be

```

sudo cp /windows/fontfolder/*  /usr/share/fonts/truetype folder

```

However if you just want to use the fonts urself only then

```

$cd ~
$mkdir .fonts
$cd .fonts
cp /window/fontfolder/*  .

```
sould work well

---

### Post by SunnyRabbiera on 2009-04-14
No you can simplify, you can install nautilus-su that will allow more ease of use.

---

### Post by Bakon Jarser on 2009-04-14
Edit: Somebody beat me to it : /

---

