---
title: "conky setup"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by drtejams on 2011-08-10
hi guys,
just installed unity and want to install conky , after browsing from different sites i have installed conky and after running it i get a black window with details in it on the left side of the screen, how can i install new themes and change the location of my conky  and add widgets
bye

---

### Post by SoFl W on 2011-08-10
There are no "themes", it is all in how you design the configuration.  To find out more, **[start here]("http://ubuntuforums.org/showthread.php?t=281865")**.
Also the [conky document]("http://conky.sourceforge.net/docs.html") page should help.

---

### Post by hookitup on 2011-08-10
^^^^ thats a little confuseing ,, what you want to do is open its config file by doing this command ```
gedit ~/.conkyrc
```

then you can go to a website like this 

[http://conky.sourceforge.net/screenshots.html](http://conky.sourceforge.net/screenshots.html) and just click the little conykyrc button and a config will come up 

or 

[http://ubuntuforums.org/showthread.php?t=281865&highlight=conky+config](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky+config)

they have lots of good ones ,,, you basically going to delete the content in the text editor that pops up when you run the above command and then paste one of these codes from either website..... beware some of the configs from the first sight did not work for me.

---

### Post by Frogs Hair on 2011-08-10
There are themes available at  [http://gnome-look.org](http://gnome-look.org) , just search Conky.
There are some things to do before installing a theme or using / making a Conky configuration .
```
sudo apt-get install conky-all
```
```
sudo apt-get-get install lm-sensors
```
```
sudo sensors-detect
```

Answer yes to all questions. At this point you can close the terminal and start Conky by using Alt+F2 and enter ```
conky
```
To stop Conky use Alt+F2 ```
killall conky
```

You will find the basic setup outright fugly . Now you can look at finding a theme /configuration . One that is very easy to install and provides a lot of information is this .[http://gnome-look.org/content/show.php/Conky+Flavours?content=94467](http://gnome-look.org/content/show.php/Conky+Flavours?content=94467)

---

