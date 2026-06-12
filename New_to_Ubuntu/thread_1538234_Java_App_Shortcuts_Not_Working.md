---
title: "Java App Shortcuts Not Working"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by trentscott on 2010-07-24
I have a Java app that I downloaded (the .jnlp source files is in my home folder). When I run the program, it places a shortcut on my desktop with the name (jws_app_shortcut_1280012345798.desktop) but it isn't actually a clickable icon. It looks like a file with information in it (link to source file, application title, date, etc.). Is there any way I can make it an actual icon?

---

### Post by leef on 2010-07-24
can you open the .desktop file as text and post it's contents here?

---

### Post by KdotJ on 2010-07-24
Is the .jnlp all you have? No JAR file? I'm not well experienced with JNLP files but don't they have to be accessed via a web browser?

---

### Post by trentscott on 2010-07-26
I'm able to access the .jnlp using Sun Java Web Start (installed separately) not OpenJDK. The program .jnlp files are in my 'Downloads' folder. Here's the .desktop file that appeared on my desktop:

```

[Desktop Entry]
Version=1.0
Type=Application
Icon=/home/trenton/.java/deployment/cache/6.0/48/1889bfb0-4965f0e2.ico
Comment=OANDA fxGame GUI
Terminal=false
Categories=Applications;OANDA fxGame
Name=OANDA fxGame
Exec=/usr/lib/jvm/java-6-sun-1.6.0.20/jre/bin/javaws -localfile /home/trenton/.java/deployment/cache/6.0/19/5d393513-61974f85
Encoding=UTF-8


```

Any thoughts?

---

### Post by trentscott on 2010-07-27
bump

---

### Post by MuddBuddha on 2010-11-07
Did you mark the jnlp as executable? 

(under permissions)

---

