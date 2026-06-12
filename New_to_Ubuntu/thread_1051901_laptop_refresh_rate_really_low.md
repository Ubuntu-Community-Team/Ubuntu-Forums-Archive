---
title: "laptop refresh rate really low"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by oliwood2 on 2009-01-27
i cant get my refresh rate over 51 hz and its almost impossible to watch videos with it. my setup is a laptop with a Nvidia Geforce 8600m GT

---

### Post by sdennie on 2009-01-27
What method are using to determine the refresh rate?  Are you using compiz?  If so, try changing the refresh rate to 60Hz with:

```

gconftool-2 --type bool --set /apps/compiz/general/screen0/options/detect_refresh_rate 0
gconftool-2 --type int --set /apps/compiz/general/screen0/options/refresh_rate 60

```

---

### Post by stchman on 2009-01-27
> **oliwood2 said:**
> i cant get my refresh rate over 51 hz and its almost impossible to watch videos with it. my setup is a laptop with a Nvidia Geforce 8600m GT

Did you enable the restricted driver(System--->Administration--->Hardware Drivers)?  Are you running Compiz?  My nvidia card(s) is also reported to run at 51Hz and I can watch videos just fine.

---

### Post by davosba on 2009-01-29
Change your xorg.conf and add this line to screen section.

"DynamicTwinView"   "False"

---

