---
title: "Lucid/java question"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by flyfishingphil on 2010-05-02
I'm wondering if some of the problems I am having with websites, and the Lucid version I just did the upgrade to, (Pogo games & Free Slots video choppiness) is directly related to the Java. I followed instructions on installing the Java jdk-6-jre/Ubuntu system and got this back in the window:

dk-6-jre-lib icedtea-plugin
[sudo] password for flyfishingphil: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openjdk-6-jre is already the newest version.
[U]openjdk-6-jre-lib is already the newest version.
openjdk-6-jre-lib set to manually installed.[/U]
E: Couldn't find package icedtea-plugin

If you look at the underlined lines (7 & 8) it shows I already have the java installed but, when looking in system monitor, it shows java as "sleeping". Is it "active"? Is there something I need to do to make it "operate" automatically if/when needed, or is it already doing that?

Please reply in very basics since I am still a noob and don't speak the language fluently, yet.

Thanks for any assists.](*,)]

---

### Post by nhasian on 2010-05-02
instead of using the open source java runtime, try sun's instead.

Add partner repository using the following command:

```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
```

Update the source list:

```
sudo apt-get update
```

Now install sun java packages using the following commands

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

See what you are currently using:
```
java -version
```

List available alternatives:
```
sudo update-java-alternatives -l
```

Change to Sun:
```
sudo update-java-alternatives -s java-6-sun
```

change back to openjava with:
```
sudo update-java-alternatives -s java-6-openjdk
```

---

### Post by flyfishingphil on 2010-05-03
OK, it works, but it is slow. 
9:29:55 enter [www.pogo](www.pogo) > 9:30:37 connects to link > 9:30:42 "loading game" > 9:30:57 game finally opens

9:31;52 clicked free slots link > 9:31:42 site page opened clicked on slot > 9:31:57 slot box shows java > 9:32:20 slot playable

I'll check on it again later and see if maybe it's just because this is the "first" visit to these locations using Lucid. Did notice that on the free slots location it showed me with a "new player" starting score, not the points I had built up in other visits.

Hope this helps others. When it doesn't seem to be connecting just walk away, pet the cat, drink a glass of ******** and then see what it's done. 

Tnx again for the assist. Will keep progress posted here for a couple of days.:confused:

---

