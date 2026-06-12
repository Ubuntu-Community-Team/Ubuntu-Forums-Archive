---
title: "totem dvd player ubunto"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by richard tor on 2009-07-06
The Totem dvd player needs a gstreamer ? please help a complete novice:p

---

### Post by scrooge_74 on 2009-07-06
Next time take some time to check the forum, there is a good HowTo for this here

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by scrooge_74 on 2009-07-06
> **scrooge_74 said:**
> Next time take some time to check the forum, there is a good HowTo for this here

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

More beginers info [here]("http://ubuntuforums.org/showthread.php?t=1052065"), also in the forum

---

### Post by ubudog on 2009-07-06
Go to Applications>Add/Remove Programs search for gstreamer and select the first six and hit Apply Changes.  Then close totem and open it again.  After that it should work.

---

### Post by richard tor on 2009-07-07
> **ubudog said:**
> Go to Applications>Add/Remove Programs search for gstreamer and select the first six and hit Apply Changes.  Then close totem and open it again.  After that it should work.
Thankyou but it still says your gstreamer installation is missing a plug in

---

### Post by Teamgeist on 2009-07-07
Install the ubuntu-restricted-extras Package. That will pull all necessary codecs for you.

---

### Post by richard tor on 2009-07-07
> **Teamgeist said:**
> Install the ubuntu-restricted-extras Package. That will pull all necessary codecs for you.
Please show me how and I will be forever in your debt:p

---

### Post by Teamgeist on 2009-07-07
Go to the Terminal (Applications--> Accessories--> Terminal

Type this: (right-click and copy it from here)
```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

Enter your password (you won't see anything, but it still "types") and hit enter.

That should be it.

You can also look for the Package in Synaptic (System--> Administration--> Synaptic-Package-Manager) and install it from there.

Post back if you have Problems or if it worked. :-)

This Package will install a lot of stuff, including Java, Flash, codecs etc

---

### Post by scrooge_74 on 2009-07-07
One more reason to point to the tutorial, that way he gets to read something and leans instead of just typing commands like a tech monkey

:lolflag:

---

### Post by richard tor on 2009-07-07
still no good I'm sorry any other help would be great

---

### Post by scrooge_74 on 2009-07-07
Did you follow the tutorials in the Multimedia section? You proly missing the DVD plugin, go back to the tutorial you proly skipped something

---

### Post by ubudog on 2009-07-07
Try this: [http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux](http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux)

---

### Post by scrooge_74 on 2009-07-07
> **ubudog said:**
> Try this: [http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux](http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux)


That would be part 4/5 of the Multimedia Tutorial, assuming he got that far reading it.

---

### Post by ubudog on 2009-07-07
Oh ok. Sorry.

---

### Post by scrooge_74 on 2009-07-07
> **ubudog said:**
> Oh ok. Sorry.

Nah, one more reason I try to point people to the tutorial or explanation that once helped me instead of just giving them commands to type.

Example, this week/weekend I get to play with a empty box to turn it into a home/small office server. The only time you will see me asking questions is if I really get ](*,) at some point. That is the best way to learn this stuff.

---

### Post by philinux on 2009-07-07
> **richard tor said:**
> The Totem dvd player needs a gstreamer ? please help a complete novice:p

Click the medibuntu & restricted formats links below.

---

