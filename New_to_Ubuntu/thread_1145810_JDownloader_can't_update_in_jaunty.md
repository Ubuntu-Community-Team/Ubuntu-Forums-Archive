---
title: "JDownloader can't update in jaunty"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by SuperBo on 2009-05-02
I make a clean Jaunty install and I download jDownloader.
But when I run java update there is a problem
```
Starting...Current Date:Sat May 02 11:56:09 ICT 2009
2009-05-02 11:56:09:Update Downloadmirrors
2009-05-02 11:56:11:Updateserver: http://update3.jdownloader.org/nupd/ (-1%)
2009-05-02 11:56:11:Updateserver: http://update2.jdownloader.org/bin/ (-1%)
2009-05-02 11:56:11:Updateserver: http://update1.jdownloader.org/bin/ (-1%)
2009-05-02 11:56:12:OS Filter: /tools/windows/unrarw32/unrar.exe
2009-05-02 11:56:13:OS Filter: /tools/windows/unrarw32/cygwin1.dll
2009-05-02 11:56:13:OS Filter: /tools/mac/unrar

End Webupdate
/home/superbo/JDownloader/updateLog.txt
Local: /home/superbo/JDownloader
Start java -jar -Xmx512m JDownloader.jar in /home/superbo/JDownloader
May 2, 2009 11:56:14 AM - SEVERE [jd.utils.JDUtilities$4(write)] -> java.lang.NullPointerException
May 2, 2009 11:56:14 AM - SEVERE [jd.utils.JDUtilities$4(write)] -> 	at jd.config.DatabaseConnector.shutdownDatabase(DatabaseConnector.java:234)
May 2, 2009 11:56:14 AM - SEVERE [jd.utils.JDUtilities$4(write)] -> 	at jd.update.Main.main(Main.java:286)
ERORR null

```
:confused::confused:

---

