---
title: "Bash PATH problem?"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by DannStarr on 2011-06-30
Ok, so I've a newly installed 64bit ubuntu, and I've just downloaded the android SDK.

I managed to run the "android command the first time round whereby I successfully downloaded android versions 2.3+

I was very clever and did this through the terminal, by going in to my android SDK directory, and then tools (for me cd /android/tools)

and then I typed android, and the gui came up..... all good.

I then decided I needed to add this directory to my path, I did some jiggery pokery here, not too much, but I cant say exactly what I did, but now, when I try to run the android command, from the correct directory all I get is the following:


```
dan@dan-HP-Pavilion-dm1-Notebook-PC:~/android/tools$ dir
adb_has_moved.txt  dmtracedump	    hprof-conv	  NOTICE.txt	     zipalign
android		   draw9patch	    layoutopt	  proguard
ant		   emulator	    lib		  source.properties
apkbuilder	   etc1tool	    mksdcard	  sqlite3
ddms		   hierarchyviewer  monkeyrunner  traceview
dan@dan-HP-Pavilion-dm1-Notebook-PC:~/android/tools$ android
android: command not found
```

I know this must be down to some kind of path error, but i'm lost as to how to correct it. I've googled all over, but every explanation seems geared towards someone with more linux knowledge than mine. Please may someone explain really simply how I fix this? thanks

---

### Post by seawolf167 on 2011-06-30
If you are in the directory with the binary, to run it type

```
./android
```else you can add that path to your ~/.bashrc file if you want, i.e.

```
gedit ~/.bashrc
```add

```
PATH="/my/path:$PATH"
```then restart your terminals

---

### Post by DannStarr on 2011-06-30
Thanks Seawolf :)

1 more Q:

When I open the bashrc file, and I need to add 

```
PATH="/my/path:$PATH"
```

I dont see anywhere a reference to PATH, so does this mean I can just enter this anywhere within the file?

---

### Post by seawolf167 on 2011-06-30
You can just add this line at the end. You don't actually need to close your terminal and re-open afterwords, you can just force bash to re-read the file with the following command

```
exec bash
```

---

### Post by DannStarr on 2011-06-30
You are awesome. This now works, thanks very much :)

---

### Post by seawolf167 on 2011-06-30
No problem - glad its working :) Don't forget to mark the thread as solved.

---

