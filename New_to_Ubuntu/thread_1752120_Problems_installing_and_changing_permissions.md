---
title: "Problems installing and changing permissions"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by Jrmurph3 on 2011-05-07
There is this application called SMS2PC that I use to remotely send and receive text messages from my mobile device.  The original download comes in a "linux.zip" folder because it was downloaded for linux use.  inside is a "SMS2PC.jar" file. I cannot open it because it says "The file '/home/john/.cache/.fr-2l2oA3/SMS2PC.jar' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit." 

I tried using sudo chmod 755 /home/john/.cache/.fr-212oA3/SMS2PC.jar which is to the file that it says isn't executable. I also tried using sudo chmod 755 /home/john/Downloads/linux.zip to allow executable permissions for the original .zip download and it still says "The file '/home/john/.cache/.fr-2l2oA3/SMS2PC.jar' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit."

I don't understand what I'm doing wrong. Someone please help.

---

### Post by rx007 on 2011-05-07
it's a jar file. you have to use java to execute it.

```

java -jar SMS2PC.jar

```

if you don't have java, install it from the ubuntu software center.

---

### Post by Jrmurph3 on 2011-05-07
> **rx007 said:**
> it's a jar file. you have to use java to execute it.

```

java -jar SMS2PC.jar

```if you don't have java, install it from the ubuntu software center.

Ok, I really appreciate that quick answer. I used your command and it says unable to  access jarfile SMS2PC.jar.

I do have java installed and I did extract the contents from the linux.zip folder to Downloads just to keep them in a relatively close area.

Any other suggestions? Thanks.

---

### Post by Jrmurph3 on 2011-05-07
I do believe I figured it out. I am very new to linux in general. 

I changed the directory in terminal then ran the command. It works.

Thanks for the help.

---

