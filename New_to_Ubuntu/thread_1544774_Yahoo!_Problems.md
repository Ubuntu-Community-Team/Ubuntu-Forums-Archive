---
title: "Yahoo! Problems"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by uRock on 2010-08-02
On one of my Karmic machines(64bit) I am having issues with using the Yahoo Beta functions. It has a hard time running the java that makes the instant emails display, but more importantly I am having issues with uploading attachments to emails, which causes the page to freeze.

Has anyone else had this problem and/or does anyone know what might fix it?

Thanx,
uRock

---

### Post by nhasian on 2010-08-03
what is the output of the terminal command:

```
java -version
```

---

### Post by uRock on 2010-08-03
```
uRock@uRock java -version  
java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) 64-Bit Server VM (build 16.3-b01, mixed mode)

```

---

### Post by nhasian on 2010-08-03
thats the same java i have and yahoo works fine.  lets see if you have any other java installed.  please use the terminal command:

```
sudo update-java-alternatives -l
```

---

### Post by uRock on 2010-08-03
> **nhasian said:**
> thats the same java i have and yahoo works fine.  lets see if you have any other java installed.  please use the terminal command:

```
sudo update-java-alternatives -l
```
```
uRock@uRock sudo update-java-alternatives -l
[sudo] password for ronnie: 
java-6-sun 63 /usr/lib/jvm/java-6-sun
```

---

### Post by nhasian on 2010-08-03
i'm out of ideas.  i dont know why your yahoo is not working properly.  i have the same exact output of those terminal commands as you do so we are both running the same java.  I even sent myself an email with a 600k image attachment and it went through just fine.

---

### Post by uRock on 2010-08-03
And you are using the Yahoo Beta? I guess I'll try installing Lucid and see if that makes the difference.

Thanx for your help,
uRock

---

### Post by nhasian on 2010-08-04
> **uRock said:**
> And you are using the Yahoo Beta? I guess I'll try installing Lucid and see if that makes the difference.

below your avatar it already said you were using Lucid...

how do i know if I'm on yahoo beta or not? sometimes when i go to mail.yahoo.com it asks me if i want classic yahoo or the new yahoo and i always do the new one.

---

### Post by mastablasta on 2010-08-04
Yahoo is strange on linux. i have 32bit 10.04, sometimes it really reacts slow. i am not sure what they are doing there, because others sites don't have any issues.

---

### Post by uRock on 2010-08-04
> **nhasian said:**
> below your avatar it already said you were using Lucid...

how do i know if I'm on yahoo beta or not? sometimes when i go to mail.yahoo.com it asks me if i want classic yahoo or the new yahoo and i always do the new one.
The PC I am working on is the HP in my signature.(the wife's) I'll have to wait for my wife to log into hers to get a screenshot of it. I use the old version of Yahoo that looks like this and requires opening a new page to see each email.

---

### Post by uRock on 2010-08-04
I went ahead and moved mine to the New version, not called beta anymore.

---

