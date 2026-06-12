---
title: "Sun Java6 Problem"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by Jinty on 2009-04-02
I am trying to install sun-java6-jdk as required by JMRI Decoderpro software.
As the jdk file and associated files did not download correctly, I tried
to install all the java6 files. The download stuck on java6-source and I had to force closure.
Now Synaptic Package Manager will not open, I get the following error message.
E:dpkg was interrupted you must manually run 'dpkg--configure-a' to correct problem.
E:Cache->open()failed.
I don't know what this means, what do I do?
Please help
Jinty

---

### Post by gandaran on 2009-04-02
just do what it says run in terminal 
> sudo dpkg --configure -a

---

### Post by philinux on 2009-04-02
Make sure there's no typo. As gandaran says but make sure the spaces are there.

```
sudo dpkg --configure -a
```

---

### Post by Jinty on 2009-04-02
Many thanks for quick replies. Have now got Package manager back.
Trying to start again to install Sun java6-jdk also installed bin and jre files.
However, not sure that it is correctly installed. All I can find is an icon to open java6 web start under apps-internet and one for sun java console under apps-system tools. 
What should I have as a launch icon?
Thanks Jinty

---

### Post by philinux on 2009-04-02
You only need these three.

sun-java6-bin
sun-java5-jre
sun-java6-plugin

The plugin is for the browser. You dont need web start or java console to be running.

---

### Post by Jinty on 2009-04-03
Once more many thanks for responses. Marking jdk for installation also installed bin and jre, should I install plugin?
The Java folder created so far only has -deployment which has folder-deployment properties.  Is this correct?
Jinty

---

### Post by gandaran on 2009-04-03
> should I install plugin?
yes, firefox needs it for web based java applets

---

