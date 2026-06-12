---
title: "soundkonverter doesnt start"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by thebestofall007 on 2009-05-08
is there anyone that is having a problem having soundkonverter not start up when you click on it or run it in the terminal (root or otherwise)? when i enter soundkonverter in the terminal, it outputs nothing and doesnt start up, like it's a broken package. ive tried purging it in synaptic then reinstalling it, but no go.

---

### Post by zvacet on 2009-05-09
Do you have ubuntu-restrictedd-extras installed? If not then 

```
sudo apt-get install ubuntu-restricted-extras
```

Try just to right click on file you like to convert.Let me know is it work.

---

### Post by thebestofall007 on 2009-05-11
> **zvacet said:**
> Do you have ubuntu-restrictedd-extras installed? If not then 

```
sudo apt-get install ubuntu-restricted-extras
```

Try just to right click on file you like to convert.Let me know is it work.

yes i have the restricted extras installed. i got it to work though. what i did was delete the kde (/home/<USERNAME>/.kde) folder because it contained dead symbolic links and then purged soundkonverter by typing:

```
sudo apt-get purge soundkonverter
```

and then removed everything that depends on it:

```
sudo apt-get autoremove --purge
```

i then restarted my machine and then reinstalled the package:

```
sudo apt-get install soundkonverter
```

---

