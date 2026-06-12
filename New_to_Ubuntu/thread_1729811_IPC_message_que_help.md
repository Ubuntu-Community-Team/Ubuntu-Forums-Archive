---
title: "IPC message que help"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by Rakesh_trap on 2011-04-15
I am seeing a strange behaviour while sending a structure whose  itemare unsigned char.
As per  example in &quot;Opening a POSIX message queue in Linux without root privileges - Ubuntu Forums&quot; Programs works properly but if change the data as

typedef struct
{
 unsigned char  x;
 unsigned char y;
 unsigned char z;
} Msg;

receiver starts giving error as message size too long.

Please help me in understanding the issue.
Thanks for your help.  Problem is  solved

---

