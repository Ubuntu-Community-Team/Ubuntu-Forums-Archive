---
title: "Trying to setup Subsonic..."
date: 2008-12-30
forum: New to Ubuntu
---

### Post by chris062689 on 2008-12-30
I recently came across this neat little guy:
[http://subsonic.sourceforge.net/](http://subsonic.sourceforge.net/)

And I'm trying to set it up for Ubuntu 8.10 64-bit.
I downloaded the files and placed them in my home directory, and there is a subsonic.sh they told me to run

--- Subsonic .sh ---
```

#!/bin/sh

# The directory where Subsonic will create files. Make sure it is writable.
SUBSONIC_HOME=/var/subsonic

# The port on which Subsonic will listen for incoming HTTP traffic.
SUBSONIC_PORT=8080

# The context path (i.e., the last part of the Subsonic URL).  Typically "/" or "/subsonic".
SUBSONIC_CONTEXT_PATH=/

# The memory limit (max Java heap size) in megabytes.
MAX_MEMORY=64


$JAVA_HOME/bin/java -Xmx${MAX_MEMORY}m  -Dsubsonic.home=${SUBSONIC_HOME} -Dsubsonic.port=${SUBSONIC_PORT} \
-Dsubsonic.contextPath=${SUBSONIC_CONTEXT_PATH} -jar subsonic-booter-jar-with-dependencies.jar

```

Now the problem is, when I try executing that, I get this:
```

chris@chris-desktop:~/Documents/Subsonic$ ./subsonic.sh
./subsonic.sh: 17: /bin/java: not found

```

I assume it has to do with this:
$JAVA_HOME/bin/java

But I don't know what JAVA_HOME is on a 64-bit system, any help?
EDIT: Yes I do have java6-bin and ia32-java6-bin installed.

---

### Post by Partyboi2 on 2008-12-30
in a terminal type
```
which java
```Then with the output eg ```
 /usr/bin/java
``` change the red part to the correct path eg.
$JAVA_HOME/usr/bin/java
```
#!/bin/sh

# The directory where Subsonic will create files. Make sure it is writable.
SUBSONIC_HOME=/var/subsonic

# The port on which Subsonic will listen for incoming HTTP traffic.
SUBSONIC_PORT=8080

# The context path (i.e., the last part of the Subsonic URL).  Typically "/" or "/subsonic".
SUBSONIC_CONTEXT_PATH=/

# The memory limit (max Java heap size) in megabytes.
MAX_MEMORY=64


$[COLOR=Red]JAVA_HOME/bin/java[/COLOR] -Xmx${MAX_MEMORY}m  -Dsubsonic.home=${SUBSONIC_HOME} -Dsubsonic.port=${SUBSONIC_PORT} \
-Dsubsonic.contextPath=${SUBSONIC_CONTEXT_PATH} -jar subsonic-booter-jar-with-dependencies.jar
```then save the change and then make sure that /var/subsonic directory is created
```
sudo mkdir /var/subsonic
```then run the script
```
sudo ./subsonic.sh
```

Edit: Then go to  [http://localhost]("http://localhost/").

---

