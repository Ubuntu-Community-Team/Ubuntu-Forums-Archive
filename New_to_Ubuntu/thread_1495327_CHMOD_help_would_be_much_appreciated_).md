---
title: "CHMOD help would be much appreciated :)"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by mark01 on 2010-05-28
Hey all, Im not so new to Ubuntu but Im learning :) I have a dedicated laptop for learning new stuff so Im using it as a springboard to new horizons.

Anyway I cannot find any coherent (to me atleast), understandable information on CHMOD. I recently installed LAMPP as SU. As a result I cannot write to my htdocs folder.

I understand by example and as such just a command for what I want to do will be sufficient:)

OK I have LAMPP installed to /opt/lampp/ and my username is Mark. I am pulling my hair out as this simple mistake is halting my progress.
Cheerio, Mark :)

---

### Post by wannabegeek on 2010-05-28
hi,
there are more knowledgeable people than me, but perhaps I can get you started...
next time use $sudo   for temporary root access...
first go to the directory where the trouble is but not inside the dir.
```
ls -l
``` 
you will see the permissions   drwxrxwrxw
                                            dir read write execute --owner
                                          then group and the last three are public
you should see something where the public and/or group are not read enabled

try backing up one dir, $cd ..   then use below command where  directoryname is the name of the directory
```
sudo chmod 755 directoryname
```

---

### Post by mark01 on 2010-05-28
Thanks for your input  :) I got it sorted :)

---

### Post by Ozymandias_117 on 2010-05-28
You have several options. I'm not sure which would be the best in this situation though, I would usually suggest option 1 just to make sure your computer stays secure.

Option 1. Use sudo
Whenever you need to modify stuff in that folder, you can use either ```
gksu nautilus
``` or ```
gksu gedit *file*
```

Option 2. Make yourself the owner
Use chown to make you the owner of it, this way you should have more security than option 3, while retaining the ability to modify it as your user. ```
sudo chown -R user:group /opt/lampp
```

Option 3. Allow anyone and everyone to mess with it. THIS IS A BAD IDEA
You can use chmod to allow everyone to do anything to it. 1 is read, 2 is write and 4 is execute, so read/write would be 1 + 2 = 3 everything would be 1 + 2 + 4 = 7. So **I HIGHLY ADVISE AGAINST DOING THIS I'M ONLY TRYING TO EXPLAIN IT'S USAGE FOR YOUR REFERENCE** ```
sudo chmod 777 /opt/lampp
``` so the 777 means everyone can do anything (Remember, read write and execute is 7). The first number is what the owner of the file can do to it. The second number is what the group the file is in can do to it and the third number is for anyone who doesn't fit into those two groups.

---

### Post by mark01 on 2010-05-28
I used CHOWN to sort it out, I will keep this as a reference, thanks :) Mucho appreciated :)

---

