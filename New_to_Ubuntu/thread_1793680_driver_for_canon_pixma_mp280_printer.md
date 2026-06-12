---
title: "driver for canon pixma mp280 printer"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by baird on 2011-06-29
[solved] Don't know how the printer connected to the driver

Following the suggestion of one of the earlier posts, I've downloaded cnijfilter-mp280- series-3.40-1deb.tar.gz from canon to file, archives and it shows on the desktop and in synaptic package manager. How do I get recognized by search and the printer.  Please, very simple and specific instructions.  My favorite interaction with an instructor is "spoon feed Me" when dealing with software code and/or commands.

Thank you very much.   baird

---

### Post by jtarin on 2011-06-29
> **baird said:**
> Following the suggestion of one of the earlier posts, I've downloaded cnijfilter-mp280- series-3.40-1deb.tar.gz from canon to file, archives and it shows on the desktop and in synaptic package manager. How do I get recognized by search and the printer.  Please, very simple and specific instructions.  My favorite interaction with an instructor is "spoon feed Me" when dealing with software code and/or commands.

Thank you very much.   baird[img]http://greenbabyguide.com/wp-content/uploads/2010/11/Baby-Playing-With-Wooden-SPoon-150x150.jpg[/img]   What earlier post?

---

### Post by baird on 2011-07-01
I think the poster's name is Mcgregor or something like that poted some time is 2010. I'd have to go back to my history to be sure. That's for a later time.  Sorry, I'm on a tight schedule right now.  Thanks for your interest baird

Correction: poster's name is vicshrike and post date is September 26th, 2010. baird

---

### Post by jtarin on 2011-07-01
Try this if you haven't.....extract the .deb from the .tgz file with a right-click and select "extract here" Open a terminal and change to the directory that the extracted file is in, then substituting your filename (cnijfilter-mp280- series-3.40-1deb) issue the command

Assuming you downloaded the file "cnijfilter-mp280- series-3.40-1deb.tar.gz", just extract it with a right-click and select "extract here". In the terminal, navigate to that folder:



```
cd Downloads
cd cnijfilter-mp280- series-3.40-1-driver(or whatever the extracted name is)
cd cnijfilter-mp280- series-3.40-1deb

```
Then install using the next line in the terminal at the present location:
```
sudo ./install.sh
```

Follow the onscreen prompts. The whole process took about 30 seconds.

---

