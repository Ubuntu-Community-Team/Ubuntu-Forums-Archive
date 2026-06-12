---
title: "I hate terminal. I can't &quot;cd to downloads&quot;"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by Iniquit-e on 2010-10-25
So i am trying to install something and it is stating that I need to open terminal and CD (change directory, I believe) to where my downloaded file is (in this case, in the default Downloads folder).

So I typed in "cd /home/downloads" and it claims no such thing exists....

Why is this so difficult? What am I doing wrong?

---

### Post by spiky001 on 2010-10-25
```
 cd /home/user/Downloads
``` try that

---

### Post by migs73 on 2010-10-25
The downloads folder is called Downloads with a capital 'D'.

---

### Post by Wicca on 2010-10-25
Unless your username is "downloads" this won't work....

Try your username in between:

cd /home/*[your username here]*/downloads or better:

cd ~/downloads

---

### Post by Jetso on 2010-10-25
All you should have to do is just ```
cd Downloads
``` it starts out in your home folder.

---

### Post by Hippytaff on 2010-10-25
> **Wicca said:**
> Unless your username is "downloads" this won't work....

Try your username in between:

cd /home/*[your username here]*/downloads or better:

cd ~/downloads
  with a capital D :-)

---

### Post by anewguy on 2010-10-25
> **Wicca said:**
> Unless your username is "downloads" this won't work....

Try your username in between:

cd /home/*[your username here]*/downloads or better:

cd ~/downloads

Yes, except capitalize the D in downloads:

cd ~/Downloads

Dave ;)

---

### Post by migs73 on 2010-10-25
> **migs73 said:**
> The downloads folder is called Downloads with a capital 'D'.

As I said , it's Capital  'D'.:)

Linux is case sensitive.

---

### Post by Wicca on 2010-10-25
Yep, you're all right. With a Huge Capital D that is.;-)

---

### Post by Jetso on 2010-10-25
You can always use ```
pwd
``` (Print working directory) to show where you are, so to speak. I believe that /home/<current user> is the default. So you wouldn't have to specify /home/user/Downloads, just "cd Downloads"

---

### Post by spiky001 on 2010-10-25
enough with the capital D

---

### Post by Hippytaff on 2010-10-25
> **Wicca said:**
> Yep, you're all right. With a Huge Capital D that is.;-)
Honestly...took me weeks to realise the case sensitive thing...very frustrating :-)

---

### Post by oldos2er on 2010-10-25
Just remember when in terminal, tab completion is your friend. [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by ArgusVision on 2010-10-25
One of the classes I teach is Basic Unix Commands. The fist slide warns that Unix is case sensitive... Linux is just as sensitive. :)

---

### Post by Old *ix Geek on 2010-10-26
> **Hippytaff said:**
> Honestly...took me weeks to realise the case sensitive thing...very frustrating :-)It was the opposite for me. Having started out on UNIX in the '80s--and we had "long file names" back then, although we didn't call them that, we just thought that was normal--when I used to have to deal with the occasional DOS/windoze box, I could *NOT* get used to the non-case sensitive, short file names. Drove me nuts! ](*,)

---

### Post by amjjawad on 2010-10-26
> **Iniquit-e said:**
> So i am trying to install something and it is stating that I need to open terminal and CD (change directory, I believe) to where my downloaded file is (in this case, in the default Downloads folder).

So I typed in "cd /home/downloads" and it claims no such thing exists....

Why is this so difficult? What am I doing wrong?


```
cd ~/Downloads
```

> **cd**: The **cd** command  will allow you to change directories.  When you open a terminal you will  be in your home directory.  To move around the file system you will use  **cd**.  Examples: 

[LIST]
[*]To navigate into the root directory, use **"cd /"** 
[*]To navigate to your home directory, use **"cd"** or **"cd ~"** 
[*]To navigate up one directory level, use **"cd .."** 
[*]To navigate to the previous directory (or back), use **"cd -"** 
[*]To  navigate through multiple levels of directory at once, specify the full  directory path that you want to go to. For example, use, **"cd /var/www"** to go directly to the /www subdirectory of /var/. As another example, **"cd ~/Desktop"** will move you to the Desktop subdirectory inside your home directory. 
[/LIST]

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by anewguy on 2010-10-26
> **Old *ix Geek said:**
> It was the opposite for me. Having started out on UNIX in the '80s--and we had "long file names" back then, although we didn't call them that, we just thought that was normal--when I used to have to deal with the occasional DOS/windoze box, I could *NOT* get used to the non-case sensitive, short file names. Drove me nuts! ](*,)

I know what you mean.  I worked with proprietery large-scale OS's with none of the limitations and was case sensitive.  Moved into minis and micros as they came around.  Also worked some with Unix in the 80's and very early 90's as well.  Windows and DOS boxes drove me nuts as well!

Dave ;)

---

### Post by everytimeref on 2010-10-26
> **Jetso said:**
> You can always use ```
pwd
``` (Print working directory) to show where you are, so to speak. I believe that /home/<current user> is the default. So you wouldn't have to specify /home/user/Downloads, just "cd Downloads"



I always thought that pwd meant Please, Which Directory?: Very polite...

---

### Post by ikt on 2010-10-26
I think it's because you didn't use capital D

but besides that, what's this?
> 
"I hate terminal."

Terminal doesn't hate you :( Where is the love?

---

### Post by 3rdalbum on 2010-10-26
Your question has already been answered, but you could also type *cd*, then a space, then drag the desired folder into the terminal. It will fill in the folder's path and you can just run the result as a command.

---

### Post by ubunterooster on 2010-10-26
> **3rdalbum said:**
> Your question has already been answered, but you could also type *cd*, then a space, then drag the desired folder into the terminal. It will fill in the folder's path and you can just run the result as a command.
:shock: That is so cool!> **spiky001 said:**
> enough with the capital D:lol:

---

### Post by Old *ix Geek on 2010-10-26
> **anewguy said:**
> I know what you mean.  I worked with proprietery large-scale OS's with none of the limitations and was case sensitive.  Moved into minis and micros as they came around.  Also worked some with Unix in the 80's and very early 90's as well.  Windows and DOS boxes drove me nuts as well!And what about those silly truncated file names: longfilename --> longfi~1 :lolflag: (I had to look this up as I couldn't actually remember any more how that went, just that it had a ~ in its name.)

When windows started supporting upper/lower case file names, I actually thought they'd finally caught up with *nix and the names were case sensitive. Wrong!

---

### Post by oldsoundguy on 2010-10-26
or you can save a lot of time and just specify the download to go to your desktop.  I started doing that a couple of years ago and found that I really don't need terminal that much.  Just do a right click on the download and grant permissions and launch in most instances.

---

### Post by ubunterooster on 2010-10-26
> **oldsoundguy said:**
> or you can save a lot of time and just specify the download to go to your desktop.  I started doing that a couple of years ago and found that I really don't need terminal that much.  Just do a right click on the download and grant permissions and launch in most instances.That leads to clutter, However you could just stick it in the home folder since you that is the terminals default location, but the way it is works best once you get used to it

---

### Post by oldsoundguy on 2010-10-26
> **ubunterooster said:**
> That leads to clutter, However you could just stick it in the home folder since you that is the terminals default location, but the way it is works best once you get used to it

Yea, if you leave that unneeded stuff on your desktop, once it is installed, trash bin for the installation file.
If I ever need to re-install, I will go get the newest version and utilize it .. and treat it the same way.
I leave my desktop bare .. the programs I use are in the panels. So I use the desktop as a temporary landing space for both downloads and uploads.  When the chore has been completed, the items are removed.

---

### Post by Jetso on 2010-10-26
> **everytimeref said:**
> I always thought that pwd meant Please, Which Directory?: Very polite...
Hey, I like that one better... I think that would work ;)

---

