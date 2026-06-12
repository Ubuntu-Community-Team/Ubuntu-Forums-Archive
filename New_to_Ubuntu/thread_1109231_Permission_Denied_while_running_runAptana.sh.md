---
title: "Permission Denied while running runAptana.sh"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by AlexanderSupertramp on 2009-03-28
Hi guys.

I am trying to install Aptana Studio on Intrepid. It is based on Eclipse, so a Java program.

I have followed steps given here: 

[http://maketecheasier.com/install-aptana-studio-in-ubuntu-intrepid/2009/03/23](http://maketecheasier.com/install-aptana-studio-in-ubuntu-intrepid/2009/03/23)

But running running the script: runAptana.sh does nothing in GUI. 

Even with sudo in terminal, I get "permission denied" error.

Here is the file content (runAptana.sh):

#!/bin/bash
export MOZILLA_FIVE_HOME=/usr/lib/xulrunner
/home/neo/aptana  #filepath to Aptana folder

Here is the output on terminal:
runAptana.sh: 3: /home/neo/aptana: Permission denied


I have marked file as executable.

Thanks for your time.

---

### Post by mgranet on 2009-03-28
Are you running it as root? If not, ```
sudo *command*
```

---

### Post by AlexanderSupertramp on 2009-03-28
I tried it with sudo, same error.

For tesing, I created another test script there, run.sh, as simple as: gedit.

I can run it, and gedit opens.

The problem is with runAptana.sh only.

---

### Post by mgranet on 2009-03-28
> **AlexanderSupertramp said:**
> I tried it with sudo, same error.

For tesing, I created another test script there, run.sh, as simple as: gedit.

I can run it, and gedit opens.

The problem is with runAptana.sh only.

Just to be sure, the command you are running is:
```
sudo sh runAptana.sh
``` Correct?

---

### Post by AlexanderSupertramp on 2009-03-28
yes. :)

---

### Post by mgranet on 2009-03-28
Hrm. You might try
```
sudo chmod 777 runAptana.sh
``` Then repeat the sudo sh runAptana.sh bit.

---

### Post by AlexanderSupertramp on 2009-03-28
thanks a lot for your time mgranet, I got the issue.

Please do not get furious, :(....

the path "/home/neo/aptana", it should have been "/home/neo/aptana/AptanaStudio", pointing to executable. 

Sorry and thanks again.

---

### Post by AlexanderSupertramp on 2009-03-28
:)

---

### Post by mgranet on 2009-03-28
> **AlexanderSupertramp said:**
> thanks a lot for your time mgranet, I got the issue.

Please do not get furious, :(....

the path "/home/neo/aptana", it should have been "/home/neo/aptana/AptanaStudio", pointing to executable. 

Sorry and thanks again.

Glad you figured it out! :)

Why I would be furious, however, I can't understand. :confused:

---

### Post by AlexanderSupertramp on 2009-03-28
well it was a silly mistake and I should have figured it out myself an hour ago, 
I thought you could not have had any clue about paths on my system.....

---

