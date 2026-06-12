---
title: "open office java install broke oo"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by caughran on 2009-10-23
Problems started when I tried a find in calc help, and it told me that java does that, but I have no java. It told me to go to the tools menu, java, and ??

It did find a java on the computer, and I did the stuff to let it use it. Restart required; did that, and discovered there seems to be no way to start it now. Opening a part of oo from the office menu seems to do nothing, except that open from template shows an "opening" box on the programs bar for a little while, until it disappears. From the command line (ooffice -calc %F), nothing. Opening document - nothing.

Reinstalled oo. No help. Command line acts like it's doing something, but nothing is visible. 

System monitor shows several instances of ooffice and oosplash. Ending them all and restarting just creates another invisible instance of each.

Java installed is 
/usr/lib/jvm/java-6-sun-1.6.0.16/jre/bin/java

Synaptic says the installed version is  
06-16-0ubuntu.9.04

open office version is 
1:3.0.1-9ubuntu3.1

---

### Post by caughran on 2009-10-23
A reboot fixed it. Funny how often that works.

---

