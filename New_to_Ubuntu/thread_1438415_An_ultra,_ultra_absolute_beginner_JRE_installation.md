---
title: "An ultra, ultra absolute beginner JRE installation tutorial?"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by RebeccaHowarth on 2010-03-25
I am trying to use the letter Wizard in Ubuntu.  The message I get is:

"OpenOffice.org requires a Java runtime environment to perform this task.  Please install a JRE and restart OpenOffice.org.  Please install the openoffice.org-java-common package for this functionality."

Is there some extremely basic, step-by-step tutorial for how to do this?  I have basically no command line experience.  I have no idea what a JRE is, why I need it, how to get it, etc.  All I'm trying to do is write a letter!

---

### Post by andrewthomas on 2010-03-25
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Here it is.

---

### Post by rockerphil on 2010-03-25
simply open up a terminal and run this command to install Java

```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

after that does it's thing you should be good to go. hope this helps,

Phil

---

### Post by RebeccaHowarth on 2010-03-25
> **rockerphil said:**
> simply open up a terminal and run this command to install Java

```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

after that does it's thing you should be good to go. hope this helps,

Phil

Thanks Phil.  I just typed that in, and the licensing agreement just came up, but it does not give me a new line to type on, and I can't click OK or anything like that, so how do I accept the agreement?

---

### Post by J_Stanton on 2010-03-25
> **RebeccaHowarth said:**
> Thanks Phil.  I just typed that in, and the licensing agreement just came up, but it does not give me a new line to type on, and I can't click OK or anything like that, so how do I accept the agreement?

just tick the box on the left and click next.

---

### Post by ankspo71 on 2010-03-25
> **RebeccaHowarth said:**
> so how do I accept the agreement?

How I do it is I press the Tab key on my keyboard, then I am able to accept the license.

---

