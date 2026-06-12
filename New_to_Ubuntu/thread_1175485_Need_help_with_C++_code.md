---
title: "Need help with C++ code"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by SKYDOS on 2009-06-01
i have this code (screen): [http://s45.radikal.ru/i107/0906/44/428550d6e369.png](http://s45.radikal.ru/i107/0906/44/428550d6e369.png)
and error a little bit lower...
what's the problem?
thanks!

---

### Post by SKYDOS on 2009-06-01
i relly need help...
i have downloaded all what i needed - gcc, g++, make, gdb...
but i have this stupid error :(

---

### Post by thomps on 2009-06-01
cout belongs to the std namespace.  Therefore you will need to either do one of the following:

```
using namespace std;
```

just below your includes but above main

or you can change cout to:

```
std::cout
```

---

### Post by SKYDOS on 2009-06-01
> **thomps said:**
> cout belongs to the std namespace.  Therefore you will need to either do one of the following:

```
using namespace std;
```just below your includes but above main

or you can change cout to:

```
std::cout
```

but why it's not working just with "linking" iostream.h library ?

thanks! now it's working.:popcorn:

---

