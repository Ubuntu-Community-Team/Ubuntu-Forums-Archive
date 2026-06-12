---
title: "i cant get firefox to open"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by aszxcv on 2010-03-28
it was working then i downloaded sh file to install vettle program that lock my system  up so i had to restart my system unexpectedly.  

i restarted system but firefox wont open now. i can  see prompt do you want to "start a new session" or "restore an old session". i click  both   prompts but firefox just wont open.  google chrome my other browser   does open but it close when i browse a few links.  so i have two browser that wont let me  browse to websites. i am using my windows vista to post this   thread.

i tried prompt  killall firebox-bin  but nothing works . 

i am using ubuntu 8.04

---

### Post by stlsaint on 2010-03-28
in terminal run:
```
killall firefox
``` 
(minus the -bin part from your last command)
then try to open firefox again.

---

### Post by xumuk37 on 2010-03-28
It seems not to be a browsers issue if more then one do the same... What it does? Just closes clicking some link? post the script you ran before, may be problem is there...

---

### Post by cgroza on 2010-03-28
Find a way to uninstall vettle.

---

### Post by aszxcv on 2010-03-28
> **stlsaint said:**
> in terminal run:
```
killall firefox
``` 
(minus the -bin part from your last command)
then try to open firefox again.

 I tried that already and  prompt i got back was   > firefox: no process killed

I never did get vettle installed so i just deleted sh files.

I am a novice linux user.  Since i pretty much cant solved problem myself,  I  will have to go back to windows until i get problem fixed hopefully from help here

---

### Post by lovinglinux on 2010-03-28
First, try to delete the cache files under ~/.mozilla/firefox/<yourprofile>/cache

If that doesn't help, then start Firefox with the following command:

```
firefox -P
```

It will load the Profile Manager. Don't start the default. Create a new profile instead. If it works, then you could simple delete your old profile folder or could try to determine the culprit. Keep in mind that deleting your entire profile will also delete bookmarks, passwords, preferences, extensions, cookies and so on.

---

