---
title: "Very Easy Network Question"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by bradacus on 2009-06-08
I have Ubuntu running on my computer. I am an extreme newbie but have a good knowledge of windows networking.
 
I am trying to access an old linux server from ubuntu.
 
When I access it - it shows me the two windows files on the windows share of the hard drive and it won't show me the linux share.
 
How can I access the linux share on that server?
 
Thanks.

---

### Post by 123456789123456789123456 on 2009-06-08
strange, what format was the linux share?  file format, you said it was old server.  try command line access.  in terminal, type ls -l and the address of the linux share on the linux server after the ls -l command.  that should list on the screen every file on the share, along with the files owner, group owner, and permissions.  It is possible that the files were hidden, which means that Ubuntu would honor the hidden permission in the GUI interface, but through command line it should appear.
The only other thing I can think of is that the file system that the linux share is using, may be too old for Ubuntu to read and understand 100% correctly, though i doubt it.

---

### Post by bradacus on 2009-06-09
I am not sure on the file format of the old linux box.  However I do know the server was built in 1984 which would make the server 24 years old....

I am able to access the server remotely through terminal... however the directory is a complete labyrinth.  I have no clue how to locate the files I am looking for because I have never been in here before...

All I know is that somewhere on that server there is an area with a lot of storage that I need to clear out.  If i can find the largest folder in a directory I can just sniff out the files I need that way.  In terminal how can I get a view of the folder and/or file sizes of a certain directory?  

Thanks for your previous answer it helped me get this far.

---

### Post by superprash2003 on 2009-06-10
are you sharing files via samba?

---

### Post by dileepm on 2009-06-10
Use latest Samba that makes sense.

---

### Post by valex on 2009-06-10
> **dileepm said:**
> Use latest Samba that makes sense.

yes. [samba]("http://us1.samba.org/samba/") is a good solution for file sharing.

---

