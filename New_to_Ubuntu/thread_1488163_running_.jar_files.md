---
title: "running .jar files"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by jrwebber on 2010-05-19
i have been using for linux for about a week. Today I installed something for the first time via command line which was something to celebrate. so lets just say I'm very new to this. I am trying to open a .jar file and installed java (yes my first install) i have tried the command java -jar <filename.jar> and got the message "aborted" I dont really know what else to try so any suggestions would be helpful

---

### Post by KdotJ on 2010-05-19
hello and welcome to ubuntu
Try give us a little more information

- how did you install java?
- what is the .jar file?
- have you tried running any other .jar files this way?
- is "aborted" the only thing it says?

---

### Post by jrwebber on 2010-05-19
I just went online and downloaded jre 1.6.0_20 (im thinking maybe i should get this latest java version sun 6) and i installed it using the ./ <file name> etc. I followed the instructions on the java site and everything seemed to go well. 

the .jar file is a program called Jearth its sort of like google earth and no i have not tried any other .jar files i only have the one haha.

as soon as I type in the command it says aborted and nothing else

thanks :)

---

### Post by oracle2b on 2010-05-19
install java: sudo apt-get install sun-java6-jre

try running the command like: ./filename.jar or sudo ./filename.jar

---

### Post by jrwebber on 2010-05-19
the install seemed to work, but when i type sudo ./jmars-public-earth.jar it says command not found or permission denied

---

### Post by KdotJ on 2010-05-19
> **jrwebber said:**
> the install seemed to work, but when i type sudo ./jmars-public-earth.jar it says command not found or permission denied

After you installed the sun-java6-jre, did you try to run the 

```
java -jar <filename>.jar
```

???

---

### Post by jrwebber on 2010-05-19
yes and it still says "aborted" nothing else :/

---

### Post by KdotJ on 2010-05-19
Very strange...
try a different .jar file (another program if you can) 
It may be something with the jar file itself rather than your machine.

Just a word of advice though, it's not advised to download stuff from the net and install it to your machine. Have a look in the Ubuntu Software Centre for stuff

---

### Post by markibrax on 2010-05-19
Hello everybody!

---

### Post by gdonwallace on 2010-05-20
First off, Welcome to ubuntu and the forums.

I too had problems with .jar files until I tried this.  Using Nautilus, navigate to where the .jar file is saved, right click on it and choose sun java to run the program.  I do this all the time and works for me without a hitch.

---

### Post by oracle2b on 2010-06-18
if permission was denied try give the file permission to execute.

> chmod +x jmars-public-earth.jar than run it

---

### Post by lykeion on 2010-06-18
Well, I have sun-java6-jre installed and I downloaded this JEarth application and had no problem running it with:

> java -jar jmars-public-earth.jar

You could also run it from Nautilus (Open with Sun Java 6 Runtime)

---

