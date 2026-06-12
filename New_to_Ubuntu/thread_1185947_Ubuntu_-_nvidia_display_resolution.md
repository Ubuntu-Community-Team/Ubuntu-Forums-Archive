---
title: "Ubuntu - nvidia display resolution"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by cjnkns on 2009-06-12
I know I have seen this on here before so I apologize for a repost. But, I just can't find it.

When ever I use the Nvidia x Server settings to change my resolution when I restart the resolution switches back. How do I run the Nvidia x servers settings so it keeps the resolution the way I want it?

Thanks! :)

---

### Post by Bölvaður on 2009-06-12
yes there is a little strange thing... from the menu it doesn't ask for your password so you are not allowed to save the change.

Alt+F2
```
gksu nvidia-settings

```

after changing resolution press "Save to X Configuration File"

You can also correct the menu item by right clicking the menu, find the nvidia settings manager and change the command to 
```
gksu /usr/bin/nvidia-settings

```

but as /usr/bin is in your PATH variable you can also just write gksu nvidia-settings as it will look for it there.

---

### Post by cjnkns on 2009-06-12
Thank you very much :)

---

