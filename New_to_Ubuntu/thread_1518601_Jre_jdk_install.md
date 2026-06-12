---
title: "Jre jdk install"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by Kirkland14 on 2010-06-26
So I am trying to install sun JRE and JDK.  after the download it asks to choose an application to use.  I'm not sure what to do. I'm not very linux oriented yet.  I keep seeing things about repositories.  What are these for and how do I make one?  

Thanks

Kevin

ps when i try this:

```
sudo add-apt-repository &#8220;deb http://archive.canonical.com/ lucid  partner&#8221;
```

i get this:

```
Error: need a repository as argument

```

---

### Post by dearingj on 2010-06-26
> **Kirkland14 said:**
> when i try this:

```
sudo add-apt-repository &#8220;deb http://archive.canonical.com/ lucid  partner&#8221;
```

i get this:

```
Error: need a [repository]("https://help.ubuntu.com/community/Glossary#R") as argument

```

I've read online that you need to replace those [curly quotes]("http://en.wiktionary.org/wiki/curly_quote") with [straight quotes]("http://en.wiktionary.org/wiki/straight_quote") when you enter that command.

After you enter that command, assuming it works without any more errors, you enter "[sudo]("https://help.ubuntu.com/community/Glossary#S") apt-get install sun-java6-jdk". This will download and install the JDK and (since the JDK [package]("https://help.ubuntu.com/community/Glossary#P") lists the JRE package as a [dependency]("https://help.ubuntu.com/community/Glossary#D")) the JRE. Note that you will be asked to accept Sun's Operating System Distributor license agreement; if I remember correctly you just have to press space until you get to the bottom of the agreement and then press y to accept.

---

### Post by Kirkland14 on 2010-06-26
> **dearingj said:**
> I've read online that you need to replace those [curly quotes]("http://en.wiktionary.org/wiki/curly_quote") with [straight quotes]("http://en.wiktionary.org/wiki/straight_quote") when you enter that command.

After you enter that command, assuming it works without any more errors, you enter "[sudo]("https://help.ubuntu.com/community/Glossary#S") apt-get install sun-java6-jdk". This will download and install the JDK and (since the JDK [package]("https://help.ubuntu.com/community/Glossary#P") lists the JRE package as a [dependency]("https://help.ubuntu.com/community/Glossary#D")) the JRE. Note that you will be asked to accept Sun's Operating System Distributor license agreement; if I remember correctly you just have to press space until you get to the bottom of the agreement and then press y to accept.

So this is what I got:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jdk has no installation candidate

```Thanks for the help

---

### Post by DougieFresh4U on 2010-06-26
Where are you installing it from? Sun Java is in the 'partner' repo now

---

### Post by adobrakic on 2010-06-26
> **Kirkland14 said:**
> So this is what I got:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jdk has no installation candidate

```Thanks for the help

Like the poster above said, you have to go into Synaptic and enable the Partner repo.

---

### Post by Kirkland14 on 2010-06-26
> **DougieFresh4U said:**
> Where are you installing it from? Sun Java is in the 'partner' repo now

So I'll apologize first off because I'm still a noob to linux.  I downloaded it from the Sun site and followed their directions but when I try and opee the download it asks me to pick an application to open it with.  I tried this code from their instructions:

```
chmod a+x jre-6u20-linux-i586.bin
```and got this:

```
chmod: cannot access `jre-6u20-linux-i586.bin': No such file or directory

```also I don't really understand what the repository is(i can imagine by the name) but don't really understand how they work or to make one(if that's what I do) etc..

Thanks

Kevin

---

### Post by Kirkland14 on 2010-06-26
> **adobrakic said:**
> Like the poster above said, you have to go into Synaptic and enable the Partner repo.

So exactly what do I look for in Synaptic to check?

thanks

Kevin

---

### Post by adobrakic on 2010-06-26
In Synaptic, go to Settings > Repos, then click on "Other Software" tab, and checkmark the partner repository.

---

### Post by DougieFresh4U on 2010-06-26
> **adobrakic said:**
> In Synaptic, go to Settings > Repos, then click on "Other Software" tab, and checkmark the partner repository.

Not sure but I thought it had to be Karmic repo as Java not in Lucid.

---

### Post by Kirkland14 on 2010-06-26
> **adobrakic said:**
> In Synaptic, go to Settings > Repos, then click on "Other Software" tab, and checkmark the partner repository.

Thanks.  I got everything going no.  I appreciate the help

Kevin

---

