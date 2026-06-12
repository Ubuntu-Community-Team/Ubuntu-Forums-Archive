---
title: "Print sharing worked once, now it doesn't"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by Flatlander84 on 2010-04-21
My computer is running Ubuntu with a printer attached to it.  The printer is working fine from my computer.  I copied someone's explaination on samba installation and setup, whatever samba is, but I somehow worked my way through it and was able to print from my other windows based laptop to my printer connected to this computer.  I have since re-started my linux computer, and now I can't print from my windows computer.  I have tried re-installing it and now it won't even detect my printer from the windows computer.  Is there some thing I have to do to get it working every time I re-boot?

I also have an installation question.  I was trying to install the most recent version of Java Run time environment from the website.
[http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80](http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80)
I followed the instructions but when I go to check which version I have installed, it still says I have version 1.6 or something.  this is version 6 that I'm trying to install.

Do I need the linux RPM version?  What's the difference, I just picked the one that said Linux.  thanks for the help guys.

---

### Post by cariboo on 2010-04-23
Open up your favorite browser and type:

[http://localhost:631]("http://localhost:631")

this will open the cups interface, click the administration tab and make sure **Share printers connected to this system** is enabled, then click the change settings button, See screen shot. 

Next restart cups by pressing Alt-F2 and typing

```
gksu service cups restart
```

You should now be able to see the printer from your Windows computer

---

