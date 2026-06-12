---
title: "Installing JDK offline"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by Dean_Grobler on 2011-06-02
Hi there,

I don't have internet access at home so I downloaded the JDK6 file from the oracle site for Linux. I unizped it to a folder and even got a "thank you for installing the JDK" html page automatically displayed to me in my browser.

When I tried to test the installation by doing **java -version**, it didn't pick up the JDK on my machine. I heard something about symlinks, I don't know what this is, or if it will work and how to do it. 

So basically, I have a folder now that contains the java bin folder and all the other files. Where do I now go from here to finish my installation?

PS-Ubuntu's Open-JDK is out of the question...

---

### Post by Mariane on 2011-06-02
Please type 

```

env

```

and check you have lines about CLASSPATH and JAVA_Home which point to the right directory. You should see something which looks like this: 

```

JAVA_HOME="/usr/local/Java/jdk1.5.0_07"
CLASSPATH="/usr/local/Java/jdk1.5.0_07/lib:."

```

BUT THE EXACT LOCATION DEPENDS UPON YOUR SETUP, don't just copy paste this in your /etc/environment file. 

Mariane

---

### Post by Dean_Grobler on 2011-06-02
Thanks Mariane, really appreciate it. If these enviromnent variables are not set on my system. How do you go about doing it? if say my jdk folder was located at /usr/local/bin/jdk1.6.0_25 for example?

---

### Post by Mariane on 2011-06-02
First also check with 

```

printenv

```

This gives you a longer list than

```

env

```

Then you can use the export command. For example

```

export DOG=Fjalla

```

Will give the value of "Fjalla" to the variable "DOG". This particular example is harmless and useless, I just happen to have a dog named Fjalla. In your case I would try: 

```

export JAVA_HOME=/usr/local/bin/jdk1.6.0_25
export CLASSPATH=/usr/local/bin/jdk1.6.0_25/lib:.

```

I don't guarantee this is going to work. The semi-colon separates entries, here for CLASSPATH you have your Java directory and '.' (The dot means whichever directory you are in when you type the "java" or "javac" commands). If you need several directories you write something like: 

```

export CLASSPATH=/usr/local/bin/jdk1.6.0_25/lib:/usr/bin/jdk1.6.0_25/:.

```

It won't hurt to include directories jdk does not actually use as long as the directories exist and that the syntax of the whole line is correct. 

Mariane

---

