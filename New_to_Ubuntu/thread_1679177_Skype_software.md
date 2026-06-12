---
title: "Skype software"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by hero2011 on 2011-01-31
I have tried installing the skype in my Ubuntu 10.10 but i can't even see it in the software center.so how can have it since i need to use it.any help?

---

### Post by weedeater64 on 2011-01-31
Did you download a .deb from the skype page?

If so navigate to the folder where it is and 

```
cd /where/ever/you/put/it
```

```
dpkg -i package.deb
```

replacing "package" with what ever the actual name  of the file is.

---

### Post by arochester on 2011-01-31
Or just RIGHT click on the .deb and choose "Install with Gdebi"

---

### Post by uRock on 2011-01-31
Skype should be listed in the Software Center.

Once installed, it should be in the Applications> Internet menu. and once opened, it should have an icon in the Notification Area.

---

### Post by bwestover on 2011-01-31
There is only beta support for Skype on Linux.

You can get the beta [here]("http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/")

After downloading, use the instructions weedeater gave you.

Edit: Or what arochester said, which is probably easier :)

> Or just RIGHT click on the .deb and choose "Install with Gdebi"

---

### Post by Cleanser23 on 2011-01-31
Open software center, click edit and Software sources all the way at the bottom, then make sure Canonical parters is checked :D

---

### Post by hero2011 on 2011-01-31
@Cleanser23.i have tried that and now it is downloading.
Thanks for all your suggestions.Really this forum has been of great benefit to me.

---

