---
title: "Tomcat help needed"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by mash.ky on 2009-02-23
i'm using ubuntu 8.10 and hav installed tomcat 5.5.

when i try 
```
sudo -s /usr/share/tomcat5.5/bin/startup.sh
``` 

it gives 
```
Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program

```

help me!

ps: i'm not good with environment variables.

---

### Post by Nepherte on 2009-02-23
See what the values of the variables are:
```
echo $JAVA_HOME
echo $JRE_HOME
```

If none of the are set, you can do it yourself:
```
export JAVA_HOME=/path/to/java
```

The problem is of course that you run the command with sudo. I thought the -s switch uses the current shell variables and -i simulates a login before eecuting the command. So you should be safe with the -s option.

---

### Post by mash.ky on 2009-02-23
thanx neph i did those changes before. after ya suggestion i used sudo su and then used ```
/usr/share/tomcat5.5/bin/startup.sh
```

now it's working fine i think. the output is```
Using CATALINA_BASE:   /usr/share/tomcat5.5
Using CATALINA_HOME:   /usr/share/tomcat5.5
Using CATALINA_TMPDIR: /usr/share/tomcat5.5/temp
Using JRE_HOME:       /usr/lib/jvm/java-1.5.0-sun-1.5.0.17/
```

it seems working properly rite?

---

