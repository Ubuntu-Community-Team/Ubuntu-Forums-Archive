---
title: "Java scanner"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by crazyclown on 2009-04-04
I did a search and found [http://ubuntuforums.org/showthread.php?t=727951](http://ubuntuforums.org/showthread.php?t=727951).  I followed the instructuoins in this thread and I am still getting the import java.util.Scanner cannot be resolved.  I know the program works I used Textpad and can compile my program just fine and used the javac and java commands to run from a terminal and it does just fine.

Any other suggestions.  Thanks.

---

### Post by Sorivenul on 2009-04-17
> **crazyclown said:**
> I did a search and found [http://ubuntuforums.org/showthread.php?t=727951](http://ubuntuforums.org/showthread.php?t=727951).  I followed the instructuoins in this thread and I am still getting the import java.util.Scanner cannot be resolved.  I know the program works I used Textpad and can compile my program just fine and used the javac and java commands to run from a terminal and it does just fine.

Any other suggestions.  Thanks.
1.) What version of Java JDK are you using? Sun or OpenJDK (or GNU...)? Did you install it manually after downloading the installer or did you use a version available in the repositories? 
2.) Did you close the import statement?
[PHP]import java.util.Scanner;[/PHP]
3.) If it works fine from a text editor and commandline combination, what exactly was giving the error? Eclipse like the post you linked to? NetBeans?

---

### Post by James_Lochhead on 2009-04-17
I have had this problem as well. It seems to be because the version of the JRE that Eclipse was using was too old to use scanner. Try installing a newer version and using:

```

sudo update-alternatives --config java

```

And choosing the newer version.

There is a new version of the sun JRE in Jaunty. If you do not want to upgrade you can simply download the Jaunty debs or use the link in my sig for manual installation.

If that doesn't work get the new version of eclipse (manual download). I think someone is doing alternative debs on launchpad as well though (PPAs are old even in Jaunty). That should fix the problem.

---

