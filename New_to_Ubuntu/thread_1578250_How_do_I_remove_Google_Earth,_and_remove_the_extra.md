---
title: "How do I remove Google Earth, and remove the extra icon."
date: 2010-09-20
forum: New to Ubuntu
---

### Post by DesiArnez6 on 2010-09-20
I downloaded the Google Earth installation file and it did not work properly. Instead, it gives me an error:

"NOTICE Google Earth could not write to the current cache or My Places file location. The values will be set as follows:
My Places Path: "/home/desiarnez6/.googleearth"
Cache Path: "/home/desiarnez6/.googleearth/Cache""

And then instead of the map, I get mostly black screen, and then if I open another window, and then minimize it, the black part where the Google Earth should be instead has the contents of the previous window.

My goal is to remove Google Earth Completely, and then remove both icons from the Applications menu (Wheun it "installed" It left two icons for some reason, only one of which has the correct Google icon. The other one is a white box with a blue top.) I then plan to reinstall Google Earth from the repositories.

Is this a good idea? (I seem to remember editing a text file with me last computer with gedit to get it to work. I don't remember exactly what I did :(

Thanks in advance for your help.

-Desi

---

### Post by ubudog on 2010-09-20
There should be a uninstall script, to find it:
```
locate uninstall
```

And for the menu items, go to System>Prefs>Main Menu, and click on whatever tab it put it in, click on Google Earth, and select delete on the right side.

---

### Post by DesiArnez6 on 2010-09-22
> **ubudog said:**
> There should be a uninstall script, to find it:
```
locate uninstall
```

And for the menu items, go to System>Prefs>Main Menu, and click on whatever tab it put it in, click on Google Earth, and select delete on the right side.

I couldn't find the uninstall file. :( When I typed "locate uninstall" all that popped up were "thunderbird langpacks", "libgnomeprint" files, and "screen-launcher-uninstall" :confused:

*I did manage to delete the extra google icon like you said, by going to: "System>Prefs>Main Menu". That is a good tip to know. I had no idea it was so simple

---

### Post by ubudog on 2010-09-22
Yeah, it is pretty simple.  A quick google search got me this:

[http://ubuntuforums.org/showthread.php?t=208254](http://ubuntuforums.org/showthread.php?t=208254)

---

### Post by DesiArnez6 on 2010-09-22
> **ubudog said:**
> Yeah, it is pretty simple.  A quick google search got me this:

[http://ubuntuforums.org/showthread.php?t=208254](http://ubuntuforums.org/showthread.php?t=208254)

I just typed this: "cd /usr/local/google-earth
" and all I got was: "No such file or directory

I'm getting frustrated again :(

---

### Post by ubudog on 2010-09-22
Then I guess it's not there.  That may be why it didn't work in the first place.  Type this into a terminal.

```
sudo updatedb
```

then,

```
locate google
```

---

