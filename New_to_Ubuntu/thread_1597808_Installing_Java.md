---
title: "Installing Java"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by SunEatsMoon on 2010-10-15
Trying to play Minecraft and having trouble with Java, I think. Either way I want to install the latest version of Java, I somehow managed to get a version of Java installed but Minecraft still won't run correctly.
Not looking for minecraft help but help getting the most recent verson of Java.

Kubuntu 10.04 
HP Pavillon zv6000

---

### Post by TBABill on 2010-10-15
Did you remove the open source java after installing sun java? If the iced tea plugin is still installed you can try removing it, then if that doesn't work remove all open java items via synaptic.

---

### Post by SunEatsMoon on 2010-10-15
I didn't even think of trying to remove the older versions. I get the basic idea of Synaptic but not how it works. 
Out with the old in with the new? where do I start?

---

### Post by lobralleo on 2010-10-15
Try this from command line:

```
sudo apt-get remove icedtea*
```

Or, in Synaptic, search for icedtea and remove all installed packages with that name.

---

### Post by SunEatsMoon on 2010-10-15
Alright, removed icedtea. 
Now how do I get/make sure I have the latest version.

---

### Post by lobralleo on 2010-10-15
To check your version of Java, load this URL:

[www.java.com/en/download/installed.jsp?detect=jre](www.java.com/en/download/installed.jsp?detect=jre)

Under Lucid, you should have by default Java version 6.20, i.e. two updates short of the latest. It should not matter a lot: I just tried to load Minecraft and it apparently works with this version (haven't tried a lot tough, I never played it before).

If you want to install the latest Java, you can download the .bin installer and follow the directions given on the Sun Java website. Again, make sure to remove all installed Java components before doing that.

---

### Post by lobralleo on 2010-10-15
Sorry, the correct url is:

[http://www.java.com/en/download/installed.jsp?detect=jre&try=1](http://www.java.com/en/download/installed.jsp?detect=jre&try=1)

My apologies :)

---

### Post by TBABill on 2010-10-15
In synaptic there is a search function in the upper right. Just enter your search parameter and when you find the file(s) you want to install or remove, just right click and select what you want to do. When finished choosing, then click apply and let it do its thing.

---

### Post by SunEatsMoon on 2010-10-15
Well I have the 6.21 and I'm still having problems, It loads and lets me look around for about 3 seconds than crashes. I thought I could do this all without help so I've been indiscriminately installing hoping for the best and when I put in "Java" in synaptic a whole list of things comes up. What, if anything should be done about that.
If its not a Java issue its probably a graphics card problem, should I start a new thread for that?

---

### Post by SunEatsMoon on 2010-10-15
> **TBABill said:**
> In synaptic there is a search function in the upper right. Just enter your search parameter and when you find the file(s) you want to install or remove, just right click and select what you want to do. When finished choosing, then click apply and let it do its thing.

Thanks, I played around a second and figured that out.

---

### Post by beew on 2010-10-16
You don't need to remove the open java,  all you need is to set the sun version as the default (you may need open java for other purposes later)

  To set sun-java as the default type in the terminal

```
sudo update-java-alternatives -s java-6-sun
```, then supply your password when prompted.

To check that you have the correct default type

```
java -version
```

---

### Post by jtarin on 2010-10-16
> **beew said:**
> You don't need to remove the open java,  all you need is to set the sun version as the default (you may need open java for other purposes later)I'm not familiar with this usage of another java application along with the default....could you expound further?

---

### Post by beew on 2010-10-16
> **jtarin said:**
> I'm not familiar with this usage of another java application along with the default....could you expound further?

I think some apps allow you to choose the java version (eclipse?) to be used instead of the system default. In any case you can certainly change the system default depending on what you want to run. Not the most elegant approach but still better than uninstalling and reinstalling different versions of java depending on the situation.

---

### Post by jtarin on 2010-10-16
> **beew said:**
> I think some apps allow you to choose the java version (eclipse?) to be used instead of the system default. In any case you can certainly change the system default depending on what you want to run. Not the most elegant approach but still better than uninstalling and reinstalling different versions of java depending on the situation.This is the exact reason I have always installed Sun-java....so all my java apps work first time everytime. Open source is OK for the occasional browser plugin and for standby duty in some apps but........:(

---

### Post by beew on 2010-10-16
But I may also just want to try different versions of java to compare the difference and gauge the progress of the open source one, as a learning exercise. :) Same reason why some people go through great length to tweak gnash while they can simply install flash.

---

### Post by jtarin on 2010-10-16
Please feel free to install and use what you want....far be it from me to tell you different. I've already had my learning and comparing experiences with Java.

---

### Post by SunEatsMoon on 2010-10-16
I found a very helpful tutorial in another thread and I have the latest Java and still having problems, thus; not a Java problem.

---

### Post by jtarin on 2010-10-16
Excellent...no java problems.

---

