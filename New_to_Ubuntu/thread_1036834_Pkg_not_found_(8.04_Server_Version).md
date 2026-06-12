---
title: "Pkg not found (8.04 Server Version)"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by 10sJunkie on 2009-01-11
Background: I bought an entry level server with 8.04 Server installed my the manufacturer... Have never used Ubuntu and have basically zero linux experience. My goal is to set up and run my own web server.

Not sure if this is an error or not but my base version appears not to have the packages included. I tried: sudo apt-get install konqueror and got "konqueror package not found" (or somthing similar). Maybe this is normal for Server version but my question is this:

How can I get and install the packages I want? I want konqueror for sure - maybe others.

Thanks in advance!

---

### Post by RealPSL on 2009-01-11
I am not sure what the vendor installs by default but Konqueror is from Kubuntu (KDE). A default Ubuntu (Gnome) installation would not have Konqueror installed by default but can be added. Most people will also say that they would rather not have GUI packages installed on their server because of added none server load but it is a personal preference. Try the following and see if it works if not we will try and assist.

Please try ```

sudo apt-get update
apt-cache search konqueror | grep konqueror

```

If the second command above does not produce any results please send ```
cat /etc/apt/sources.list
```.

If the second command above does produce konqueror as one of the results then please run your original ```
sudo apt-get install konqueror
```

---

### Post by 10sJunkie on 2009-01-11
Looks like a bunch of stuff updated and the apt-cache search gives a list of konqueror items but I think I will heed your advice (and the advice of others) and not install it.

Thanks!

---

### Post by stevoo on 2009-01-11
true Konqueror ... is not needed if you are using ubuntu. Youll just be installing tons of stuff for no special reason !

---

