---
title: "No active java"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by rjr0218 on 2009-08-04
I'm trying to install java for Linix.  It doesn't install properly. Can you please help?

Thanks!

---

### Post by arochester on 2009-08-04
Connect to the internet, open a Terminal and issue the command: > sudo apt-get install ubuntu-restricted-extras

---

### Post by credobyte on 2009-08-04
Execute this command in Terminal:
```
sudo apt-get install sun-java6-jre sun-java6-plugin

```

> **arochester said:**
> Connect to the internet, open a Terminal and issue the command:
Ubuntu restricted extras does NOT contain Java runtime environment.

---

### Post by oldos2er on 2009-08-04
> **credobyte said:**
> Execute this command in Terminal:
```
sudo apt-get install sun-java6-jre sun-java6-plugin

```Ubuntu restricted extras does NOT contain Java runtime environment.

 apt-cache show says it does: Installing this package [ubuntu-restricted-extras] will pull in support for MP3 playback and decoding, support for various other audio formats (GStreamer plugins), Microsoft fonts, Java runtime environment, Flash plugin, LAME (to create compressed audio files), and DVD playback.

---

### Post by credobyte on 2009-08-05
> **oldos2er said:**
> apt-cache show says it does: Installing this package [ubuntu-restricted-extras] will pull in support for MP3 playback and decoding, support for various other audio formats (GStreamer plugins), Microsoft fonts, Java runtime environment, Flash plugin, LAME (to create compressed audio files), and DVD playback.

Yes, it contains Java for AMD64 ( [http://packages.ubuntu.com/jaunty/ubuntu-restricted-extras](http://packages.ubuntu.com/jaunty/ubuntu-restricted-extras) ) - x86 platforms don't have such a [COLOR=DimGray]feature[/COLOR] ;)

---

### Post by rjr0218 on 2009-08-05
> **credobyte said:**
> Execute this command in Terminal:
```
sudo apt-get install sun-java6-jre sun-java6-plugin

```


Ubuntu restricted extras does NOT contain Java runtime environment.

Thanks!

The information you sent to install java in ubutu worked. Again thanks!

---

### Post by oldos2er on 2009-08-05
> **credobyte said:**
> Yes, it contains Java for AMD64 ( [http://packages.ubuntu.com/jaunty/ubuntu-restricted-extras](http://packages.ubuntu.com/jaunty/ubuntu-restricted-extras) ) - x86 platforms don't have such a [COLOR=DimGray]feature[/COLOR] ;)

 I learn something new every day here! Wonder why the difference in the restricted extras packages...?

---

### Post by SoulTerror on 2009-08-06
> **credobyte said:**
> Execute this command in Terminal:
```
sudo apt-get install sun-java6-jre sun-java6-plugin

```


I used this command and now I'm stuck at this screen.

I have tried hitting enter, esc, and closing the window. When I try to close it, it tells me that a program is still being executed. Been sitting there for a few minutes now. Is there something I'm missing?

---

### Post by credobyte on 2009-08-06
```
Tab -> ENTER

```

---

### Post by SoulTerror on 2009-08-06
OMG, I'm such a noob :(

THANKS!

---

