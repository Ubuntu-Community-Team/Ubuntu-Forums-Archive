---
title: "downloaded java. having trouble instaling"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by Bunny12391 on 2011-05-27
the instructions the download gives are a little hard for me to understand. im still new

---

### Post by TBABill on 2011-05-27
Easier to just go to Software Sources (or in Synaptic click Repositories) and check the box for Canonical Partner Repositories. Then you can click reload in Synaptic, search for Sun Java and install the files directly. That'll save you the headache of installing from the Java website.

---

### Post by Bunny12391 on 2011-05-27
> **TBABill said:**
> Easier to just go to Software Sources (or in Synaptic click Repositories) and check the box for Canonical Partner Repositories. Then you can click reload in Synaptic, search for Sun Java and install the files directly. That'll save you the headache of installing from the Java website.
where would that software sources be?

---

### Post by Bunny12391 on 2011-05-28
its not working

---

### Post by wildmanne39 on 2011-05-28
> **Bunny12391 said:**
> its not workingHi, did you use synaptic? what errors are you getting?

---

### Post by nitstorm on 2011-05-28
```

sudo apt-get install openjdk-6-jdk openjdk-6-jre

```

---

### Post by wog on 2011-05-29
The version of Sun Java in Synaptic is old. No-one has apparently seen fit to update it yet.

---

### Post by spcwingo on 2011-05-29
If you have the partner repositories enabled, use this command in a terminal:

```
sudo apt-get install -y sun-java6-plugin sun-java6-jre sun-java6-fonts sun-java6-bin
```

If you haven't enabled the partner repositories and you need a hand in doing that, just let me know.  ;)

---

### Post by wog on 2011-05-30
I'm guessing I at least don't have partner repos installed, since when I tried your command line instruction, all I got was 1.6.24, and not 1.6.25.

Help would be helpful. :)

---

### Post by spcwingo on 2011-05-30
> **wog said:**
> I'm guessing I at least don't have partner repos installed, since when I tried your command line instruction, all I got was 1.6.24, and not 1.6.25.

Help would be helpful. :)

I was replying to the OP.  I don't think anyone has packaged 1.6.25 for 10.10 yet (I'm assuming that's what release you're using by your profile).

[COLOR="Red"]EDIT:[/COLOR] I just found a PPA that might have it.  You can check out the PPA here:

[https://launchpad.net/~sun-java-community-team/+archive/sun-java6]("https://launchpad.net/~sun-java-community-team/+archive/sun-java6")

---

