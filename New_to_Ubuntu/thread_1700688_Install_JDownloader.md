---
title: "Install JDownloader"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by faviouz on 2011-03-05
Hello,

I would like to download and install JDownloader in Ubuntu 10.10 but I am having some trouble with it. I've only been able to download it from the Ubuntu Software Center which doesn't work. Nothing happens when I try to open it. I purged, removed and re-installed it a couple of times but it didn't fix it.

As for other install methods, I think I've tried most of them. The [download page at JDownloader]("http://jdownloader.org/download/index") offers 2 mirrors, one of which is broken and the other works the same as the case above. There's also a quick note under the download locations which I've tried but did not succeed. I searched around for other download alternatives but most websites redirect to the [official download page at JDownloader]("http://jdownloader.org/download/index").

Not so long ago I had it running in Ubuntu but I removed it eventually. Now that I want to install it again, I can't possibly install it. What are your suggestions?

---

### Post by jeremyjjbrown on 2011-03-05
Try this in a terminal.

```
sudo add-apt-repository ppa:jd-team/jdownloader
```

```
sudo apt-get update
```

```
sudo apt-get install jdownloader
```

---

### Post by faviouz on 2011-03-05
Hi, thanks for replying.

I've tried that before and it didn't work. However I gave it another go. The results are the same.

---

### Post by jeremyjjbrown on 2011-03-05
Perhaps you want to contact the jdownloader dev team.

---

### Post by papibe on 2011-03-05
Do you have Java installed?

The method that has worked for me is to download and run the script (jd.sh) that is available at their site.

Regards.

---

### Post by jbiggs12 on 2011-03-05
I had difficulties with JDownloader too... I can't remember exactly what it was that fixed it, but what you describe is exactly what was happening. After clicking multiple times it still wouldn't appear no matter what I tried. Have you tried launching it from the terminal (type jdownloader) and seeing the output that it spits out?

---

### Post by faviouz on 2011-03-06
Yes, I do have Java installed.

And I've tried running it from the terminal before. The output is as follows:

```
JAR
00s.002 - FINEST [jd.utils.JDUtilities(getJDClassLoader)] -> Create Classloader: for: /home/fabio/.jdownloader
00s.042 - FINEST [jd.JDClassLoader(<init>)] -> rootDir:/home/fabio/.jdownloader
/home/fabio/.jdownloader
 null
00s.504 - FINER [jd.config.DatabaseConnector(<init>)] -> Loading database
00s.504 - FINER [jd.config.DatabaseConnector(checkDatabaseHeader)] -> Checking database
00s.522 - SEVERE [jd.controlling.JDLogger(exception)] -> SEVERE Exception occurred
java.sql.SQLException: Database broken!
	at jd.config.DatabaseConnector.<init>(DatabaseConnector.java:76)
	at jd.utils.JDUtilities.getDatabaseConnector(JDUtilities.java:856)
	at jd.config.SubConfiguration.<init>(SubConfiguration.java:77)
	at jd.config.SubConfiguration.getConfig(SubConfiguration.java:106)
	at jd.update.WebUpdater.getConfig(WebUpdater.java:74)
	at jd.update.Main.main(Main.java:121)
00s.539 - SEVERE [jd.utils.JDUtilities(getDatabaseConnector)] -> Database broken! Creating fresh Database
00s.540 - FINER [jd.config.DatabaseConnector(<init>)] -> Loading database
01s.213 - FINER [jd.config.DatabaseConnector(<init>)] -> No CONFIGURATION database found. Creating new one.
01s.229 - FINER [jd.config.DatabaseConnector(<init>)] -> Starting database wrapper
/home/fabio/.jdownloader/config/WEBUPDATE.cfg (No such file or directory)
{}

/home/fabio/.jdownloader/config/PACKAGEMANAGER.cfg (No such file or directory)
{}

java.awt.HeadlessException
	at java.awt.GraphicsEnvironment.checkHeadless(GraphicsEnvironment.java:173)
	at java.awt.Window.<init>(Window.java:437)
	at java.awt.Frame.<init>(Frame.java:419)
	at java.awt.Frame.<init>(Frame.java:384)
	at javax.swing.JFrame.<init>(JFrame.java:174)
	at jd.update.Main.initGUI(Main.java:459)
	at jd.update.Main.main(Main.java:129)
ERROR null

```

---

