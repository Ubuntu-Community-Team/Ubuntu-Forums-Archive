---
title: "echo $JAVA_HOME from command line shows nothing"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by unagimiyagi on 2011-05-08
Hi,

I've spent all evening trying to get my JAVA_HOME correct.
I'm using the openJDK (not Sun's)

I have ubuntu 11.04

in my ~/.profile, I've added this at the end of what comes standard:

```

JAVA_HOME =/usr/lib/jvm/java-1.6.0-openjdk

export JAVA_HOME

PATH=$PATH:$JAVA_HOME/bin:~/Downloads/apache-tomcat-7.0.12/bin
export PATH

options thinkpad_acpi fan_control=1


```

When I reboot, echo $JAVA_HOME shows nothing, and nothing has been added to my PATH.  Any ideas why?

Thanks!

---

### Post by lloyd_b on 2011-05-08
Not sure if this is a typo or not - there's a space between JAVA_HOME and the =, which is *not* allowed for scripting```

JAVA_HOME =/usr/lib/jvm/java-1.6.0-openjdk
```should be```
JAVA_HOME=/usr/lib/jvm/java-1.6.0-openjdk
```

Try fixing this first, and see what happens...

Note that you do not have to reboot to check if the changes have taken effect - just log out and back in.  Also, if you make the changes to ~/.bashrc instead of ~/.profile, you can simply close the current terminal window and open a new one, and the changes should be reflected.

Lloyd B.

---

