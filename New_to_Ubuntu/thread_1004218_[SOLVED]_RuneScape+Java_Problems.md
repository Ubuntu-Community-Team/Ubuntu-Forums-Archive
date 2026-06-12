---
title: "[SOLVED] RuneScape+Java Problems"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by Kyaizen on 2008-12-07
...

---

### Post by taurus on 2008-12-07
You can install java 6 from the repos.  Did it, java, show up when you did the search in Add/Remove?

---

### Post by Kyaizen on 2008-12-07
...

---

### Post by taurus on 2008-12-07
If you installed it (or both versions) from Add/Remove, then you have java on your system.  Not sure what else you are asking here.

To see which version you are using, run this command from a terminal to see what it shows.

```
java -version
```

---

### Post by Kyaizen on 2008-12-07
...

---

### Post by taurus on 2008-12-07
Maybe you need the Sun version plus the plugin.

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
When you get to the licensing screen, press the Tab key to highlight the <OK> and press Return to except it.  Then, see which version you have this time.

```
java -version
```
Don't forget to restart firefox.

---

### Post by Kyaizen on 2008-12-07
...

---

### Post by Kyaizen on 2008-12-07
...

---

### Post by taurus on 2008-12-07
You won't see the cursor moves when you type in your password.  That's normal so just type it in and hit Return when you are done.

---

### Post by Kyaizen on 2008-12-07
...

---

### Post by taurus on 2008-12-07
My mistake (typo).  It should be sun-java6-jre.

```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by Kyaizen on 2008-12-07
...

---

### Post by Kyaizen on 2008-12-07
...

---

### Post by taurus on 2008-12-07
What kind of graphic card do you have and have you installed a driver for it?

System -> Administration -> Hardware Drivers

---

### Post by Kyaizen on 2008-12-07
...

---

### Post by Kyaizen on 2008-12-07
...

---

