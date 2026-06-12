---
title: "switching buttons locations"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by Existance0 on 2010-05-04
I finally upgraded to 10.04 and the close/maximize/minimize buttons are all on the left side. Also in dialog boxes all the buttons seem switched. I can't find where you change this back would someone mind telling me?

---

### Post by spaik on 2010-05-04
> **Existance0 said:**
> I finally upgraded to 10.04 and the close/maximize/minimize buttons are all on the left side. Also in dialog boxes all the buttons seem switched. I can't find where you change this back would someone mind telling me?

use Ubuntu tweak!

---

### Post by theozzlives on 2010-05-04
> **Existance0 said:**
> I finally upgraded to 10.04 and the close/maximize/minimize buttons are all on the left side. Also in dialog boxes all the buttons seem switched. I can't find where you change this back would someone mind telling me?

I don't think there is. I made a stink about it during the Alpha phase. I guess we got to live with it. To get the context menu, right-click on the title bar.

---

### Post by r-senior on 2010-05-04
You haven't done a search have you? [-X

It may have come up, once or twice. :D

[http://ubuntuforums.org/showthread.php?t=1469475]("http://ubuntuforums.org/showthread.php?t=1469475")

---

### Post by spaik on 2010-05-04
> **theozzlives said:**
> I don't think there is. I made a stink about it during the Alpha phase. I guess we got to live with it. To get the context menu, right-click on the title bar.

u can change them back very easily :) just use ubuntu tweak :) there is a code to do that, but i like the ubuntu tweak better :)

---

### Post by Cavsfan on 2010-05-04
or just enter this in terminal:

 ```
 gconftool-2 --set /apps/metacity/general/button_layout --type string menu:minimize,maximize,close
```

EDIT: a little late!

---

### Post by Calash on 2010-05-04
Please see the following thead.

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by r-senior on 2010-05-04
It might be worth quoting this part of that link too ...

> Using gconf-editor is not the right approach as this could bork future themes. This change makes it easier for themes to do interesting things with window borders. Unfortunately, if the wrong approach spreads, they won't be able to do that.

What does Ubuntu Tweak do BTW? Is it potentially going to cause the same problems as gconf-editor?

---

### Post by Cavsfan on 2010-05-04
Not sure, but at the time I did it, it was the only way to get it done.
EDIT: And I believe I am fine.

---

### Post by Norm24 on 2010-05-04
This fixes that issue:

[http://wojox.homelinux.org/?p=65](http://wojox.homelinux.org/?p=65)

---

### Post by Vined Adobo on 2010-05-04
> **Existance0 said:**
> I finally upgraded to 10.04 and the close/maximize/minimize buttons are all on the left side. Also in dialog boxes all the buttons seem switched. I can't find where you change this back would someone mind telling me?

Open a terminal.  type gconf-editor

When configuration editor opens, expand Apps.  Scan down down to meta city.  Expand Metacity and select general.  Change "button_layout" key from menuclose,maximize,minimize: (or however it's written there) and replace it with menu:minimize,maximize,close Note that the colon placement determines if the buttons will be on the right or left side

Write what it says when you start so you can put it back if you want.

Dave

---

### Post by Existance0 on 2010-05-04
Thanks, you are correct I did not do a search for this but really... I didn't know what to call it lol. I'll go with ubuntu tweak since apparantly the other option can break themes.

---

### Post by Cavsfan on 2010-05-04
> **Norm24 said:**
> This fixes that issue:

[http://wojox.homelinux.org/?p=65](http://wojox.homelinux.org/?p=65)


Isn't that exactly like the code I entered above?
It sure looks like it...

---

### Post by philinux on 2010-05-04
See the sticky in General Help re lucid.

---

### Post by Cavsfan on 2010-05-04
> **philinux said:**
> See the sticky in General Help re lucid.

I guess we should pay more attention to those stickys! #-o

---

### Post by Calash on 2010-05-04
> **Existance0 said:**
> Thanks, you are correct I did not do a search for this but really... I didn't know what to call it lol. I'll go with ubuntu tweak since apparantly the other option can break themes.

They all do the same thing, so no worries about one breaking a theme that the others will not.

---

