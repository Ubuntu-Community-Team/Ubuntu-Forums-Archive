---
title: "How do I install Java?"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by brawnypandora0 on 2011-03-19
[http://www.chess.com/play/computer.html](http://www.chess.com/play/computer.html)

Back when I had Windows, a dialogue box popped up when I visited the page for the first time and Java was automatically installed. Now with Ubuntu, there's no box. What do I do to install Java?

---

### Post by howefield on 2011-03-19
There are two versions of java to choose from, the open source version openjdk which you can install via synaptic package manager or the software centre, and Suns java which you'll find in the Partner repository (from 10.04 on).

If you install suns java, you'll need sun-java6-fonts sun-java6-jre and sun-java6-plugin packages. 

```
https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Sun%20Java%20moved%20to%20the%20Partner%20repository
```

---

### Post by brawnypandora0 on 2011-03-19
SO which one should I install?

---

### Post by 5149.5 on 2011-03-19
You can[ start here]("http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com"). I did it last night for Libre office and everything went fine but I just discovered that firefox/minefield doesn't have any java configured so I've got another mystery to work on.

---

### Post by howefield on 2011-03-19
If you have no preference one way or the other on free vs proprietary grounds, I'd install Sun Java. 

Only for the fact the open version doesn't always work so well.

---

### Post by brawnypandora0 on 2011-03-19
> **howefield said:**
> There are two versions of java to choose from, the open source version openjdk which you can install via synaptic package manager or the software centre, and Suns java which you'll find in the Partner repository (from 10.04 on).

If you install suns java, you'll need sun-java6-fonts sun-java6-jre and sun-java6-plugin packages. 

```
https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Sun%20Java%20moved%20to%20the%20Partner%20repository
```

My Ubuntu version is older than 10.04. So what do I do?

---

### Post by howefield on 2011-03-19
What version are you running ?

---

### Post by brawnypandora0 on 2011-03-19
**Ubuntu 9.04**

---

### Post by howefield on 2011-03-19
OK, presumably you know that is not a great idea given 9.04 is no longer a supported edition (end of life).

In any event, your best bet for installing to an end of life Ubuntu would be to install manually.

Follow the instructions here...

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by 5149.5 on 2011-03-19
I got the link to the java directory installed in the FF plugins directory. It wasn't a big deal for me but there is no way that the average guy is going to install a java plugin in hs browser. [IMG]http://www.pic4ever.com/images/Bananeyessss.gif[/IMG]

---

### Post by brawnypandora0 on 2011-03-19
> **5149.5 said:**
> I got the link to the java directory installed in the FF plugins directory. It wasn't a big deal for me but there is no way that the average guy is going to install a java plugin in hs browser. [IMG]http://www.pic4ever.com/images/Bananeyessss.gif[/IMG]

What's the FF plugins directory?

I'm completely new to Linux, and I don't know which I'm supposed to install in Synaptic Package Manager. There's so many--cacao source, default-jre-headless, icedtea, openjdk-6-jre-, openjdk-6-plugin, open-6-source. etc, etc. I just want the version of Java to play online games. So which one do I install?

What does the "S" at the top left of Synaptic column mean? Why do some packages have Ubuntu icons and other don't?

Also, why is it when I try to install some packages, I get a message that says "You are about to install software that can't be authenticated! Doing this could allow a malicious individual to damage or take control of your system"

Java is so ubiquitous, so why doesn't Ubuntu come with it PRE-installed?

---

### Post by 5149.5 on 2011-03-19
The way I did it was using this down load: [http://javadl.sun.com/webapps/download/AutoDL?BundleId=47143](http://javadl.sun.com/webapps/download/AutoDL?BundleId=47143) with these instructions: [http://java.com/en/download/help/linux_install.xml#selfextracting](http://java.com/en/download/help/linux_install.xml#selfextracting) 

 That will get the java installed. Then you use these instructions: [http://support.mozilla.com/en-US/kb/Using%20the%20Java%20plugin%20with%20Firefox](http://support.mozilla.com/en-US/kb/Using%20the%20Java%20plugin%20with%20Firefox)  for configuring the browser to use java.

---

### Post by brawnypandora0 on 2011-03-20
I don't understand the instructions. I downloaded the file to the Downloads Folder. When I clicked on the icon, I got a box that said Could not display...the file is unknown type. Following step one in your link, I typed that into the terminal and got a message that read, "bash: version: No such file or directory"

So what do I do?

Also, what's bash?

---

### Post by 5149.5 on 2011-03-20
> **brawnypandora0 said:**
> I don't understand the instructions. I downloaded the file to the Downloads Folder. When I clicked on the icon, I got a box that said Could not display...the file is unknown type. Following step one in your link, I typed that into the terminal and got a message that read, "bash: version: No such file or directory"

So what do I do?

Also, what's bash?

Nothing in step 1 says to click on the icon so that's not a problem. Before you enter the command in step 1 you have to change directories to the one where the file resides that you down loaded. That is done using the cd command. bash is the shell that is interpreting the commands you are entering on the terminal. 

That is a pretty lousy procedure for the installation. There is a fair amount of reading between the lines and ad-libbing required. The average non computer geek will struggle with it.

---

