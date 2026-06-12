---
title: "Where in Eclipse can I tell it to use Sun Java?"
date: 2009-01-13
forum: New to Ubuntu
---

### Post by mojo_man on 2009-01-13
Hi,

I am new to Ubuntu. I have Sun JRE 6 installed in Ubuntu through Synaptic. But my eclipse keeps using gcj. How can I tell it to use Sun?

I cannot seem to find the configuration option in the menu.

Thanks

---

### Post by andrewc6l on 2009-01-14
There are two places.

If you're talking about using Sun Java to run Eclipse, start Eclipse with the -vm option and give it the path to the Sun executable:
eclipse -vm /path/to/jdk/bin/java
You can set this permanently in an Eclipse .ini file - see here: [http://wiki.eclipse.org/Eclipse.ini](http://wiki.eclipse.org/Eclipse.ini)

If you're talking about using Sun JDK to run your programs, you want to select Windows -> Preferences -> Java -> Installed JREs and add the Sun JDK as a VM.
[http://books.google.com/books?id=cGYMActRiakC&pg=PA98&lpg=PA98&dq=installed+JREs+eclipse&source=web&ots=vAomObyO3u&sig=wM7VG7azvUPvsp5lIJo6oYsubxk&hl=en&sa=X&oi=book_result&resnum=10&ct=result](http://books.google.com/books?id=cGYMActRiakC&pg=PA98&lpg=PA98&dq=installed+JREs+eclipse&source=web&ots=vAomObyO3u&sig=wM7VG7azvUPvsp5lIJo6oYsubxk&hl=en&sa=X&oi=book_result&resnum=10&ct=result)

---

