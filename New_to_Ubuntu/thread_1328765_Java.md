---
title: "Java"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by qwertyuiop96 on 2009-11-16
How do install the java plugin?  I have open-jdk but Firefox says it needs additional plugins.  When I say to install the sun java plugin, it says sun-java6-plugin not found.  I searched for that in Synaptic, and nothing came up.  Help please?  I'm a java dev, so this is important...

---

### Post by desperado665 on 2009-11-16
search synaptic for ubuntu-restricted-extras

that will include the java plugin

---

### Post by MonoDeem on 2009-11-16
```
sudo apt-get update && sudo apt-get install sun-java6-jre sun-java6-plugin

```

---

### Post by qwertyuiop96 on 2009-11-16
Nothing turns up if I search ubuntu-restricted-extras.  I have no idea why.

---

### Post by qwertyuiop96 on 2009-11-16
If I do the terminal thing, I get

```

Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

```

---

### Post by MonoDeem on 2009-11-16
> **qwertyuiop96 said:**
> If I do the terminal thing, I get

```

Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

```

You need to enable Multiverse repositories. Follow [this guide]("https://help.ubuntu.com/community/Repositories/Ubuntu") and you should be fine.

---

### Post by qwertyuiop96 on 2009-11-16
> **MonoDeem said:**
> You need to enable Multiverse repositories. Follow [this guide]("https://help.ubuntu.com/community/Repositories/Ubuntu") and you should be fine.

Worked, but I wasn't sure what to hit when it came up w/ the license.  Enter and space didn't work, and I couldn't click so I excited.  I went to synaptic, and an install option came up, but is says another synaptic is running.  I rebooted, and had the same problem.  I think I did something when I killed the terminal process.  Now what?

---

### Post by Miljet on 2009-11-16
When you get to the point of accepting the license, hit your tab key. That will allow you to select the yes button.

Not sure about the synaptic already running. You might try running
```
sudo apt-get update && sudo apt-get upgrade
```
from the terminal.

---

### Post by qwertyuiop96 on 2009-11-16
Opened synaptic, and it informed me a package was broken and asked if I wanted to fix it.  I said yes, and then all was fixed.  I love Ubuntu.  ;-)

---

### Post by iruel on 2009-11-16
highly recommended you download from [http://java.sun.com](http://java.sun.com), it's make you can upgrade offline installation,this is step-by-step

1.after you has been download it, open terminal on same directory where the jdk installer saved, and then type like this **./jdk6-u17xxxx.bin** and agree with condition

2.you has been extracted the binary,and move as you wish directory, ie: **/opt/dev**
3.setting(create if not exist) **.profile** under you home directory
4.add this line
   export JAVA_HOME=/opt/dev/jdk6-u17
   export PATH=$PATH:$JAVA_HOME/bin
5.relogin(log off and login again) and then go to your java library (**/opt/dev/jdk6-u17/jre/lib/i386/client**) find **libnpjp2.so** and copy to your firefox-plugin folder, by default on **/usr/lib/firefox-3.5.3/plugins** or **/usr/lib/firefox-3.5/plugins** it's depends on your firefox version.

---

