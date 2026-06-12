---
title: "Problems Installing Grails on Ubuntu 10.04 TLS"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by madmiarde on 2011-03-23
New to Linux.

Trying to install Grails.

First installed Java:  sudo aptitude install...
     - java version "1.6.0_20"
       OpenJDK Runtime Environment (IcedTea6 1.9.7) (6b20-1.9.7-0ubuntu1~10.04.1)
       OpenJDK Client VM (build 19.0-b09, mixed mode, sharing)

Then installed Groovy: sudo aptitude install groovy
     - Groovy Version: 1.6.4 JVM: 1.6.0_20

Then downloaded Grails from the Grails site (in zip format, which is all I saw available):
     - I ran the following:  sudo unzip /home/miarde/Downloads/grails-1.3.7 -d /usr/share
     - If I try to locate grails, it says it was installed in /home/miarde/Grails/grails-1.3.7> I'm guessing it did not extract it to /usr/share which might be part of the problem.

I modified the /etc/bash file and it looks like the following:

[B]# # # Java
JAVA_HOME=/etc/java-6-openjdk
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH


# # # Groovy
GROOVY_HOME=/usr/share/groovy
PATH=$PATH:$GROOVY_HOME/bin
export PATH GROOVY_HOME


# # # Grails - 1st Try
#GRAILS_HOME=/usr/share/Grail
#PATH=$PATH:GRAILS_HOME/bin
#export PATH GRAILS_HOME

# # # Grails - 2nd Try
GRAILS_HOME=/home/miarde/Grails
PATH=$PATH:GRAILS_HOME/bin
export PATH GRAILS_HOME[/B]

After each edit to this file, I restarted Ubuntu.

Now the final step was to check if grails was installed.  The directions I followed said to type:  "Grail" in the terminal - got Grail command not found.  Then I tried "grail" in terminal - same result.  I finally tried "grails" in terminal and received:  

miarde@miarde:~$ grails
Welcome to Grails 1.3.7 - [http://grails.org/](http://grails.org/)
Licensed under Apache Standard License 2.0
Grails home is set to: /home/miarde/Grails/grails-1.3.7


So it looks as if it's installed properly, I guess I'll find out more.  Not sure why it didn't extract it to /usr/share so hopefully it works.  

Any thoughts as to what happened and if you think it will work?  I will be trying soon to write my first grails app.

Thanks

---

