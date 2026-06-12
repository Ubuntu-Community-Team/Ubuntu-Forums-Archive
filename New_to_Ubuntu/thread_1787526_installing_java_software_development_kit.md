---
title: "installing java software development kit"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by gr8ansh4u on 2011-06-21
hey everyone... i'm using ubuntu for the first time...i wana install java sdk...i've downloaded it and its in .bin extension...hw to install it...  please help....

---

### Post by r-senior on 2011-06-21
Don't install the .bin file. Use the repositories.

Go into Synaptic Package Manager, then Settings -> Repositories -> Other Software. Tick "Canonical Partners".

Synaptic will ask you to update, then search for 'sun-java'. Install the JDK and any dependencies.

Then, to switch to Sun Java:

```

sudo update-java-alternatives -s java-6-sun

```

Test it's installed with:

```

javac -version
java -version

```

The above are instructions to install Sun Java. You could try OpenJDK which works for most things. In this case, just search for 'openjdk' in Synaptic and install the JDK. If you are doing this, you don't need to update alternatives as shown above.

---

### Post by gr8ansh4u on 2011-06-21
when i click on synaptic manager, it shows following message

"     **Unable to get exclusive lock**

This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first. "

hw to close that application??

---

### Post by computerandu on 2011-06-21
> **gr8ansh4u said:**
> hey everyone... i'm using ubuntu for the first time...i wana install java sdk...i've downloaded it and its in .bin extension...hw to install it...  please help....

use ./filename.bin to run install applications from bin files...

---

### Post by gr8ansh4u on 2011-06-21
any other way to install it??

---

### Post by arno48 on 2011-06-21
I have a similar problem.
I installed OpenJDK but it does not succeed to work with some websites.
Some questions:
1) I have to remove OpenJDL before installing Sun Java?
 2) In Synaptic  I read several alternatives, the ones nearer to my needs seem the following:
    Sun Java (TM) Runtime Environment (JRE) 6 (architecture dependent files) sun-java6-bin
                                                         or
    Sun Java (TM) Runtime Environment (JRE) 6 (architecture independent files) sun-java6-ire
                                                        or
   Sun Java (TM) Plug-in, Java SE 6      sun-java6-plugin

but there are others.

Which one  have I to choose?

3) I do not want to damage my Ubuntu 11.04 with Sun Virtual machines, therefore would it better
  to work with those websites using Windows installed computers?

Thanks for your time

---

### Post by gr8ansh4u on 2011-06-21
> **r-senior said:**
> Don't install the .bin file. Use the repositories.

Go into Synaptic Package Manager, then Settings -> Repositories -> Other Software. Tick "Canonical Partners".

Synaptic will ask you to update, then search for 'sun-java'. Install the JDK and any dependencies.

Then, to switch to Sun Java:

```

sudo update-java-alternatives -s java-6-sun

```

Test it's installed with:

```

javac -version
java -version

```

The above are instructions to install Sun Java. You could try OpenJDK which works for most things. In this case, just search for 'openjdk' in Synaptic and install the JDK. If you are doing this, you don't need to update alternatives as shown above.







thank you r-senior....it worked :) :) :) :)....

---

### Post by r-senior on 2011-06-21
> **arno48 said:**
> Some questions:
1) I have to remove OpenJDL before installing Sun Java?

No. The update-java-alternatives script will switch between them. So to switch to Sun Java. it's "sudo update-java-alternatives -s java-6-sun". To switch back, it's "sudo update-java-alternatives -s java-6-openjdk".

> 
 2) In Synaptic  I read several alternatives, the ones nearer to my needs seem the following:
    Sun Java (TM) Runtime Environment (JRE) 6 (architecture dependent files) sun-java6-bin
                                                         or
    Sun Java (TM) Runtime Environment (JRE) 6 (architecture independent files) sun-java6-ire
                                                        or
   Sun Java (TM) Plug-in, Java SE 6      sun-java6-plugin

but there are others.

Which one  have I to choose?

Some packages are dependent on others. Generally speaking, if you want to do Java development, install the one that ends 'jdk' and let it figure out the dependencies. If you don't want to write Java programs, don't install the JDK.

If you just want the plugin for running applets in a browser, the Sun plugin is sun-java6-plugin. The Open JDK plugin is 'icedtea-plugin'.

> 
3) I do not want to damage my Ubuntu 11.04 with Sun Virtual machines, therefore would it better
  to work with those websites using Windows installed computers?

Installing Java will not damage Ubuntu.

---

### Post by arno48 on 2011-06-21
> **r-senior said:**
> No. The update-java-alternatives script will switch between them. So to switch to Sun Java. it's "sudo update-java-alternatives -s java-6-sun". To switch back, it's "sudo update-java-alternatives -s java-6-openjdk".


Some packages are dependent on others. Generally speaking, if you want to do Java development, install the one that ends 'jdk' and let it figure out the dependencies. If you don't want to write Java programs, don't install the JDK.

If you just want the plugin for running applets in a browser, the Sun plugin is sun-java6-plugin. The Open JDK plugin is 'icedtea-plugin'.


Installing Java will not damage Ubuntu.

Thank you very much

---

