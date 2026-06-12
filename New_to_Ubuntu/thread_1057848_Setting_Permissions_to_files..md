---
title: "Setting Permissions to files."
date: 2009-02-02
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-02-02
Hi Guys Im on the customizing cd part of my ubuntu adventure and I have ubuntu installed on a external harddrive. I am trying to give permissions to a few files so I can go in and edit the text to change the background of the live cd I am going to create, I tried lots of commands for chmod and chown but maybe Im doing it wrong and advice?

---

### Post by Neural oD on 2009-02-02
well what permissions do u want to give

---

### Post by ithanium on 2009-02-02
to edit a text file with adminitrator permissions, enter in Terminal and type:
```

gksudo gedit path_to_file

```

---

### Post by Neural oD on 2009-02-02
i use this: sudo chmod xxx /your-files
where first x is for owner,second for group and third for others
you must replace the x's as such 4 - read 2 - write 1 - execute 
so a 6 would mean read and write where 7 is full permissions.
Hope i've made myself clear

---

