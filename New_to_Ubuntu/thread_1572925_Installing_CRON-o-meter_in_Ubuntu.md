---
title: "Installing CRON-o-meter in Ubuntu"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by greenleaves123 on 2010-09-11
I already read this: [How to install CRON-o-meter]("http://ubuntuforums.org/showthread.php?t=761095"), but I still can't get it to work. At the end of the path, there is java, but I don't have java in that folder. 

I tried to download java, but I couldn't figure it out. Can someone please post how to install and open the CRON-o-meter step by step for me? Has the instructions changed sinced 2008?

---

### Post by gmargo on 2010-09-12
If you are using Ubuntu 8.10 Intrepid, you should think about upgrading since 8.10 no longer gets security updates.

Anyway, here's a simple way to get CRON-o-meter working on 8.10 Intrepid.  First, open a terminal window since we'll do everything else on the command line.

Install Java.  There are several choices, the sun versions, the openjdk versions.  The JREs (runtime environment) or JDKs (development kit). Let's try the openjdk runtime version 6:
```

sudo aptitude -V install openjdk-6-jre

```Download the CRON-o-meter release, which you probably already have.  Put it in a handy directory.  Unzip it.
```

mkdir $HOME/cronometer
cd $HOME/cronometer

wget http://sourceforge.net/projects/cronometer/files/cronometer/0.9.7/CRONoMeter-0.9.7.zip/download

unzip CRONoMeter-0.9.7.zip

```Download the linux startup script in the same directory.
```

wget http://spaz.ca/cronometer/cronometer.sh

chmod +x cronometer.sh

```Now start CRON-o-meter with this command:
```

./cronometer.sh

```This works for me under 8.10 Intrepid.

---

### Post by greenleaves123 on 2010-09-12
Thanks so much for the instructions! It worked! Yay!

Thanks for the tip about needing to upgrade too. I will download the latest version soon. I was wondering why I never got updates anymore. LOL

---

### Post by Uubo on 2011-02-27
Tried, didn't work.  Ubuntu 10.10.

```
./cronometer.sh
cd: 10: can't cd to CRONoMeter.app/Contents/Resources/Java/
```


cronometer.sh code:
```
cd "CRONoMeter.app/Contents/Resources/Java/"
java -cp cronometer.jar:jcommon-1.0.10.jar:jfreechart-1.0.6.jar:swingx-0.9.3.jar:cronometer.jar:usda_sr22.jar:crdb_004.jar:docs.jar ca.spaz.cron.CRONOMETER
```

No item named CRONoMeter.app exists after unzipping the MacOS version of CRONOMETER-0.9.7.tar.gz

Followed instructions on top 3 google hits for "ubuntu cronometer"

What am I missing?

---

### Post by gmargo on 2011-02-27
> What am I missing?

[http://sourceforge.net/projects/cronometer/files/cronometer/0.9.7/](http://sourceforge.net/projects/cronometer/files/cronometer/0.9.7/)
CRONOMETER-0.9.7.tar.gz is the source code.
The .zip file (was called CRONoMeter-0.9.7.zip but is now called CRONoMeter-0.9.7-MacOSX.zip) is the compiled binary.

So download and unzip the .zip file, or figure out how to compile the source.

---

### Post by Uubo on 2011-02-27
Thanks!  It works now.

I had to do slightly different than was recommended above though.
After unzipping "CRONoMeter-0.9.7-MacOSX.zip"  (must say this or else, as stated above, is source code)


modify "chronometer.sh" so it reads:
```
cd /wherever/you/unzipped/the/file
cd "CRONoMeter.app/Contents/Resources/Java/"
java -cp cronometer.jar:jcommon-1.0.10.jar:jfreechart-1.0.6.jar:swingx-0.9.3.jar:cronometer.jar:usda_sr22.jar:crdb_004.jar:docs.jar ca.spaz.cron.CRONOMETER
```

replace /wherever/you/put/unzipped/file with ... wherever you unzipped the file.
For me it was:
cd /home/johndoe/cronometer/CRONoMeter-0.9.7-MacOSX

place "cronometer.sh" into the folder you just extracted from "CRONoMeter-0.9.7-MacOSX.zip"
then it worked for me

---

