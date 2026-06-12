---
title: "How to connect To my school server... HTTPS or wHat????"
date: 2006-09-14
forum: Networking &amp; Wireless
---

### Post by BOBSONATOR on 2006-09-14
I connected using the connect to server..

Then it shows up as a little icon on my desktop. when i click on it, it opens up in firefox, not a folder, and i need to place files in this folder, if anyone can help, that would be nice.

Thanks.

---

### Post by Jussi Kukkonen on 2006-09-14
Please be a little more specific. What do you want to happen? What have you tried already, how did it fail (and has this worked before)? What kind of a connection/server are you talking about (I'm guessing it's SMB -- windows filesharing)?

---

### Post by BOBSONATOR on 2006-09-14
I want to open up my folder in the server just like i would a normal folder.

The address to the server is [https://lhfs01.svusd.org/students/yassamis025](https://lhfs01.svusd.org/students/yassamis025), and my username is yassamis025. 

So i guess i would use https? so i connect to server using https, and then i get an icon on my desktop. i can click on it but the folder does not show up.

So i was told to open up a blank folder, and press contol L, then type [https://lhfs01.svusd.org/students/yassamis025](https://lhfs01.svusd.org/students/yassamis025), so i did and it says nautalis cannot display the folder, so do i need another viewer to put my files in there?

Thanks.

---

### Post by Jussi Kukkonen on 2006-09-15
https is web... Have you tried a web browser?

EDIT: it can also be webDAV (which is more likely if you are supposed to be able to write there too), that should work from *Places --> Connect to Server* (select webdav, fill in the rest)

---

### Post by BOBSONATOR on 2006-09-15
I did that, and when i log in, it doenst accept my pass for a reason...but i can still connect through firefox.
and i also installed samba...

heres a screen.
[http://img166.imageshack.us/img166/2395/screenshotsj0.png](http://img166.imageshack.us/img166/2395/screenshotsj0.png)

---

### Post by BOBSONATOR on 2006-09-15
bump...

Comon, someone has to know...

Thanks.

---

### Post by frankos44 on 2007-11-11
This worked for me:

$ sudo apt get install cadaver
$ cadaver [https://domain.com/path/folder/](https://domain.com/path/folder/)

login in using your school username and password

Hey presto!

type "help" to get list of commands. e.g.  to get a file from the server type 

mget filename. (shoves it in your home folder)

Hope this helps

---

