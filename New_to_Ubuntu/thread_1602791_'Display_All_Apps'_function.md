---
title: "'Display All Apps' function?"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by WithoutAClue on 2010-10-21
I'm new to Linux and have no idea what to even call this...  I tried a few searches, but...  Anyway - in Mac's soon to be released OS X Lion there will be an app called "Launchpad" (different than Ubuntu's) that will list every app on your computer in the form of a desktop icon - something that is being carried over from the iPhone and iPad.  
For absent minded people like myself who often forget exactly what has been installed, this would be a God send.  Anything comparable available for Ubuntu???

---

### Post by pvonbert on 2010-10-21
Very easy, but you’ll get a long list!!!
Open: System; Synaptic Package Manager, and click on Status and select Installed.
At the bottom of the window you get the total of packages listed, installed (the same number) and how many are broken or need upgrade or removal.
In my case I got 'only' 2215 packages, a long list indeed. And all open source and free.

---

### Post by beew on 2010-10-21
Or in the terminal type 

```
dpkg -l | less
```

You will get an alphabetical listing of everything installed, the "| less" option is for you to be able to scroll the list up and down, otherwise you will only see the last page.

---

### Post by Zzl1xndd on 2010-10-21
> **pvonbert said:**
> Very easy, but you&#8217;ll get a long list!!!
Open: System; Synaptic Package Manager, and click on Status and select Installed.
At the bottom of the window you get the total of packages listed, installed (the same number) and how many are broken or need upgrade or removal.
In my case I got 'only' 2215 packages, a long list indeed. And all open source and free.

I don't think this is really what WithoutAClue is looking for. Unfortunately I am not sure if there is (although if not I am sure someone will make one) however I don't think its really a problem stock Ubuntu needs solved.

My Better half is an Apple user and she is looking forward to this feature because her doc is cluttered with Apps, many she doesn't use often but enough that she doesn't want to dig thorough her Applications folder so for her great new feature.

As Most applications people use in Ubuntu are listed under Applications there isn't as much of a need.

---

### Post by WithoutAClue on 2010-10-21
Thank you for the quick reply pvonbert.

I asked after reading a plug for 'Lion', but after a little consideration I realized there are much more organized (read *better*) ways of doing the same thing with custom stacks, dock folders, etc. already available on my computer...  Thanks again anyway!

Thank you also beew and tweakedenigma, apparently you both were posting while I was typing...

---

