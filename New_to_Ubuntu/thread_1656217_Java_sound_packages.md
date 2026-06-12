---
title: "Java sound packages"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by Chrissd on 2010-12-30
Hi, I'm trying to install the sound packages from: [http://java.sun.com/products/java-media/sound/soundbanks.html](http://java.sun.com/products/java-media/sound/soundbanks.html)

I have downloaded and extracted the package I want, but the readme says: 

1. If you installed the Java 2 SDK, change directories to 
   <install-dir>/jre/lib/audio *otherwise*

   If you installed the Java 2 RE, change directories to 
   <install-dir>/lib/audio*

   The <install-dir> should be where you installed your
   copy of the Java 2 SDK.


Now, I have a standard xubuntu on here, I have no idea what my install directory would be. I think I have iced-tea or something for me java/jre.

Can anyone tell me where I might find the folder I would need?

Thanks

---

### Post by Chrissd on 2010-12-31
Can anyone help me with this please?

---

### Post by lykeion on 2011-01-01
The soundbanks for the Java Sound API is used when you are programming some MIDI software in Java. To be able to program in Java you need to have the Java JDK installed.
When you say that you are not sure what Java you have installed it makes me wonder what you are trying to achieve here, so...

What do you need the soundbanks for?

---

### Post by Chrissd on 2011-01-03
For TuxGuitar, apparently they improve the sound.

---

### Post by lykeion on 2011-01-04
Okay I see. 
Found [this]("http://arkold.com/811-java-sound-synthesizer-and-tuxguitar-on-karmic") page where the instructions to use Java sound banks with TuxGuitar is just move the .gm file of the Java sound banks to the lib-folder of Java JRE.

1. Download Java sound banks
```
wget http://java.sun.com/products/java-media/sound/soundbank-deluxe.gm.zip
```
2. Unpack it:
```
unzip soundbank-deluxe.gm.zip
```
3. Move it to the lib folder (this supposes you have the default OpenJDK Java JRE installed):
```
sudo mv soundbank-deluxe.gm /usr/lib/jvm/java-6-openjdk/jre/lib
```

---

### Post by Chrissd on 2011-01-09
Massive thanks.

Appreciated the help.

---

