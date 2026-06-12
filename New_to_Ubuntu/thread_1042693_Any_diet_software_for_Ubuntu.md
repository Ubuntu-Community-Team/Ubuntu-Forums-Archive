---
title: "Any diet software for Ubuntu?"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by greenleaves123 on 2009-01-17
I really like FitDay, but it doesn't work for Linux. Is there something like FitDay that works with Ubuntu?

I know I can use the website FitDay for free, but what would I do when I have no access to Internet?

---

### Post by maruchan on 2009-01-17
There are a few ways to define "diet," so I'd recommend listing the features you'd need and the features you'd like. Keeping that separate from the idea of "dieting" will probably help you find something faster; at least you'll be able to compare software more easily.

You could start here: [http://www.linux.com/feature/51606](http://www.linux.com/feature/51606)

...or open Synaptic and search for "diet" or "nutrition."

Also note that people use software like Excel (OpenOffice Calc comes with Ubuntu and works just as well) to track diet and exercise. You might try a Google search for "free dieting spreadsheet" or "free dieting spreadsheet +blog" to find files. Here's one example:

[http://jeremy.zawodny.com/blog/archives/006851.html](http://jeremy.zawodny.com/blog/archives/006851.html)

---

### Post by greenleaves123 on 2009-01-17
OK, I'm kind of stupid, but I installed a nutrition application or something from synaptic and I don't know how to open it. :/ It's the NUT.

---

### Post by maruchan on 2009-01-17
Usually you type what's under the "package" column in Synaptic. Try typing "nut-nutrition" in a terminal window. Or press Alt+F2 and type it.

---

### Post by cariboo on 2009-01-17
Have you tried typing in at terminal:

```
nut-nutrition
```

The executable is more then likely located in /usr/bin, so if it isn't anywhere in the menu you can always you can always create a custom launcher. To find out for sure where the program is located in a treminal type:

```
locate nut-nutrition | less
```

The less is for just incase there is more than 1 page of output.

Jim

---

### Post by greenleaves123 on 2009-01-17
Thanks, it worked. Before I just typed in nut in the terminal.

Now I just have to explore Nut and learn how to use it. Thanks.

---

