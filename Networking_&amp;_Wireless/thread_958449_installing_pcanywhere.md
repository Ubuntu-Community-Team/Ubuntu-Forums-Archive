---
title: "installing pcanywhere"
date: 2008-10-25
forum: Networking &amp; Wireless
---

### Post by timczer on 2008-10-25
I am having issues installing pcanywhere.  I have read a couple of threads but could not get it to work. 

 During install I get a JVM not found error each time.  

I have run > sudo update-alternatives --config java

and chosen >  /usr/lib/jvm/java-6-sun/jre/bin/java from the choices.  

I run > sudo java -jar SetupLinuxMac.jar

and get the above error.  All the symlinks seem to point to the location of java.  I have tried > sudo /usr/lib/jvm/java-6-sun/jre/bin/java -jar SetupLinuxMac.jar, as well, with the same result.

How do I get the pcanywhere installer to find by JVM install?

---

### Post by jlisek on 2008-10-25
Hi,

Well, try [www.gotodevice.com](www.gotodevice.com) this is no easy java hack remote administration, but a full linux binary (download easy to install deb files, also x64 support if needed)!

More features than pcanywhere and fully cross-platform!:KS

Best regards

John

---

### Post by timczer on 2008-10-25
Unfortunately, I need this for work.  The sites I need to contact all have pcanywhere hosts running, so I need to connect via pcanywhere.

---

### Post by timczer on 2008-10-26
Finally got this figured out.  As others have had to do, I finally had to install java 1.4.2 to get pcAnywhere to install.

I wonder why some have had no issue getting it to install with java-6-sun and others (such as myself) have had to use an older version of java to get it to install.

---

### Post by Law506 on 2008-11-11
I installed the older version of Java and got a little further than before.  I am trying to use 11.5, does this even work with Ubuntu?  I tried using WINE but that was hasn't proven to work yet either with this.

Any suggestions?

---

### Post by EyesOnFire on 2010-09-20
Additionally, you could download this PCAnywhere Client and run it under WINE:

[http://www.softpedia.com/get/Internet/Remote-Utils/pcAnywhere-Remote-Control.shtml](http://www.softpedia.com/get/Internet/Remote-Utils/pcAnywhere-Remote-Control.shtml)

The only thing I had to add manually was the MSVBVM60.DLL from an XP install (Found in System32). No installation necessary. Just the executable, its DLL and the MSVBVM60.DLL.

---

### Post by burebista on 2010-10-04
try this:
1. install j2sdk1.4.2_18 in /usr/lib/jvm/j2sdk1.4.2_18
2. run from console:
$sudo -s
$/usr/lib/jvm/j2sdk1.4.2_18/jre/bin/java -jar SetupLinuxMac.jar
and use the gui installer, it works 100%.
3. run from console
$sudo gedit /usr/bin/pcAnywhere
4. replace this line:
java -Djava.CPR.dirs=$PCAPATH -jar /usr/local/lib/pcAnywhere/vprcd.jar
with
/usr/lib/jvm/j2sdk1.4.2_18/jre/bin/java -Djava.CPR.dirs=$PCAPATH -jar /usr/local/lib/pcAnywhere/vprcd.jar
5. save the file /usr/bin/pcAnywhere
6. run from Alt-F2 or from Terminal "pcAnywhere".

That's it.

---

