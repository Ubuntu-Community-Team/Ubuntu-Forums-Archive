---
title: "Lost Sudo rights, had to recreate admin group"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by wiseheart on 2009-02-18
I somehow lost my username from the sudo group. No idea how, I opened up the Users and Groups GUI for the first time today, and added a group named fuse, then closed it. After that my username no longer had sudo access.

I read some other posts regarding this, so I rebooted in recovery mode, ran visudo, and checked to ensure that I had both the lines:
root All = (ALL) ALL 
%Admin All = (ALL) ALL 

Which I did. 

So, not really sure what to do next, I tried adding myself to the admin group. This returned that there was no admin group. So, I created that group and then added myself to it. Now, my sudo is restored. 

Hopefully, that helps someone else if they made the same mistake. Any insight into what caused this would be appreciated.

---

### Post by bodhi.zazen on 2009-02-18
Yes, your user needs to be in the admin group to access sudo.

My observation / advice is to keep in mind linux is case sensative.

The correct group is "admin" , without quotes and you listed "Admin" in your post ..

so [color=red]A[/color]dmin != [color=red]a[/color]dmin

---

### Post by wiseheart on 2009-02-18
> **bodhi.zazen said:**
> Yes, your user needs to be in the admin group to access sudo.

My observation / advice is to keep in mind linux is case sensative.

The correct group is "admin" , without quotes and you listed "Admin" in your post ..

so [color=red]A[/color]dmin != [color=red]a[/color]dmin

Thanks for your advice, although it was merely when typing here as opposed to in the shell. I actually tried it both ways.

---

