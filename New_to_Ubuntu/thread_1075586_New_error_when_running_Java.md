---
title: "New error when running Java"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-02-20
I have run a certain Java program ([oogalleryimport]("http://oogalleryimport.sourceforge.net/")) many times before.

Suddenly, it now gives an error:
```
com.sun.star.lib.loader.Loader::getCustomLoader: cannot add UNO jar files: java.lang.ClassNotFoundException: com.sun.star.comp.helper.UnoInfo
Exception in thread "main" java.lang.NoClassDefFoundError: com/sun/star/uno/Exception
        at java.lang.Class.getDeclaredMethods0(Native Method)
        at java.lang.Class.privateGetDeclaredMethods(Class.java:2427)
        at java.lang.Class.getMethod0(Class.java:2670)
        at java.lang.Class.getMethod(Class.java:1603)
        at com.sun.star.lib.loader.Loader.main(Loader.java:168)
Caused by: java.lang.ClassNotFoundException: com.sun.star.uno.Exception
        at com.sun.star.lib.loader.Loader$CustomURLClassLoader.findClass(Loader.java:287)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at com.sun.star.lib.loader.Loader$CustomURLClassLoader.loadClass(Loader.java:298)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
        ... 5 more
```I am at a total loss as to even begin looking for how to solve this. I don't know what the error means.

I've not changed the program or the method of running it at all.

Does anyone know where I can start interpreting this error or, better, how I can get the program to run again?

I'm running Hardy 8.04.

Thank you.

---

### Post by tarps87 on 2009-03-12
You might want to try downloading the latest version of oogalleryimport and check you are using sun's java. This can be done using ```
java --version
```
This should install the latest version of sun's java runtime envorment
```
sudo apt-get install sun-java6-jre
```

Note: It is advised to use descriptive tiles, that way members browsing the forum will know if they can help without looking.

---

### Post by Paddy Landau on 2009-03-12
Thanks for the advice. I've changed the title of the first post to make it more descriptive.

I have the latest version of oogallery, but I downloaded again just in case.

java -version gives 1.6.0_07, the latest version according to Synaptic Package Manager. Just in case, I reinstalled through Synaptic Package Manager.

Sadly, I still get the same error.

Looking on the official Java website, I see that the latest version is 1.6u12 (Synaptic holds only update 7).

I'd like to [download the latest version]("http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com"), in case that helps, but I'm confused; do I download the Linux RPM or the other Linux one? Once downloaded, I don't know from the instructions exactly where to do the installation. I presume that I must first uninstall the Synaptic version?

Any ideas? Or will installing a later version of Java make no difference? Would the problem have been caused by the most recent updates to OpenOffice (I have version 3.0.1)?

TIA

---

### Post by tarps87 on 2009-03-12
The difference between java6 update 7 and update 11  should not effect oogalleryimport. Looking at the exception it is linked to open office and may well be a result of updating to OpenOffice 3.0.1
I currently don't have access to a Ubuntu box but if you let me know how you installed open office I will try to recreate it when I get a chance.


If you want to install the latest jre, you can download it fron Sun's site:
[http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)
If you select Linux and then the .bin download
e.g.
jre-6u12-linux-i586.bin

Now these commands to install java
```
sudo chmod a+x jre-6u12-linux-i586.bin
sudo ./jre-6u12-linux-i586.bin
```
And this one to set which version to use
```
sudo update-alternatives --config java
```

Thanks for changing the title, I will try to get back soon

---

### Post by Paddy Landau on 2009-03-12
> **tarps87 said:**
> ... these commands to install java...
Thanks for that. If Java isn't the problem, then I'll stick with Synaptic Manager and stay with the older version. Otherwise I'll have to manually update Java every new release.

> **tarps87 said:**
> ... let me know how you installed open office...
I forget now. I might have added the OO repository to Synaptic Package Manager:
[http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main

But, because of problems with that repository, I instead probably downloaded the DEB package from the OO site:
[http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US)

Thanks again for your help.

---

### Post by tarps87 on 2009-03-13
I managed to recreate the problem using java6 update 12, open office 3.1.0 and the latest version of ooarchiveimport. It looks like there are some incompatibility issues. I have added the jar file containing the missing class but am now getting null pointer exceptions for within the oogalleryimport code.
It looks like the current solution will be to use the previous version of open office instead of or along side 3.1.0
I will post back if I find another solution
Sorry I can't be of more help

---

### Post by Paddy Landau on 2009-03-13
Thank you for taking the trouble to test this.

I booted into Windows, and it has exactly the same problem with OO version 3.

So I'm sure that you're right.

I don't want to revert my version of OO, so I'll have to boot into Windows whenever I want to convert any clip art.

I've raised a bug report for this:
[]("https://sourceforge.net/tracker/index.php?func=detail&aid=2686266&group_id=135292&atid=732629")[https://sourceforge.net/tracker2/index.php?func=detail&aid=2686266&group_id=135292&atid=732629](https://sourceforge.net/tracker2/index.php?func=detail&aid=2686266&group_id=135292&atid=732629)

I hope that the owner is watching it!

---

