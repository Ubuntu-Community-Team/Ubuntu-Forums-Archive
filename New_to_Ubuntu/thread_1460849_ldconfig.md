---
title: "ldconfig"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by newport_j on 2010-04-23
I read about the syntax of ldconfig and how it is used in checking the accessibility of a file:

ldconfig -p | grep libraryname

Now I used it.

errol@fermi:/usr$ ldconfig -p | grep libcutil_i386.a
errol@fermi:/usr$ 

I am unsure of the response which in this case is nothing. Does that mean that the library is not accessible? What does this output in this case mean? 

Newport_j

---

### Post by talonmies on 2010-04-24
> **newport_j said:**
> I read about the syntax of ldconfig and how it is used in checking the accessibility of a file:

ldconfig -p | grep libraryname

Now I used it.

errol@fermi:/usr$ ldconfig -p | grep libcutil_i386.a
errol@fermi:/usr$ 

I am unsure of the response which in this case is nothing. Does that mean that the library is not accessible? What does this output in this case mean? 

Newport_j

It shows the available shared libraries in the current link loader search paths. The name of the library you are looking for has a .a extension, which makes it a static library. As a result, the link loader will have no role in the use of that library, and whether it prints something out or not is no indication of whether the library exists or not.

---

