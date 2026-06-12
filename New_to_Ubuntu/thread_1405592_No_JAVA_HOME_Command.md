---
title: "No JAVA_HOME Command"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by dchester11 on 2010-02-12
I am new to Linux and am trying to set up my dev environment.  I am following the directions in this thread [http://ubuntuforums.org/showthread.php?t=1386751&highlight=jdk-6u18-linux-i586](http://ubuntuforums.org/showthread.php?t=1386751&highlight=jdk-6u18-linux-i586).  I have not installed any other packages in my installation.

When I try to set my JAVA_HOME variable I get the following error:

```

dustin@dustin-ubuntu-laptop:/usr/local$ JAVA_HOME /usr/local/bin/jdk1.6.0_18/
JAVA_HOME: command not found

```

Also, will installing Java in this location make it available to all users?

Thanks everyone!

---

### Post by Cheezespread on 2010-02-12
I specifically no nothing of the variable to be honest.But if you try to echo its contents , you can see where it is pointing to at this moment.
```

echo $JAVA_HOME
```

And if the required path is not present in the echoed result , you can very well add it .

```
export JAVA_HOME =$JAVA_HOME:/usr/local/bin/jdk1.6.0_18/
```

**the PATH variable is set in the /etc/environment file as I read someplace. I am not sure of this. Will adding the info about JAVA_HOME in the same make it available to all users? **. Hope some one clarifies this.

---

### Post by dchester11 on 2010-02-14
That worked!  Thank you.  Starting at square 1 with an OS... the simple stuff takes all day :)

---

