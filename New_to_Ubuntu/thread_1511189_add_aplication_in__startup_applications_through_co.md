---
title: "add aplication in  startup applications through commandline"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by anantshri on 2010-06-16
Hi All,

can anyone help me in finding a way by which i can add an application to automatically start everytime i login to my gnome session.

i guess it has to be something throught gconf-tool.

seems i am not able to find it have been searching for around 20 minutes.

Please help

Please do not provide graphical alternative.

---

### Post by cj.surrusco on 2010-06-16
Maybe you could try one of these alternatives. (I'm guessing you want to do it from the command line?)

[http://www.astahost.com/info.php/start-program-startup-options_t13846.html](http://www.astahost.com/info.php/start-program-startup-options_t13846.html)

---

### Post by anantshri on 2010-06-16
pardon my ignorance..


yes i need a solution based on CLI....


but this above method is for system bootup i am looking for something simmilar to startup applications gui tool in gnome environment. and would like my application to start only when gnome environment is running.

hope that clears the question.

If i remember it correctly this could be done by gconf or simmilar tool.

what i am exactly looking is a one line commnd which when executed  could set my application at startup


EDIT : looks like i found something

all i need to do is to place  file in ~/.config/autostart/

with following details

[Desktop Entry]
Type=Application
Exec=<file_to_be_executed_location>
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name=Name
Comment=Description

---

### Post by cj.surrusco on 2010-06-16
Sorry, my fault, I didn't even read the title thoroughly. 
> **anantshri said:**
> 

EDIT : looks like i found something

all i need to do is to place  file in ~/.config/autostart/

with following details

[Desktop Entry]
Type=Application
Exec=<file_to_be_executed_location>
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name=Name
Comment=Description
This should work, I just checked and it appears the the gui tool puts .desktop files in that folder for every program set to run at startup.

---

### Post by anantshri on 2010-06-16
well can you suggest a one liner application that can do such stuff.

or i need to write my own. I suppose i can do that using a simple shell script

---

