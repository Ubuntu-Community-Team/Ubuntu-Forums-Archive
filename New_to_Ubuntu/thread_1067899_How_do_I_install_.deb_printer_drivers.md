---
title: "How do I install .deb printer drivers?"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by Bearly Able on 2009-02-12
Hi All,

I'm trying to configure an Epson Stylus Office BX300F all-in-one printer.  I've downloaded the drivers from Epson as .deb files, but I'm not sure how to go about installing them.  Can I just use ```
sudo dpkg -i *.deb
``` Is this the right command, and will the drivers be installed in the right directory?

Second question: can anyone recommend a good book to help me understand the command line stuff, so I don't have to ask so many daft questions on the forums?  I have a good general book (Beginning Ubuntu Linux - Novice to Professional by Keir Thomas), but it only has a brief section on using the command line.

Thanks for any help you can offer on either question.

Lesley

---

### Post by scragar on 2009-02-12
That command will work, although there is a gui which looks better if you just double click the isntaller(or atleast there is in ubuntu, not sure about Xubuntu).

I think it is easier to learn what you need on the command line and learn it step by step, getting some comprehensive guide might be nice, but it will likely be more confusing than anything else.

---

### Post by Sub101 on 2009-02-12
In general with .deb you can double click and they will run.

---

### Post by mc4100 on 2009-02-12
> **Lesley Lutomski said:**
> Can anyone recommend a good book to help me understand the command line stuff, so I don't have to ask so many daft questions on the forums?  I have a good general book (Beginning Ubuntu Linux - Novice to Professional by Keir Thomas), but it only has a brief section on using the command line.

Thanks for any help you can offer on either question.

Lesley
It's not a book, but:
[http://www.linuxcommand.org/learning_the_shell.php#contents](http://www.linuxcommand.org/learning_the_shell.php#contents)

---

### Post by wolfen69 on 2009-02-12
just put the file in your home directory and:
```
sudo dpkg -i name_of_file.deb
``` or just double click to install.

---

### Post by Bearly Able on 2009-02-17
Hi Guys,

Thanks for the help.  I followed your instructions and the drivers seemed to install just fine, but they're not appearing on the list of available drivers when I try to configure the printer.  I found a tip elsewhere that the drivers for another model will work, and it does seem to be printing OK at the moment, but I'd really like to use the correct drivers.  I haven't tried the scanner, but I suspect it may not work on the current configuration.  Any suggestions?

Thanks for the link, mc4100 - it's just what I was looking for.

Lesley

---

### Post by stchman on 2009-02-17
That printer is reported to work "Mostly" according to openprinting.org

[http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_Office_BX300F](http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_Office_BX300F)

Are you having problems printing at all?

---

### Post by Bearly Able on 2009-02-17
Hi stchman,

The system belongs to an elderly friend, who has never used a computer before, and was given this one.  Hence, I've not had much time to play about with the printer, or check the scanner.  Using the driver for Stylus CX3800, it prints mono text nicely, if very slowly, but I haven't tried it with colour or images.

Lesley

---

