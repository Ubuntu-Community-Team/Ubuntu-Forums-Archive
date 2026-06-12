---
title: "Azureus"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by qdjorge on 2007-10-31
Hi, when i've azureus on U 7.04 it's well but since i was installed U 7.10 azureus shut down ... what can i do? thnx

---

### Post by Perkins on 2007-10-31
If you want a meaningful answer, we're going to need more information.  Error messages?  What does the console output look like?  

Start by collecting these things, then if the cause of the problem doesn't jump out and bite you, look at the Azureus web site (If it's a common problem, they'll probably have a way to fix it) and then come back here with either the solution, or the additional information you've collected and we'll be able to do something for you with a bit of luck.

LMP

P.S.  As with any operating system, upgrades change how things work...  Have you tried completely uninstalling and reinstalling the program?  Be sure you remove the configuration files.  Nine times out of ten that fixes this kind of problem.

---

### Post by teaone on 2007-11-01
This probably related to path where JAVA was installed.
To make sure the path is correct, look into directory where bin directory was installed, usually it's in /usr/java/<java version>/bin.

You may correct the path in azureus bash script (/usr/local/bin/azureus) in line:
JAVA_PROGRAM_DIR="/usr/java/jre1.6.0_02/bin/"

Save the script and try launch Azureus again.

Hope this help.

---

### Post by BennBuntu on 2007-11-01
I found Azurueus never ran smoothly. Never shut down cleanly, slowed my system etc..

I switched to deluge, not as fully featured but being gtk based has less problems.
Transmission also seems good though even more basic. both in repos.

---

