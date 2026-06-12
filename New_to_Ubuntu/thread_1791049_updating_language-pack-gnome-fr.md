---
title: "updating language-pack-gnome-fr"
date: 2011-06-26
forum: New to Ubuntu
---

### Post by mkornig on 2011-06-26
Good morning from France,

When updating this package is listed but greyed out on my system. So I can't click on/activate it to be updated. To me this seems like a contradiction: why list a package and then not allow it to be updated?

Additional information: I use GNOME and most of my communication is in French. So updating this package seems to be important.

---

### Post by mikewhatever on 2011-07-01
Not quite sure. What do you get when running the following in a terminal:

```
sudo apt-get install language-pack-gnome-fr
```

---

### Post by mkornig on 2011-07-04
> **mikewhatever said:**
> Not quite sure. What do you get when running the following in a terminal:

```
sudo apt-get install language-pack-gnome-fr
```

Thanks, Mike.

Please, see attached file for my system's response.

It seems that other packages (and/or more recent versions) are needed. I'll look into this and report back here.

---

### Post by mkornig on 2011-07-04
After analysing the response I got once again, it seems that the system requires OLDER versions than those already installed on my system (in order to satisfy some kind of denpencies?). That's strange, isn't it?
 
In order to fix this I uninstalled the following packages :

[LIST=1]
[*]language-pack-gnome-fr
[*]language-pack-gnome-fr-base
[*]language-pack-fr
[*]language-pack-fr-base
[*]language-support-fr
[/LIST]
Then I tried to install these packages again in reversed order. Installing 5, 4, 3 back went smoothly. However, when reinstalling the last two, i.e.

[LIST]
[*]language-pack-gnome-fr-base
[*]language-pack-gnome-fr
[/LIST]
I get the following error message "Package dependencies cannot be resolved".

What next? Any ideas welcome.

---

### Post by mkornig on 2011-07-04
By the way: After uninstalling French, Gnome speaks English now (the default language?). Which is fine for me right now.

---

### Post by mkornig on 2011-07-05
Well it appears to be Frenglish. A strange mixture of French and English...

---

### Post by mkornig on 2011-07-08
> **mkornig said:**
> After analysing the response I got once again, it seems that the system requires OLDER versions than those already installed on my system (in order to satisfy some kind of denpencies?). That's strange, isn't it?
 
In order to fix this I uninstalled the following packages :

[LIST=1]
[*]language-pack-gnome-fr
[*]language-pack-gnome-fr-base
[*]language-pack-fr
[*]language-pack-fr-base
[*]language-support-fr
[/LIST]
Then I tried to install these packages again in reversed order. Installing 5, 4, 3 back went smoothly. However, when reinstalling the last two, i.e.

[LIST]
[*]language-pack-gnome-fr-base
[*]language-pack-gnome-fr
[/LIST]
I get the following error message "Package dependencies cannot be resolved".

What next? Any ideas welcome.

Since some of the packages 3, 4 and 5 have been updated recently, I tried reinstallation of 1 and 2 again. I there have been any problems at this time. :)

I'm back to French any happy. Cheers, Martin

---

