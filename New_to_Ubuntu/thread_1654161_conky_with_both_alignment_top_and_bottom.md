---
title: "conky with both alignment top and bottom ?"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by honeybear on 2010-12-27
man says:
"Text alignment on screen, {top,bottom,middle}_{left,right,middle}"

How to update please the .conkyrc so that it would give (in red)

```

alignment top_left

TEXT
${execi 15 echo "`myfile1 `"}      [COLOR="Red"]## <- I would like here top_left[/COLOR]
${execi 15 echo "`myfile2 `"}     [COLOR="Red"] ## <- I would like here bottom_left[/COLOR]
```

---

### Post by mobilediesel on 2010-12-28
> **honeybear said:**
> man says:
"Text alignment on screen, {top,bottom,middle}_{left,right,middle}"

How to update please the .conkyrc so that it would give (in red)

```

alignment top_left

TEXT
${execi 15 echo "`myfile1 `"}      [COLOR="Red"]## <- I would like here top_left[/COLOR]
${execi 15 echo "`myfile2 `"}     [COLOR="Red"] ## <- I would like here bottom_left[/COLOR]
```

The easiest way to do that would be to have to .conkyrc files. One with **alignment top_left** and the other with **alignment bottom_left**
Then use the **-c** switch to load the other .conkyrc
```
conky -c ~/.conkyrc
conky -c ~/.conkyrc2
```
or whatever filename you give it.

---

### Post by honeybear on 2010-12-28
> **mobilediesel said:**
> The easiest way to do that would be to have to .conkyrc files. One with **alignment top_left** and the other with **alignment bottom_left**
Then use the **-c** switch to load the other .conkyrc
```
conky -c ~/.conkyrc
conky -c ~/.conkyrc2
```
or whatever filename you give it.


thank you but are you really sure that there is not better alternative, using less CPU, so with a single process?

---

### Post by mobilediesel on 2010-12-28
> **honeybear said:**
> thank you but are you really sure that there is not better alternative, using less CPU, so with a single process?

If your "myfile1" and "myfile2" will always be the same size you could just put a bunch of blank lines between them:
```
TEXT
${execi 15 echo "`myfile1 `"}      ## <- I would like here top_left






${execi 15 echo "`myfile2 `"}      ## <- I would like here bottom_left
```

as many lines as it takes.

---

### Post by honeybear on 2010-12-28
> **mobilediesel said:**
> If your "myfile1" and "myfile2" will always be the same size you could just put a bunch of blank lines between them:
```
TEXT
${execi 15 echo "`myfile1 `"}      ## <- I would like here top_left






${execi 15 echo "`myfile2 `"}      ## <- I would like here bottom_left
```

as many lines as it takes.

well I use my pc on several workstation at school too, and it seems difficult to program :( 
thank you anyhow. Maybe there is better programs than conky, but dont know any. I would have to ./configure ; make  at home to have a compiled other alternative

---

