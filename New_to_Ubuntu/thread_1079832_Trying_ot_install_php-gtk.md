---
title: "Trying ot install php-gtk"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by cerealtx on 2009-02-24
trying to install php-gtk so i can make some cross platform apps, when trying to build from source i get this...
```
cereal@cereal-desktop:~/Desktop/php-gtk-2.0.0$ ./buildconf
/bin/sh: phpize: not found
make: *** [buildmk.stamp] Error 127

```

can't find any info on phpize

---

### Post by sandyd on 2009-02-24
for php5...
```

sudo apt-get install php4-dev

```for php5...
```

sudo apt-get install php5-dev 

```

contradiction to your sig ;) ([http://www.google.ca/search?q=phpize+not+found&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=phpize+not+found&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a))

---

### Post by cerealtx on 2009-02-24
> **carlee said:**
> for php5...
```

sudo apt-get install php4-dev

```for php5...
```

sudo apt-get install php5-dev 

```

contradiction to your sig ;) ([http://www.google.ca/search?q=phpize+not+found&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=phpize+not+found&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a))

yah, thanx yah i had found it already from the php-devel thought it was a lib not a function,

---

