---
title: "sony vaio trackpad not working"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by vnpifhf on 2011-02-19
Basically, my trackpad is not working at all, I had an alps pointing driver on windows, the right & left click buttons don't work, it had a side and top down scroll as well.

Sony VPCEE2S1E/BQ

Thanks.

---

### Post by vivek.pandey on 2011-02-19
> **jahangir99 said:**
> Basically, my trackpad is not working at all, I had an alps pointing driver on windows, the right & left click buttons don't work, it had a side and top down scroll as well.

Sony VPCEE2S1E/BQ

Thanks.

by trackpad you mean touchpad or both the terms are different?

---

### Post by vnpifhf on 2011-02-19
[URL="http://en.wikipedia.org/wiki/Touchpad"]yes I meant touchpad.
[/URL]

---

### Post by vivek.pandey on 2011-02-19
> **jahangir99 said:**
> [http://en.wikipedia.org/wiki/Touchpad](http://en.wikipedia.org/wiki/Touchpad)
please read the first sentence.

i guess this may help a bit it has helped me a number of times
the entire command in one line 

gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true

---

### Post by vnpifhf on 2011-02-19
sorry that's not worked but thanks anyway!

---

### Post by Bölvaður on 2011-02-21
let me see your output of this command

```
xinput list
```

---

