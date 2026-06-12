---
title: "how do you make large shadows? is there a way?"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by enri2 on 2009-05-27
i want large shadows , larger than the compiz window decoration. I want something like leopard shadows... my question is: is it possible to overdrive the shadow radius in window decoratin(compiz) bigger than 18.0000, or is there any other way of making large shadows??

---

### Post by konqueror7 on 2009-05-27
mmm...have you tried using Emerald window decorations instead and tweaking the shadow radius there?

---

### Post by kpkeerthi on 2009-05-27
If you are using Compiz with GTK window decorator, write these commands in a terminal:
```

gconftool-2 --type float --set /apps/compiz/plugins/decoration/allscreens/options/shadow_radius 18

```

```

gconftool-2 --type float --set /apps/compiz/plugins/decoration/allscreens/options/shadow_opacity 0.85

```

Or press ALT + F2 and enter **gconf-editor**. Then, navigate to /apps/compiz/plugins/decoration/allscreens/options and change the radius and opacity of the shadows.

If you are using Compiz with emerald, you can change the shadow settings in Emerald Theme Manager.

---

### Post by enri2 on 2009-05-27
> **kpkeerthi said:**
> If you are using Compiz with GTK window decorator, write these commands in a terminal:
```

gconftool-2 --type float --set /apps/compiz/plugins/decoration/allscreens/options/shadow_radius 18

```

```

gconftool-2 --type float --set /apps/compiz/plugins/decoration/allscreens/options/shadow_opacity 0.85

```

Or press ALT + F2 and enter **gconf-editor**. Then, navigate to /apps/compiz/plugins/decoration/allscreens/options and change the radius and opacity of the shadows.

If you are using Compiz with emerald, you can change the shadow settings in Emerald Theme Manager.thanks so much, but I have a problem now.The panel has a large shadow too .. I want it to have a shadow  but not that large... anyway  i can lower  the panel shadow?

EDIT: never mind , I'm fine :D   , but if you know it tell me 
thanks
damn this is amazing!!!

---

