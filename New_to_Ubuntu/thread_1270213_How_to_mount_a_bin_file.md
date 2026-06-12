---
title: "How to mount a bin file?"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by karthick87 on 2009-09-19
I know .bin file was a image of cd/dvd,in windows i used poweriso to mount the file.But here in ubuntu i want to know how to mount a .bin file?
  
                     Thanks in advance..

---

### Post by Malta paul on 2009-09-19
Put the file in your /home directory.
In the terminal, sudo apt-get install sh 'your file'

---

### Post by seshomaru samma on 2009-09-19
try [this ]("http://www.acetoneteam.org/")

---

### Post by scorp123 on 2009-09-19
> **Malta paul said:**
> Put the file in your /home directory.
In the terminal, sudo apt-get install sh 'your file' You not only did not understand what OP is asking, your instructions are plain wrong and don't even work. You never ever install local files with "apt get install". Please do some Googling before giving people false recommendations and bad advice, yes?

---

### Post by Malta paul on 2009-09-19
Thanks for correcting me. Perhaps you would care to give getyourkarthick the answer to his question?:confused:

---

### Post by scorp123 on 2009-09-19
> **Malta paul said:**
> Perhaps you would care to give getyourkarthick the answer to his question?

[http://ubuntuforums.org/showpost.php?p=7974022&postcount=3](http://ubuntuforums.org/showpost.php?p=7974022&postcount=3)

---

### Post by scorp123 on 2009-09-19
> **getyourkarthick said:**
> But here in ubuntu i want to know how to mount a .bin file? I'd recommend you convert the file into ISO first. Mounting an *.iso file is easy.

[http://www.linuxtent.com/?p=82](http://www.linuxtent.com/?p=82)
[http://www.alterego7.com/2008/03/convert-bin-to-iso-in-ubuntu.html](http://www.alterego7.com/2008/03/convert-bin-to-iso-in-ubuntu.html)

And there's "CDemu":
[http://cdemu.sourceforge.net/](http://cdemu.sourceforge.net/)

Ubuntu packages can be downloaded from here (they also have their own repos):
[http://cdemu.sourceforge.net/project.php#binary](http://cdemu.sourceforge.net/project.php#binary)

But this "client & server" model that CDemu uses to simulate a CD drive is quite complicated ... and IMHO not really necessary as on Linux one could mount any *.ISO file directly without the extra help of any background programs.

---

### Post by Oaklar on 2012-07-10
> **scorp123 said:**
> I'd recommend you convert the file into ISO first. Mounting an *.iso file is easy.

[http://www.linuxtent.com/?p=82](http://www.linuxtent.com/?p=82)
[http://www.alterego7.com/2008/03/convert-bin-to-iso-in-ubuntu.html](http://www.alterego7.com/2008/03/convert-bin-to-iso-in-ubuntu.html)


The above urls that you have indicated are not correct as they are either redirecting to a different site all-together or else they no longer have the info you expected them to hold.
  But what i think is that the info is no longer helpful through that site.

---

### Post by Mark Phelps on 2012-07-10
> **karthick87 said:**
> I know .bin file was a image of cd/dvd,in windows i used poweriso to mount the file.But here in ubuntu i want to know how to mount a .bin file?
  
                     Thanks in advance..

Once again, it seems that folks don't bother to actually READ the OP's question before providing (wrong) advice!

The .bin file is NOT an executable; instead, it is a form of compressed archive -- often complemented with a .cue file.

Perhaps the info in the link below can be of some help:

[http://goinggnu.wordpress.com/2007/05/08/howto-mount-bincue-files-in-linux/]("http://goinggnu.wordpress.com/2007/05/08/howto-mount-bincue-files-in-linux/")

---

### Post by oldos2er on 2012-07-10
Old thread closed.

---

