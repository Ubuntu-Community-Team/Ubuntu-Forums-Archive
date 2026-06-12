---
title: "Where do downloads land Heron 8.04"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by Chris Edgell on 2009-04-04
I have downloaded a pamphlet. Each time it downloads, I lose all on the screen besides the pamphlet (and it's long) and I can only get rid of it by shutting down the computer.  Therefore, every time I download it I see a long list (on a black background) of downloads- that list immediately disappears, but it's there long enough for me to see that I've downloaded it 8 or 10 times, but I don't know, to where.  I'd like to find them and delete, can you help me?

---

### Post by Racecar56 on 2009-04-04
If you downloaded it in Firefox, it's most probably on your desktop.

---

### Post by unutbu on 2009-04-04
Open a terminal (Applications>Accessories>Terminal) and type
```

find . -type f -mmin -10 -print
```
This will show you all the files in your home directory that have been modified in the last 10 minutes.

There are other ways of finding the downloads depending on what web browser you use. Which one are you using?

Edit: 
If you use Firefox, go to Edit>Preferences. Click the "Main" icon. In the middle of the preference dialog window you will see some options relevant to Downloading. You can set where you want downloads to be saved here.

---

### Post by Chris Edgell on 2009-04-04
Not on my desktop...

---

### Post by Chris Edgell on 2009-04-04
unutbu:  I tried to do all you said...I'm afraid my desktop is messed up.  I have a lot of repetition in my "path".  It started when I tried to make my desktop look like my Microsoft desktop.  "My Computer"  "My Documents"  "Chris", etc.  In this case I had "Home" "File Manager"  (etc.)  When I tried to separate the personal stuff from the other systems stuff, I got a lot of overlap in the files and/or folders.  So I think I have 2 or even 3 desktops floating around.  Any advise?

---

### Post by albinootje on 2009-04-04
> **Chris Edgell said:**
> Not on my desktop...

Click on ->Tools ->Downloads in Firefox (or ctrl-Y).
Then right click on your downloaded file, and choose "Open Containing Folder".

---

### Post by Chris Edgell on 2009-04-04
Ah, that worked, as I went to "Tools" and found "Downloads" I must say, when I right clicked and tried to click "Open containing folder", nothing happened.  Dropping down one category to "Go to Download Page", it will do that.....
I'm wondering if this file was downloaded into what I call the other side of my computer, or if it is only stored and available to me on this download list??

---

### Post by Racecar56 on 2009-04-04
> **Chris Edgell said:**
> Ah, that worked, as I went to "Tools" and found "Downloads" I must say, when I right clicked and tried to click "Open containing folder", nothing happened.  Dropping down one category to "Go to Download Page", it will do that.....
I'm wondering if this file was downloaded into what I call the other side of my computer, or if it is only stored and available to me on this download list??
Go to Edit > Preferences > Main.
Look at what "Save files to:" says.
[Screenshot]("http://img217.imageshack.us/img217/2074/savefilestoscreenshotde.jpg")
Go to the folder where that is, and then delete the file that is making the trouble.

---

