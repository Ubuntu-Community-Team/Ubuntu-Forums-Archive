---
title: "Help with problem installing java runtime environment"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by francy.casalino on 2011-03-09
Hi,

I am trying to install Squirrel SQL client, and one of the requirement is of course Java runtime environment, so I was first installing this following the instruction on this great link ([http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html)), but of course my desktop freezes and when I try to re-install using the command line "sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts", I get an error message saying:
"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."

But I do not know how to do this...I tried looking online for un-installing and re-installing but I cannot find information...

When I try to write that command, this error message comes up:
######################3
The following packages have unmet dependencies:
 sun-java6-jre : Depends: sun-java6-bin (>= 6.21dlj-0ubuntu1~maverick1~ppa1) but it is not going to be installed or
                          ia32-sun-java6-bin (>= 6.21dlj-0ubuntu1~maverick1~ppa1) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
 sun-java6-plugin : Depends: sun-java6-bin (>= 6.21dlj-0ubuntu1~maverick1~ppa1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
#####################

Then when I try to run the 'apt-get -f install
I get this error:
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


Please help me...

Thank you very much.

---

### Post by zenwalker on 2011-03-09
You should be a root user to do all this or else use sudo command with those commands.

---

