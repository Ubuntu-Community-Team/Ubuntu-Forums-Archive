---
title: "No Sound and cant play multimedia files"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by r.sushant on 2010-03-25
Hello friends, i am new to ubuntu.
Right now i am using win7 on my laptop n interested in ubuntu. I have installed ubuntu on my pen drive... i boots normally but problem is theres no sound and i cant play even mp3 files oe any video file.... for any file type it prompts that couldent play this format.
please help.

---

### Post by cogier on 2010-03-25
If you have no sound right click on the speaker icon and make sure the "Mute" box is not set. Also check the volume is up by left clicking on the same icon.

Have you got any sound yet. Check by restaring the computer to see if you get the logon sound.

Then we can work on the MP3s

---

### Post by r.sushant on 2010-03-25
i tried restarting, there no even logon sound!
i checkd volume control also... but didnt workd!
even if i play mp3 files it prompts for codec... it cqn play only ogg but again no sound!!!

---

### Post by cogier on 2010-03-25
As you have no sound at all I would start here [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

If you get that working you can play your MP3 s by going to Applicationa>Ubuntu Software Centre. Type "rest" in the search box and install the Ubuntu Restricted files.

Hope that helps.

---

### Post by r.sushant on 2010-03-25
ubuntu software center didnt helpd...
it has option 'ubuntu restricted extras' but in that it shows, 'not available in current data'
let me have a look at the link you have given!

---

### Post by cogier on 2010-03-25
You are in the wars.

Open terminal (Applications>Accessories>Terminal) and run the following 

```
sudo apt-get update
```

That may get rid of the "not available...." message

---

