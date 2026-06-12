---
title: "Can't find stdio.h"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by Poincare101 on 2009-04-11
I did sudo aptitude install build-essential and I got all the stuff. But when I try to compile a program this is what I get:

dhaivatpandya@LinuxDesktop:~/Desktop$ gcc someCode.c 
someCode.c:1:20: error: stdio.h: No such file or directory
someCode.c: In function ‘main’:
someCode.c:4: warning: incompatible implicit declaration of built-in function ‘printf’
someCode.c:3: warning: return type of ‘main’ is not ‘int’
dhaivatpandya@LinuxDesktop:~/Desktop$ 


please help!

---

### Post by CLomax on 2009-04-11
If you can paste the part of the source where you are calling the stdio.h header, that would help us help you. :)

---

### Post by Poincare101 on 2009-04-11
#include <stdio.h>

void main (void) {
     printf("It works!");

}

---

### Post by Joeb454 on 2009-04-11
You need to install [build-essential]("apt://build-essential") by either clicking that link or running ```
sudo apt-get install build-essential
``` :)

---

### Post by taurus on 2009-04-11
Or maybe make it look something like

```

#include <stdio.h>

main ()
{
printf("It works!");
}
```

---

### Post by ibuclaw on 2009-04-11
> **Poincare101 said:**
> I did sudo aptitude install build-essential and I got all the stuff. But when I try to compile a program this is what I get:

dhaivatpandya@LinuxDesktop:~/Desktop$ gcc someCode.c 
someCode.c:1:20: error: stdio.h: No such file or directory
someCode.c: In function ‘main’:
someCode.c:4: warning: incompatible implicit declaration of built-in function ‘printf’
someCode.c:3: warning: return type of ‘main’ is not ‘int’
dhaivatpandya@LinuxDesktop:~/Desktop$ 


please help!

I have managed to replicate your error message by removing stdio.h from the system, and it is installed by default along with gcc as a dependency. So I'm not sure what is going on there.

Try reinstalling the package which has stdio.h inside.
```
sudo apt-get install --reinstall libc6-dev
```
Regards
Iain

---

