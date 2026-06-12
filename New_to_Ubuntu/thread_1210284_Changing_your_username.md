---
title: "Changing your username?"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by FoxFireX on 2009-07-11
Yeah I accidently spelled my username wrong, possible to change?

I see an option in this ubuntu tweak thing I downloaded, that says Current user information..


Username
Home directory


not sure if there would be a more official way to do it, don't wanna screw anything up ya know?


PS, could anyone here remote connect to me and show me how to install a metacity and gtk theme?

---

### Post by elliotn on 2009-07-11
Ja

---

### Post by FoxFireX on 2009-07-11
ich verstehen nicht...Können dich mir sagen, wie?

Yeah it won't let me change it in ubuntu tweak though so.

---

### Post by unutbu on 2009-07-11
To change your username:
[list]
[*] The safe way: Click System>Admin>"Users and Groups". Create the new user. Be sure to add "admin" privileges for the new user. Then copy over any data you have from the old user to the new user's account. Do not copy over configuration files (see below for the reason.) Redo all your GNOME configuration settings.
[*] The quick but prone to error way:
Open a terminal (Applications>Accessories>Terminal) and type
```

sudo usermod --login NEWNAME --home /home/NEWNAME -m OLDNAME
sudo groupmod --new-name NEWGROUP OLDGROUP

```

Change NEWNAME to the desired new username
Change OLDNAME to the old username

The above command copies all the files in your current home directory and moves them to the new user's home directory.

Note however that OLDNAME may still be present in the contents of certain configuration files. For instance, if you told GNOME to use a certain image /home/OLDNAME/Pictures/background.jpg as your background image, then even after you move your files to the /home/NEWNAME, GNOME will still try to find the background image in /home/OLDNAME. Since that directory will cease to exist, your configuration file will be broken. 

If you use WINE, then you'll have even more things to fix, since WINE makes symlinks to files in /home/OLDNAME, so you'll have a couple of symlinks to fix too.

[/list]

---

### Post by FoxFireX on 2009-07-11
Hey if I assigned the new user to the main group of root, would that make it so that I would have just as much authority as root?

---

### Post by unutbu on 2009-07-11
The correct way to give a user root privileges is to make the user a member of the "admin" group. The way to do that using the GUI is to click the "User Privileges" tab and enable the line that says "Administer the system".

---

### Post by sisco311 on 2009-07-11
> **unutbu said:**
> 

...

```

sudo usermod --login NEWNAME --home /home/NEWNAME **--gid NEWNAME** -m OLDNAME
```

...



rather than changing the user's initial login group (btw it's not possible if the group doesn't exist) one should rename his/her primary group:
```
sudo groupmod -n newname oldname
```

---

### Post by unutbu on 2009-07-11
> **sisco311 said:**
>  (btw it's not possible if the group doesn't exist) 


Yes, that's true. Thanks for the correction!

---

### Post by FoxFireX on 2009-07-11
What main group should I make it in? admin? users? root?

---

### Post by unutbu on 2009-07-11
Before making a new user, click the "Manage Groups" button. Add a new group. Make the group name the same as your new username (NEWNAME).

Then click "Add User" and make the "main group" of the new user = NEWNAME.

---

### Post by FoxFireX on 2009-07-11
Erm, There is not a NEWNAME group in the drop down menu, I'm doing it the system - administration - manage users groups - new user way.

---

### Post by unutbu on 2009-07-11
Did you make a new group called NEWNAME? (I just call it NEWNAME since I don't know what your new username really is...)

---

### Post by FoxFireX on 2009-07-11
Oh now I get you, how do I make a new group?


EDIT, nvm i got it :D

EDIT2: uh it keeps saying that the username already exists.. but It doesn't atleast I don't see it in the users..

---

### Post by FoxFireX on 2009-07-11
bump

---

### Post by LewRockwell on 2009-07-11
> **FoxFireX said:**
> bump

Re: Bump...

I think those assisting you took your last post to mean that you had gained enough knowledge to proceed on your own for awhile.

Also note: On this forum(and many others as well) it is customary and courteous to refrain from bumping a thread until it has reached the end of the second or third page of listed threads in that area/section. One might associate this restraint as the same general respect given to others waiting in line at the theater, market, or amusement park.

With respect to your original question/topic in THIS thread, most will find extreme pleasure in the discovery of each and every area of a new and fascinating open source operating system. This is a process that most find both fulfilling and invigorating. Yes, the old dog can learn new tricks.

Feel free to experiment with your freshly installed operating system confident in the complete knowledge that if you do something that makes it "buggy" you can always re-install and continue on. If you really want to open the hood and get your hands greasy then you might consider installing a micro distro like Damn Small Linux or a mini distro like Puppy Linux(both of which can be torn-apart, hacked-on, and then re-installed repeatedly as you gain confidence in your abilities and processes).

.

---

### Post by FoxFireX on 2009-07-11
DSL sucks, I dont need a micro distro, I appreciate the advice you gave me on bumping threads, but quit bothering me. If you want to tell me something message me. Otherwise quit making pointless posts to my questions. You're not a moderator quit acting like one. Is that the only reason you posted? To tell me that I shouldn't bump threads unless they are past page 2? Wow. Now I can see where you get your 12 posts a day.


EDIT: I will be back later to check for answer I have to go somewhere real fast.

---

### Post by unutbu on 2009-07-11
Go back and click the "Manage Groups" button.
Delete the NEWNAME group.
Then click the "Add User" button.
Fill out the forms, but do not fill in anything under the "Advanced" tab. The GUI will create the main group for you.

---

### Post by LewRockwell on 2009-07-11
> **FoxFireX said:**
> DSL sucks, I dont need a micro distro, I appreciate the advice you gave me on bumping threads, but quit bothering me. If you want to tell me something message me. Otherwise quit making pointless posts to my questions. You're not a moderator quit acting like one. Is that the only reason you posted? To tell me that I shouldn't bump threads unless they are past page 2? Wow. Now I can see where you get your 12 posts a day.

My threads and posts are directed to the community as a whole even when I address one post in one thread on one forum.

Reason and logic prevail, and your thin skin doesn't change that...perhaps when you're fifty you'll be over that phase...

.

---

