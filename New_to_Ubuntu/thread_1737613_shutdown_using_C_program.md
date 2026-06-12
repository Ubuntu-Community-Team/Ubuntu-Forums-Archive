---
title: "shutdown using C program"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by LittleGyko on 2011-04-23
I am using Ubuntu 10.04. I wanted to write my own power management program in C. For this I need to understand how to get the system to shutdown using a C program. This is the code I wrote. 



#include<stdio.h>
#include<stdlib.h>
int main()
{
        system("shutdown -r now");
}

However, to execute "shutdown -r now" I need to be root. How do I give this program root privileges. 

Thanks in advance.

---

### Post by SteveDee on 2011-04-23
> **LittleGyko said:**
> ...How do I give this program root privileges...

One way is to modify your /etc/sudoers file by adding a line like this:-
```

%admin ALL = NOPASSWD: /sbin/shutdown

```

Your code should use the command string:-
```

sudo shutdown -r now

```
in this case, sudo is used but you are not prompted for a password.

---

### Post by sanderj on 2011-04-23
make root the owner of the executable, and set the s-bit...

---

