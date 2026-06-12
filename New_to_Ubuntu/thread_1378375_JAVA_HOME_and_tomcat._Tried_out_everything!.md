---
title: "JAVA_HOME and tomcat. Tried out everything!"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by BioVirtual on 2010-01-11
I configured JAVA_HOME in ~/.bashrc and  ~/.profile as below:


```


export JAVA_HOME=/usr/lib/jdk1.6.0_17
export PATH=$PATH:$JAVA_HOME/bin:$PATH


```

when I type :
```
 $ echo $JAVA_HOME 
```


 I get: 

```

/usr/lib/jdk1.6.0_17

```

but I cannot install tomcat. When I run startup.sh I get below error:

The JAVA_HOME environment variable is not defined
This environment variable is needed to run this program


I read lots of articles. there is nothing more than what I did. Is it possible that tomcat doesn't understand the new version of java?!

---

### Post by tom.swartz07 on 2010-01-11
> **BioVirtual said:**
> I configured JAVA_HOME in ~/.bashrc and  ~/.profile as below:


I read lots of articles. there is nothing more than what I did. Is it possible that tomcat doesn't understand the new version of java?!

EDIT::

I remembered that I posted to your other question a few days ago.
Hold on while I look up the problem a little more.

---

### Post by tom.swartz07 on 2010-01-11
What version of tomcat are you trying to install?
This guide: [http://www.heidisoft.com/blogs/installing-tomcat-6-ubuntu-910](http://www.heidisoft.com/blogs/installing-tomcat-6-ubuntu-910) says that Tomcat 6 works fine with almost no config.

Some other forums suggest that you turn off tomcat security until you get it running. [http://www.activeobjects.no/subsonic/forum/viewtopic.php?t=2340](http://www.activeobjects.no/subsonic/forum/viewtopic.php?t=2340)

Hopefully these help.
If you followed the guide presented in your other post, there should be no problems with Java- it might just be a few bumps with your tomcat installation.

---

### Post by Mighty_Joe on 2010-01-11
I see in your other post you clarified what my questions were.

---

### Post by Hospadar on 2010-01-11
Why not install it from the repositories?
```
sudo apt-get install tomcat6
```If need manual installation for some reason, you might try adding those export statements to the actual install script to make sure they get defined there.  Sometimes install and config scripts will have blanks in them for you to define variables like that (though I don't know about tomcat specifically), so also check the actuall install script and see if there is some placeholder assignment for those variables.
You might see something like```
JAVA_HOME=
```

---

### Post by BioVirtual on 2010-01-11
It's tomcat 5.0.24 coming with openlaszlo. 

[http://www.openlaszlo.org/lps4/docs/installation/install-instructions.html](http://www.openlaszlo.org/lps4/docs/installation/install-instructions.html)

---

### Post by BioVirtual on 2010-01-11
Well, this is a file called setclasspath.sh . I found below in it if it can help:
```

# -----------------------------------------------------------------------------
#  Set CLASSPATH and Java options
#
#  $Id: setclasspath.sh,v 1.7 2004/02/12 21:38:56 markt Exp $
# -----------------------------------------------------------------------------

# Make sure prerequisite environment variables are set
if [ -z "$JAVA_HOME" ]; then
  echo "The JAVA_HOME environment variable is not defined"
  echo "This environment variable is needed to run this program"
  exit 1
fi
if $os400; then
  if [ ! -r "$JAVA_HOME"/bin/java -o ! -r "$JAVA_HOME"/bin/javac ]; then
    echo "The JAVA_HOME environment variable is not defined correctly"
    echo "This environment variable is needed to run this program"
    exit 1
  fi
else
  if [ ! -r "$JAVA_HOME"/bin/java -o ! -r "$JAVA_HOME"/bin/jdb -o ! -r "$JAVA_HOME"/bin/javac ]; then
    echo "The JAVA_HOME environment variable is not defined correctly"
    echo "This environment variable is needed to run this program"
    echo "NB: JAVA_HOME should point to a JDK not a JRE"
    exit 1
  fi
fi
if [ -z "$BASEDIR" ]; then
  echo "The BASEDIR environment variable is not defined"
  echo "This environment variable is needed to run this program"
  exit 1
fi
if [ ! -r "$BASEDIR"/bin/setclasspath.sh ]; then
  echo "The BASEDIR environment variable is not defined correctly"
  echo "This environment variable is needed to run this program"
  exit 1
fi

# Set the default -Djava.endorsed.dirs argument
JAVA_ENDORSED_DIRS="$BASEDIR"/lib

# Set standard CLASSPATH
CLASSPATH="$JAVA_HOME"/lib/tools.jar

# OSX hack to CLASSPATH
JIKESPATH=
if [ `uname -s` = "Darwin" ]; then
  OSXHACK="/System/Library/Frameworks/JavaVM.framework/Versions/CurrentJDK/Classes"
  if [ -d "$OSXHACK" ]; then
    for i in "$OSXHACK"/*.jar; do
      JIKESPATH="$JIKESPATH":"$i"
    done
  fi
fi

# Set standard commands for invoking Java.
_RUNJAVA="$JAVA_HOME"/bin/java
if [ $os400 = false ]; then
  _RUNJDB="$JAVA_HOME"/bin/jdb
fi
_RUNJAVAC="$JAVA_HOME"/bin/javac

```

---

### Post by einan on 2010-01-11
why don't you try giving 755 to all *.sh under /conf

I had this problem before..

---

### Post by reconditedave on 2010-01-12
I came here to post this exact problem.

I exported my JAVA_HOME as you are supposed to:
[FONT=Courier New]dave@Cocytus:~$ export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.15/
dave@Cocytus:~$ echo $JAVA_HOME
/usr/lib/jvm/java-6-sun-1.6.0.15/[/FONT]

I even tried (as per other forum posts) piping it to my /etc/environment
[FONT=Courier New]dave@Cocytus:~$ more /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.15/[/FONT]

When I try to run tomcat, you have to run as root i.e. 
[FONT=Courier New]dave@Cocytus:~$ [/FONT][FONT=Courier New]sudo startup.sh[/FONT]

BUT tomcat complained about my JAVA_HOME every time.

The problem is, when I sudo to root the JAVA_HOME is not set:
[FONT=Courier New]dave@Cocytus:~$ echo $JAVA_HOME
/usr/lib/jvm/java-6-sun-1.6.0.15/
dave@Cocytus:~$ sudo -s
root@Cocytus:~# echo $JAVA_HOME

root@Cocytus:~# 

[/FONT]I have to explicitly sudo to root, THEN set $JAVA_HOME otherwise it will not work.

My questions are:
1) How can I set the JAVA_HOME variable for root (without [FONT=Courier New]sudo -s[/FONT])
2) How can I set tomcat to start automatically when I boot my server?

---

### Post by reconditedave on 2010-01-14
I got it working based on instructions I found here:
[http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/](http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/)

I created a file /etc/init.d/openlaszlo
```
    # OpenLaszlo auto-start

    export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.15

    case $1 in
    start)
            sh /usr/local/lps-4.6.1/Server/tomcat-5.0.24/bin/startup.sh
            ;;
    stop)  
            sh /usr/local/lps-4.6.1/Server/tomcat-5.0.24/bin/shutdown.sh
            ;;
    restart)
            sh /usr/local/lps-4.6.1/Server/tomcat-5.0.24/bin/shutdown.sh
            sh /usr/local/lps-4.6.1/Server/tomcat-5.0.24/bin/startup.sh
            ;;
    esac  
    exit 0
```I am not sure why I had to do this, but I then added these two symbolic links:
(For some reason I had to move into the directories, otherwise it would not create the links properly)
```
cd /etc/rc1.d/
sudo ln -s /etc/init.d/openlaszlo ./K99openlaszlo
cd /etc/rc2.d/
sudo ln -s /etc/init.d/openlaszlo ./S99openlaszlo
```

---

