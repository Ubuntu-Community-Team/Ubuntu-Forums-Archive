---
title: "Where to install java"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by paul88 on 2010-11-26
I have downloaded the file j2sdkee-1_3_1-linux.tar.gz

Where do I extract the file to and how do i go about setting the classpath for this.

Thanks

---

### Post by napoleon3665 on 2010-11-26
you need to extract the file first...

---

### Post by paul88 on 2010-11-26
Thanks for your reply

Can I just extract the file to anywhere?

---

### Post by napoleon3665 on 2010-11-26
yeah, you can extract it to the desktop for example and then run it and it should install.

---

### Post by paul88 on 2010-11-26
Which file do I run as there is no .bin but there are a few .sh, but no obvious installer?

---

### Post by ramjet_1953 on 2010-11-27
Hi, Paul!

The easiest way is to follow the instructions in this link:

[http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html)

This will place it in the synaptic repository for you and then you just install it from Synaptic.

Regards,
Roger :D

---

### Post by paul88 on 2010-11-27
Thanks for your reply.

I'm not trying to install the jre.

I am trying to install the EE SDK as when running a java program i get the following:

```

javax.naming.NoInitialContextException: Cannot instantiate class: com.sun.jndi.fscontext.RefFSContextFactory [Root exception is java.lang.ClassNotFoundException: com.sun.jndi.fscontext.RefFSContextFactory]


```

Thanks

---

### Post by lykeion on 2010-11-27
Hi paul88
I think you are trying to download the wrong file. The one you are missing is the JNDI File System Service Provider.
[LIST=1]
[*]Go to Oracle JNDI downloads: [http://java.sun.com/products/jndi/downloads/index.html](http://java.sun.com/products/jndi/downloads/index.html).
[*]Click the download link for JNDI 1.2.1 & More.
[*]Download File System Service Provider, 1.2 Beta 3.
[*]Extract the zip archive and add the jars in the lib subfolder to your java project.
[/LIST]

---

### Post by paul88 on 2010-11-27
Thanks for the Link. I have downloaded it a put in in the lib folder.
So it now looks like

/Lookup.class
/lib/fscontext.jar
/lib/providerutil.jar

I hope that is right.

I have also included them in the CLASSPATH
```

paul@paul-laptop:~/Documents/eprogramming/week5$ echo $CLASSPATH 
/home/paul/apache-tomcat-6.0.26/lib/servlet-api.jar:/home/paul/apache-tomcat-6.0.26/lib/jsp-api.jar:/home/paul/apache-tomcat-6.0.26/lib/mysql-connector-java-5.1.12-bin.jar:/home/paul/Documents/eprogramming/fscontext.jar:./lib/fscontext.jar:/home/paul/Documents/eprogramming/week5/lib/:/home/paul/Documents/eprogramming/week5/lib/fscontext.jar:/home/paul/Documents/eprogramming/week5/lib/providerutil.jar


```


But when i run the program i get the following


```

paul@paul-laptop:~/Documents/eprogramming/week5$ java -cp . Lookup /tmp/
javax.naming.NoInitialContextException: Cannot instantiate class: com.sun.jndi.fscontext.RefFSContextFactory [Root exception is java.lang.ClassNotFoundException: com.sun.jndi.fscontext.RefFSContextFactory]


```


This is my java file:

```

import javax.naming.Context;
import javax.naming.InitialContext;
import javax.naming.NamingException;
import java.util.*;

public class Lookup{

    public static void main(String[] args){
        
        if(args.length != 1){
            System.out.println("You have not entered anything");
            System.exit(-1);
        }
        String name = args[0];
        Hashtable env = new Hashtable(11);
        env.put(Context.INITIAL_CONTEXT_FACTORY, "com.sun.jndi.fscontext.RefFSContextFactory");
        try{
            Context ctx = new InitialContext(env);
        
            Object obj = ctx.lookup(name);
            System.out.println(name +" is bound to " + obj);

            ctx.close();
        }catch(Exception e){System.out.println(e);}
    }

}


```

Thanks

---

### Post by lykeion on 2010-11-27
I take you're not using an IDE since you are trying to run from command-line. Otherwise the solution might be different.

Try to append the CLASSPATH variable to the -cp parameter, like this:```
java -cp .:$CLASSPATH Lookup /tmp/
```
Note #1
Normally you should not set the CLASSPATH variable. If you leave it unset, Java will look in the current directory to find classes.

Note #2
By using the -cp parameter the CLASSPATH variable will be ignored. It's only read when NOT using this parameter. It's also ignored when using an IDE like Eclipse/IntelliJ/NetBeans.

---

### Post by paul88 on 2010-11-27
Thank you for your help, it now works. I have spent hours trying to work that out.

Just one question, why is is that i seem to be forced to use the -cp part?

```

paul@paul-laptop:~/Documents/eprogramming/week5$ java Lookup /tmp/Exception in thread "main" java.lang.NoClassDefFoundError: Lookup
Caused by: java.lang.ClassNotFoundException: Lookup
    at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
Could not find the main class: Lookup.  Program will exit.


```

---

### Post by paul88 on 2010-11-27
I didn't have the . dot in my classpath



Fixed Now Thank you for your help

---

### Post by lykeion on 2010-11-28
Glad to be of help. Please tag this thread as SOLVED to let others find solutions easily.

---

