---
title: "I have a sound problem, I would really appreciate youre help!"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by maher139 on 2010-03-05
So, I play on an internet go server for KGS for those of you who know what go is, and I have a problem with the sound and audio for it. Someone recommended I post anout it here and I took up his advice. My problem is I don't know how to set up my sound to provide working oss emulation. Can someone help me with this? 
Thank you in advance,
maher139~

P.S. I have ubuntu 9.10

---

### Post by solar george on 2010-03-06
Do you know the name of the executable for the "go" client (note I don't know what this is)? If so try opening a terminal and typing:
```
padsp *executable*
```
where *executable* is the name of the client executable.

---

### Post by KIAaze on 2010-03-06
It's usually played through a java applet.

The command is:
```
javaws cgoban.jnlp
```
if you download the java applet from here:
[http://www.gokgs.com/download.jsp](http://www.gokgs.com/download.jsp) (java web start client)

or
```
javaws http://files.gokgs.com/javaBin/cgoban.jnlp
```
(as they suggest on the site)

So it would be:
```
padsp javaws cgoban.jnlp
```
or
```
padsp javaws http://files.gokgs.com/javaBin/cgoban.jnlp
```

I also didn't have sound, but haven't tried it ingame with padsp yet.
Don't want to start a game and quit directly after all.

---

### Post by maher139 on 2010-03-06
I tried that code, it didn't work, it just took me to a "did you mean" page on google.

---

### Post by KIAaze on 2010-03-07
Did you enter that code in the terminal or in the browser?
Because I can't see why the terminal would mention anything about Google.

The terminal or console:
[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

---

### Post by maher139 on 2010-03-07
I tried it in the terminal now, still no sound. What else could it be?

---

### Post by solar george on 2010-03-07
Just wondering, are you running 32 or 64 bit ubuntu?

---

### Post by solar george on 2010-03-07
also are you using the sun Java package or the openjdk one?
If the sun one then either try using the openjdk version or do
```
sudo mv /usr/lib/jvm/java-6-sun/jre/lib/i386/libjsoundalsa.so /usr/lib/jvm/java-6-sun/jre/lib/i386/libjsoundalsa.so.bk

```
This will disable the alsa support in sun-java-6 and force it to fall back to oss which should make the padsp command work.

---

### Post by maher139 on 2010-03-07
64 bit and im using sun java
I'll try that right now ^^ thank you everyone.
Edit: I tried it, and still I still have no sound, maybe it could be something else?
Edit2: Do I put that code into the terminal or elsewhere?

---

### Post by jamie0nz on 2010-05-06
I have had problems with sound and cgoban too. openjdk is so close ... the sounds for time running out come up (albiet a little oddly) but the stones hitting the board dont make a sound. Eventually I resorted to going to the sun website, downloading the 64-bit java (I run Lucid on my box now) and putting this in the /opt directory. It doesn't link in to firefox and it doesn't do a whole lot of things but I can run cgoban with ...

/opt/jre1.6.0_20/javaws/javaws "/home/jamie/.netx/cache/http/files.gokgs.com/javaBin/cgoban-nfa.jnlp"

... and it works perfectly.

The cache file I cut and pasted from running the jnlp file with openjdk, which would work in every way except sound - which I like too much to be able to go without.

I used to run the above with a padsp in front, but don't seem to need it now.

---

