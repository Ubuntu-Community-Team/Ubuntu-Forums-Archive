---
title: "Problems Adding Repositories"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2010-01-24
I am having some problems re-adding a repository I accidentally. I see from [this website]("https://help.ubuntu.com/community/Repositories/CommandLine") that these type of commands use "deb". However, each time I use "deb" my machine gives me this: ```
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
deb: command not found
```
Is there a way of getting over this?

Thanks for your time,
RedStarYellowSun

---

### Post by Thomas Garman on 2010-01-24
Whatever you are trying to get from deb that way it not working.  Try this in your terminal:

gksu gedit /etc/apt/sources.list

that will create a text file and then at the end of that file you add your deb line and save the file.  For example you might add 

deb http:[www.geekconnection.org/remastersys/repository](www.geekconnection.org/remastersys/repository) ubuntu/

to the end of your text file and save and then you will be able to type in your terminal

sudo apt-get update

and you will find that when you type

sudo apt-get install remastersys

that package will install like you are wanting it to.  Of course, in this example I used "remastersys" but you would put in the package you are trying to install in all of the relevant places.

---

### Post by gnometorule on 2010-01-24
It's much easier if you go to

System -> Administration -> Software Sources,

then enable what you would like. If it was a 3rd party source, you'd go to 

Other Software, click 'add', 

then paste in the URL that the site you want to download from tells you to use. If it was the universe or so repository, just check what you need on the tab 'Ubuntu Sortware'.

You can manually edit the sources.list file too (as sudo), as described on the page you link. However, this probably takes a little longer. Also, have another careful read of the description of that page which, I think, is pretty good. You wouldnl't simply type 'deb' at the command line - that's just indicating a file format which needs to go with further statements. Just use the graphical interface above instead.

---

### Post by RedStarYellowSun on 2010-01-25
Thanks for the replies!
It worked.

Take care,
RedStarYellowSun

---

