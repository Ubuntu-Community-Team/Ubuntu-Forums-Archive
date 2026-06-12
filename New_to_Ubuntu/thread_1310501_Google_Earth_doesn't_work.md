---
title: "Google Earth doesn't work"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by wheatpenny on 2009-11-01
I downloaded and installed Google Earth and although there is an icon for it, when I click on the icon nothing happens. (I'm running Ubuntu 9.10). I never had Google Earth on 9.04 so I don't know if the upgrade has anything to do with it.

---

### Post by IgnorantGuru on 2009-11-01
try running it from a console with
```
googleearth
```

That way you can see any error.  If it can't find it, you'll have to specify the full path, which will vary depending on where you installed it.  You could try
```
~/google-earth/googleearth
```

or do a search for it.

---

### Post by mrboojive on 2009-11-01
How did you download and install it? I think adding the Medibuntu repository and then installing the googleearth package is the easiest way, and I've never had any problems getting it to run: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by wheatpenny on 2009-11-02
> **mrboojive said:**
> How did you download and install it? I think adding the Medibuntu repository and then installing the googleearth package is the easiest way, and I've never had any problems getting it to run: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I downloaded it off Goggle Earth's website and installed it with the terminal.

---

### Post by Paddy Landau on 2009-11-02
GoogleEarth has been a problem on Linux from the get-go, despite Google being very pro-Linux.

As the previous poster said, uninstall it completely and install from Medibuntu. That will give you greatest chance of success.

Unfortunately, whether it works, doesn't work, or indeed crashes Linux, is a matter of pot-luck.

It works on two of my machines, and not on a third (even though it works on Windows on that same machine). No known reason, no known solution.

Good luck.

---

### Post by philinux on 2009-11-02
I've always installed by activating the medibuntu repos then install via synaptic. Had a 100% success rate with this on numerous machines.

---

