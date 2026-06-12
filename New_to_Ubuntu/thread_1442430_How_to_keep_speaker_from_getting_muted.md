---
title: "How to keep speaker from getting muted?"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by Chuck_N on 2010-03-30
Using 9.10. Every time I bootup, sound is Muted and I have to go to the Speaker symbol at top-right and turn it on. Where is the default changed?

---

### Post by yetiman64 on 2010-03-31
Hi,

Here is a thread link (marked as solved) that appears to be a very similar problem to yours. Hope this helps you.

[http://www.uluga.ubuntuforums.org/showthread.php?p=8969595](http://www.uluga.ubuntuforums.org/showthread.php?p=8969595)

---

### Post by Chuck_N on 2010-03-31
[COLOR=Lime]I would love to try that, but don't understand how.....[/COLOR]

Audio mute fix
Works everytime for me,
This issue may be a problem in pulseaudio. I managed to get it to work as expected by replacing the line

load-module module-device-restore

in /etc/pulse/default.pa with

#load-module module-device-restore

Now set audio where you like and log-out on log-on to make
sure of fix.

---

### Post by yetiman64 on 2010-03-31
> [COLOR=Lime]I would love to try that, but don't understand how.....[/COLOR]That's ok Chuck_N. 

Firstly you should go to Applications (at the top of your screen), > Accesories > click on Terminal.

Type in (or you can copy and paste in, its easier and more accurate)

```
gksudo gedit /etc/pulse/default.pa
```Enter your user password when prompted to.

That will open the file to be changed in a root text editor (needed).

Scroll down or find the line 

> load-module module-device-restoreInsert the cursor at the very start of the line and then on the keyboard hold down the Shift key and press 3 (once). This inserts a # which is used to comment out or "deactivate" this line.

Press the Save button in the editor, and then close all windows.

Set your volume to where you want it, then Restart your machine (logout is suggested in the instructions, but either are good).

When you get back to your desktop check to see if your volume is ok, if it is then it should be fixed. If not, its quite easy to reverse this process with no damage done.

Oh, and if you can, try to use the quote tags at the top of the reply "editor" when copying in text as you have done. However I will say that your copying the text helped me greatly here - thanks.

Good Luck, 
Nev

---

### Post by Chuck_N on 2010-03-31
thanks Nev. That's the first time I used gedit.  I'm such a beginner here, I don't even know what the filename was when I entered  
gksudo gedit /etc/pulse/default.pamy suspicion is gksudo is a system command
etc  a directory , pulse a folder in that directory,
and default.pa the file I edited.

I'm getting a book to work on this stuff 

oh yes, and it worked, too............

thanks.

---

### Post by yetiman64 on 2010-03-31
Good to hear its fixed,Chuck_N,

For your info; gksudo (yes, a system command) raises gedits priviledges to "root" (needed to alter any system file), the path is /etc/pulse/ and the file at the end of the path is default.pa (this is what you editted). 

Always be very careful when using sudo or gksudo, they're powerfull tools and used wrongly with some other programs, will let you destroy your install (personal data backups with any system are advisable).

All the best with learning Linux (Its very worth it)

Bye, Nev

---

### Post by TheNerdAL on 2010-03-31
Please change the thread to [SOLVED] if it is solved. :)

---

### Post by yetiman64 on 2010-04-01
> **TheNerdAL said:**
> Please change the thread to [SOLVED] if it is solved. :)

I'm quite new to the forums and Chuck_N is a new user. Could you please explain  
1. Who should mark a thread as solved?.
2. How to mark it as such.

or possibly drop a link to this info, please.

Thank you,  Nev

---

### Post by Chuck_N on 2010-04-01
> **yetiman64 said:**
> I'm quite new to the forums and Chuck_N is a new user. Could you please explain  
1. Who should mark a thread as solved?.
2. How to mark it as such.

or possibly drop a link to this info, please.

Thank you,  Nev

My thread; my responsibility.
I went to Thread Tools at the top of the thread and did it.
Thanks again, Nev

---

