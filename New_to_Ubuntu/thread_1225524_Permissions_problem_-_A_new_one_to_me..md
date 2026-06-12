---
title: "Permissions problem - A new one to me."
date: 2009-07-28
forum: New to Ubuntu
---

### Post by brawd on 2009-07-28
I installed QCAD a couple of weeks ago and have just completed a sequence of drawings, they are ready to send to the workshops.

I went to Places - Documents and double clicked to open one of my files but when it opened it told me I didn't have permission to open it. But I am the one who drew it, so why can't I open it.

Then I found out that there seems to be a clone of the folder containing my drawings. I get there by Places-Home Folder-Documents but once again I can't open them by double clicking or right clicking and taking 'Open with...'. I get the 'Please check permissions.' message.

After the panic and two heart attacks I discovered that if I open QCAD first, select 'File' and look at the files listed as history THEN I can open them.

But what happens 2 years down the road when I have 150 files. How will I open the older files?

I hate the whole idea of permissions.
I want to be boss of my computer. A computer is just a toolbox to me but inside mine just now is an enemy.

Any suggestion please?
Any and all help appreciated even if I don't know how to mark a thread solved or say Thank you.

regards,

brawd.

---

### Post by Jimleko211 on 2009-07-28
```

gksudo nautilus

```

Then browse to your file.  Right click.  Go to Properties.  Permissions.  Then, in one of the empty boxes of user groups, select the name you use to log in.  Then set the other field to Read and Write.

---

### Post by brawd on 2009-07-28
That didn't work I'm afraid.

While I was gksudo'ing I did a right click on one of my files and selected QCAD to open it.

Same fault message -'Please check permissions'


brawd.

---

### Post by credobyte on 2009-07-28
Try:
```
sudo chown -R user:user /path_to_files/

```

Don't forget to replace user:user with your username !

---

### Post by brawd on 2009-07-28
Ahh, but the path is the tricky bit.

When I'm at the desktop I click on Places, then take Documents, then a new window opens up and I take a folder called qcad. This opens up another window and I take the folder called Engine1.

So can you tell me what my path is please?

brawd.

---

### Post by credobyte on 2009-07-28
Not 100%, but .. :
```
$HOME/Documents/qcad/Engine1
```

---

### Post by brawd on 2009-07-28
Nothing doing again I'm afraid. I still get the same message.

No wonder I couldn't get a path command to work for me - I've never seen the $ sign used in a path only '/'.

brawd.

---

### Post by brawd on 2009-07-28
I wonder if QCAD has a default setting for it's saved files.

Perhaps I should backup the files, reinstall QCAD and stick the files in the default folder.

I think I'll try that and see how I get on.

If it fails again I can try bumping this back to the top.

Thanks to all.

brawd.

---

### Post by credobyte on 2009-07-28
> **brawd said:**
> Nothing doing again I'm afraid. I still get the same message.

No wonder I couldn't get a path command to work for me - I've never seen the $ sign used in a path only '/'.

brawd.

$HOME is equal to /home/user/ and it doesn't make any difference when executing commands in terminal.

---

### Post by brawd on 2009-07-28
Thanks for the info on paths Credobyte.

Well I tried uninstalling QCAD, and did an update and reboot as well.

Then I reinstalled QCAD and I'm in exactly the same position as before.
It went to the 'CAD' folder thingee I made in Applications and the paths I set up when I first installed it were once more in use.

It's been too long a day to do any more tonight.

Tomorrow I might set up another computer and install it there and see what happens.

Goodnight all and thanks for your help,

brawd,
(a very tired and worn out draughtsman)

---

### Post by brawd on 2009-07-29
Got this from QCAD forum, posted by 'webpilot'.





Joined: 21 Feb 2009
Posts: 1
Location: on this Earth
	
PostPosted: Sat Feb 21, 2009 1:14 am    Post subject: Please check the permissions ... isn't really the error 	Reply with quote
Hi all,

I am running (trying to run?) QCad version 2.0.5.0 (Community Edition) on Ubuntu Hardy Heron.

The problem is with Nautilus 2.22.5.1.

If I click on a saved .dxf file created with QCad from a former session, QCAD launches, but I get this error message



You can see the file location error, namely,

/home/fde/file:/home/fde/myDrawings ...

To cure this for now,

    * I right mouse clicked on a .dxf file,
    * left mouse clicked on 'Open with Other Application',
    * chose 'Use a custom command'
    * I typed in the word, qcad
    * left mouse clicked on Open

Now when I left mouse click on a .dxf file, QCad launches and I see the drawing.

Cheers

---

### Post by webpilot on 2010-01-14
Hi brawd, 

That was me over there.  

I'm a little late to say, but I'm glad you found my solution useful.

Cheers

**PS**

I posted over there an image of the error message one gets, but the link keeps getting broken.  It reads:

> 
Warning 
 
Cannot open the file 
/home/fde/file:/home/fde/myDrawings/QCad/second.dxf 
Please check the permissions. 
 
OK


---

