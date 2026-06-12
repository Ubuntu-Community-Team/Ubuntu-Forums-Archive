---
title: "uninstall - Dynamic Wallpaper"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by Eld.Raven on 2009-05-03
Hey

I downloaded a application called Dynamic wallpaper (thats at least what its says on the launch icon) but now that I have installed it I notice that it doesnt work as I want to, and now I want to uninstall it. I have tried to check all installed packages threw dpkg-commands and threw "Synaptic Package manager" but I cant find it. And since I dont know what its called I cant uninstall it.

And I am very new to Linux, that could be why I dont know how to find it.

Greetings // Sebastian

---

### Post by imagia on 2009-05-03
Try searching for "drapes". That might show you the program.

---

### Post by Eld.Raven on 2009-05-03
Yeah I found it.. But I its not marked as installed. I have tried running "-ps A" to find it, but I dont know how to sort it out from the rest of the apps. Since Im not used to Linux I dont know what the different apps are doing. =/

---

### Post by Eld.Raven on 2009-05-03
Hmm well I know what the name of the package was or the "install-file".

dynamic-wallpaper_0.3.1-1~getdeb1_all.deb
can be found here: [http://www.gnomefiles.org/app.php?soft_id=2515](http://www.gnomefiles.org/app.php?soft_id=2515)

---

### Post by aikiwolfie on 2009-05-03
In my experience the name of the .deb package is what appears in Synaptic. So I'd search for that. Other wise double click on the package and see what Gdebi offers to do for you.

---

### Post by Eld.Raven on 2009-05-03
Hmm yeah that is weird, cuz I cant find it in the Manager. But when I try to run it again the only option I get is to reinstall it.

---

### Post by aikiwolfie on 2009-05-04
You should be able to look inside the package from nautalus. See what files are in there. Search for those.

---

### Post by Didius Falco on 2009-05-04
> **Eld.Raven said:**
> Hmm well I know what the name of the package was or the "install-file".

dynamic-wallpaper_0.3.1-1~getdeb1_all.deb
can be found here: [http://www.gnomefiles.org/app.php?soft_id=2515](http://www.gnomefiles.org/app.php?soft_id=2515)

You'd use```
 sudo dpkg -r dynamic-wallpaper_0.3.1-1~getdeb1_all.deb
```in a Terminal shell. 

To remove any future *.deb packages you download and install you can use the same format ```
sudo dpkg -r package_name
```where *package_name* is replaced with the name of the package.

I hope this helps...

---

### Post by Eld.Raven on 2009-05-04
Sry Didius it didnt work.

```
dpkg: you must specify packages by their own names, not by quoting the names of the files they come in
```

---

### Post by Didius Falco on 2009-05-04
This will do the trick. I just installed it and purged it from my system to test it.


```
sudo dpkg --purge dynamic-wallpaper
```
[]("http://sourceforge.net/project/showfiles.php?group_id=210448&package_id=320590#")

---

### Post by Eld.Raven on 2009-05-04
Hehe WEI!

Thanks, finally its gone! =)

---

### Post by Didius Falco on 2009-05-04
My pleasure!

Please mark this thread as solved.

In case you don't know how to do that, just edit your first message, click the Go Advanced button and type "solved" at the front of the thread title, which is just above the text box. That will help others with the same problem to find an answer during a search.

Regards,

Didius

---

### Post by gmoctav on 2009-05-16
Thanks , Didius !

---

