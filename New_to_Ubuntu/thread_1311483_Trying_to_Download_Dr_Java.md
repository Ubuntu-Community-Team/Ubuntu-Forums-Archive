---
title: "Trying to Download Dr Java"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by blackmatrix00 on 2009-11-02
I'm new to ubuntu and just started using it. I've been trying to download Dr Java on Ubuntu 9.04 and 9.10. Everytime I click on it I open it with Archive Manager, so I downloaded Wine and thought that might work. But it didn't, every time I use wine it says "This application requires a java runtime environment 1.5.0." I'm not sure what to do beyond this

Does anyone know the answer to download Dr Java?

---

### Post by liquidbee on 2009-11-02
Install Java JRE ( I would go for the latest version ):
```
sudo apt-get install sun-java6-jre sun-java6-plugin

```Open Terminal, change the working directory to where your DrJava file ( replace the name if it's different from what you have there ) is and execute the following command:
```
java -jar DrJava.jar
```

---

### Post by blackmatrix00 on 2009-11-02
What do you mean by " change the working directory to where your DrJava file is" ? I'm not clear as to what I should do.

---

### Post by liquidbee on 2009-11-02
> **blackmatrix00 said:**
> What do you mean by " change the working directory to where your DrJava file is" ? I'm not clear as to what I should do.

A few examples:
```
cd $HOME/Desktop
cd $HOME/Downloads
```

[COLOR=DimGray]$HOME [/COLOR]stand for [COLOR=DimGray]/home/username [/COLOR]( eg., [COLOR=DimGray]/home/liquid[/COLOR] ).

---

### Post by blackmatrix00 on 2009-11-02
> **liquidbee said:**
> A few examples:
```
cd $HOME/Desktop
cd $HOME/Downloads
```

[COLOR=DimGray]$HOME [/COLOR]stand for [COLOR=DimGray]/home/username [/COLOR]( eg., [COLOR=DimGray]/home/liquid[/COLOR] ).
So should I input DrJava. jar $HOME/Desktop into the terminal?

---

### Post by liquidbee on 2009-11-02
> **blackmatrix00 said:**
> So should I input DrJava. jar $HOME/Desktop into the terminal?

DrJava.jar ( if that's not the right name, rename it ) is on your Desktop ( if not, move it now ):
```
cd $HOME/Desktop
java -jar DrJava.jar
```

---

### Post by blackmatrix00 on 2009-11-02
> **liquidbee said:**
> DrJava.jar ( if that's not the right name, rename it ) is on your Desktop ( if not, move it now ):
```
cd $HOME/Desktop
java -jar DrJava.jar
```
The file I have on my desktop for Dr Java is called "drjava-stable-20090821-r5004.exe" is that the file name you want me to change? Or do you want me to extract it or something?

---

### Post by liquidbee on 2009-11-02
> **blackmatrix00 said:**
> The file I have on my desktop for Dr Java is called "drjava-stable-20090821-r5004.exe" is that the file name you want me to change? Or do you want me to extract it or something?

You've downloaded the wrong file. [Click here ]("http://downloads.sourceforge.net/project/drjava/1.%20DrJava%20Stable%20Releases/drjava-stable-20090821-r5004/drjava-stable-20090821-r5004.jar?use_mirror=sunet")to download JAR file.

---

### Post by blackmatrix00 on 2009-11-02
> **liquidbee said:**
> You've downloaded the wrong file. [Click here ]("http://downloads.sourceforge.net/project/drjava/1.%20DrJava%20Stable%20Releases/drjava-stable-20090821-r5004/drjava-stable-20090821-r5004.jar?use_mirror=sunet")to download JAR file.
I downloaded it, now what do I do? It's not on my desktop.

---

### Post by liquidbee on 2009-11-02
> **blackmatrix00 said:**
> I downloaded it, now what do I do? It's not on my desktop.

```
find $HOME -i -name drjava-stable-20090821-r5004.jar -exec java -jar {} \;
```What's the output ?

---

### Post by blackmatrix00 on 2009-11-02
> **liquidbee said:**
> ```
find $HOME -i -name drjava-stable-20090821-r5004.jar -exec java -jar {} \;
```What's the output ?
This is the output:

find: unknown predicate `-i'

What should I do now?

---

### Post by liquidbee on 2009-11-02
> **blackmatrix00 said:**
> This is the output:

find: unknown predicate `-i'

What should I do now?

Execute it without the -i argument:
```
find $HOME -name drjava-stable-20090821-r5004.jar -exec java -jar {} \;
```

---

### Post by blackmatrix00 on 2009-11-02
There was no output afterward. Does that mean that it worked? If so, what now?

---

### Post by liquidbee on 2009-11-02
> **blackmatrix00 said:**
> There was no output afterward. Does that mean that it worked? If so, what now?

You should see it opening ( at least it does so on my PC ) :roll:

```
find $HOME -name drjava
```

Please reply with the output.

---

### Post by blackmatrix00 on 2009-11-02
Dr Java seems to work now when I click on the .jar file on my desktop that you told me download. Now all that is left is getting the JDK for the compiler. Do you know how to do that?

---

### Post by liquidbee on 2009-11-02
> **blackmatrix00 said:**
> Dr Java seems to work now when I click on the .jar file on my desktop that you told me download. Now all that is left is getting the JDK for the compiler. Do you know how to do that?
```

sudo apt-get install sun-java6-jdk sun-java6-fonts
```

---

### Post by blackmatrix00 on 2009-11-02
I downloaded jdk-1_5_0_12-nb-5_5_1-win-ml.exe for the other .exe file.

---

### Post by blackmatrix00 on 2009-11-02
It appears to be working. Thank you for you help, but one last question, do you know why the .jar file does not have the Dr Java logo on it?

---

### Post by blackmatrix00 on 2009-11-02
> **liquidbee said:**
> DrJava.jar ( if that's not the right name, rename it ) is on your Desktop ( if not, move it now ):
```
cd $HOME/Desktop
java -jar DrJava.jar
```
Should I use the code you wanted me to use earlier? 

Code: 
cd $HOME/Desktop
java -jar DrJava.jar

---

