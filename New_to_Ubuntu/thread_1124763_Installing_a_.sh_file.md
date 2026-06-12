---
title: "Installing a .sh file"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by smithwk2 on 2009-04-13
How to I install a program on Ubunutu that has a .sh extension?  Thanks in advance.

---

### Post by taurus on 2009-04-13
You just run it from a terminal to install it.

```
chmod +x filename.sh
./filename.sh
-or-
sudo ./filename.sh (If you need root privilege.)
```

---

### Post by eeeandrew on 2009-04-13
you first need to set it so that it can be executed as a program. right click the file select properties choose the permissions tab and check "allow executing program as file". Next you can double click file and it will run. This can also be done from command line...not sure how to do the first bit but to run it navigate to the directory the file is in and then type 

./ file.sh 

where file.sh is the name of the file.

Hope this helps,
Andrew

---

### Post by Jakey_TheSnake on 2009-04-13
You can cd to the directory, then type in:

"sh filename.sh"

---

