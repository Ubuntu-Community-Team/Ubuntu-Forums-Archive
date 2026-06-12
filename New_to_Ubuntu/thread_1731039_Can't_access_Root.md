---
title: "Can't access Root?"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by TheOmnipotentPilot on 2011-04-16
Ok, I think this is the place to post this (I am a beginner =))
anyway, i'm trying to get into the "root" folder on my drive, but when I try to click on it, i get a message saying "you do not have the permissions necessary to view the contents of "root""
Umm... i thought I left this problem behind when i left windows... how do I get permission to view and edit the files? I'm the only user on this computer....

Thanks!!!

---

### Post by scott-ian on 2011-04-16
There would be no need to access that specific directory.  You could press alt+f2, and type "gksudo nautilus".  You will have to type your password, and then you will be able to access all files in that window.  You may want to create a link to run the command.  There is also a link to it with this program: [http://code.google.com/p/ucc/](http://code.google.com/p/ucc/).

---

### Post by K_45 on 2011-04-16
Why do you need access?

---

### Post by yetiman64 on 2011-04-16
> **scott-ian said:**
> **There would be no need to access that specific directory.**  You could press alt+f2, and type "gksudo nautilus".  You will have to type your password, and then you will be able to access all files in that window.  You may want to create a link to run the command.  There is also a link to it with this program: [http://code.google.com/p/ucc/](http://code.google.com/p/ucc/).

**+1** also if as a beginner you are using a root file browser (nautilus) I suggest your first step be to use (in the root browser) Edit > Backgrounds and Emblems > Colours Tab, find the firetruck red and drag it into the nautilus root window.

This will turn all root browser windows bright red as a warning to what you are using in future. You can save yourself from potential disaster when it's obvious your running as root.

Best advice is to stay out of /root unless it is absolutely necessary.

---

### Post by akakingess on 2011-04-16
+1 for yetiman64, his advice about changing the background color is excellent to say the least and I had not even thought of that before so thank you yetiman64, and to the OP I would strongly recommend doing exactly as he stated to save yourself from a plethora of future headaches.

---

### Post by fabricator4 on 2011-04-16
> **TheOmnipotentPilot said:**
> 
Umm... i thought I left this problem behind when i left windows... 
Thanks!!!

No, what you left behind was the ability to easily get viruses, trojans and malware.  What you GOT was a highly secure and stable platform for all your computing needs.  :-)

Not being logged in as root by default is just part of that security.  You can do anything that you need to on your computer easily and simply when you know how.

More information [here]("https://help.ubuntu.com/community/RootSudo").

Chris

---

### Post by scott-ian on 2011-04-16
> **yetiman64 said:**
> **+1** also if as a beginner you are using a root file browser (nautilus) I suggest your first step be to use (in the root browser) Edit > Backgrounds and Emblems > Colours Tab, find the firetruck red and drag it into the nautilus root window.

This will turn all root browser windows bright red as a warning to what you are using in future. You can save yourself from potential disaster when it's obvious your running as root.

Best advice is to stay out of root unless it is absolutely necessary.

I never thought of that.  That is a good tip for **anyone** who decides to use the root file manager, especially if you are likely to run both a root and a normal Nautilus at the same time, which I sometimes do.

---

### Post by oldos2er on 2011-04-16
> **TheOmnipotentPilot said:**
> Ok, I think this is the place to post this (I am a beginner =))
anyway, i'm trying to get into the "root" folder on my drive, but when I try to click on it, i get a message saying "you do not have the permissions necessary to view the contents of "root""


It's unclear whether you mean / or /root. **cd /** will get you to the root folder (the folder from which everything in the file system originates). /root is the root (or admin) user's home folder, in the same sense that your user's home folder is /home/user.

Which files are you wanting to modify?

---

### Post by dkolars on 2011-05-10
> **yetiman64 said:**
> **+1** also if as a beginner you are using a root file browser (nautilus) I suggest your first step be to use (in the root browser) Edit > Backgrounds and Emblems > Colours Tab, find the firetruck red and drag it into the nautilus root window.

This will turn all root browser windows bright red as a warning to what you are using in future. You can save yourself from potential disaster when it's obvious your running as root.

Best advice is to stay out of root unless it is absolutely necessary.

Tried this.... not sure where the "nautilus root window" is... I opened Nautilus, clicked on root (can't view contents of course), but dragging any color to anything doesn't work - it just bounces back to the color chart.  Hints?

---

### Post by yetiman64 on 2011-05-10
> **dkolars said:**
> Tried this.... not sure where the "nautilus root window" is... I opened Nautilus, clicked on root (can't view contents of course), but dragging any color to anything doesn't work - it just bounces back to the color chart.  Hints?

When you open a normal browser window (nautilus) you will note in the side bar the home directory has your user name.

In a terminal you can open a root browser window with the command,

```
gksu nautilus
``` Notice when this is used the home directory is that for "root". Use it with extreme caution as changing anything with it can destroy your install or make it unbootable if mistakes occur. Also the reason to change the background to bright red, as a symbol for danger.

Hence my earlier comment,
> Best advice is to stay out of /root unless it is absolutely necessary.Only use a root browser when necessary and it is arguable as to whether it ever is. You can safely do any command from terminal with the "sudo" command. Just asking here in the forums for the correct commands to use is safer than using the "easier" method with a root browser window (Oh So Dangerous !)

---

### Post by deconstrained on 2011-05-10
To view "root", path / (a.k.a. "File System" under "Computer" in the "Places" menu) you don't need root permissions. 

The path /root is an entirely different creature altogether -- the home directory of the superuser, and access to it is restricted.

However, **There's nothing to see in /root. The folder is just empty by default in most Linux/Unix distributions.**

---

### Post by dkolars on 2011-05-10
Thanks, that worked!  I don't mess around with root too much, but sometimes really wish I didn't need to input a password for **everything**!!

---

### Post by fballem on 2011-05-10
.. and sometimes, as we all have learned, the fact that you have to put in a password for so much should make you think - do I REALLY want to do this.

Just think back to windows of all of those times when you would get a message box up during an installation and just answer yes or click okay.

You might also want to look at: [http://ubuntuforums.org/showthread.php?t=1171373&highlight=phishing+scam](http://ubuntuforums.org/showthread.php?t=1171373&highlight=phishing+scam)

and be grateful for all those times, going forward, when you will have to enter your password.

---

### Post by yetiman64 on 2011-05-10
> **dkolars said:**
> Thanks, that worked!  I don't mess around with root too much, but sometimes really wish I didn't need to input a password for **everything**!!

Tight permissions and file & folder ownership are one of the reasons viruses/malware find it near impossible to get a foot hold in a Linux environment. 

Get used to the passwords if you want safer computing. 

Also whenever you are asked for a password adjust to the idea it is the system giving you a friendly prod to remind you what you do next if done wrong can do serious damage, particularly with a root browser window. 

Bad memories of crippled systems are flooding back here from when I first started in Ubuntu and was in the habit of using a root browser, it's too easy to make monumental blunders on occasion requiring re-installs. 

Try to do your best to learn terminal commands if you can, in no time you will find them actually quite a bit faster and much safer to use. Take care for now though.

> .. and sometimes, as we all have learned, the fact that you have to put  in a password for so much should make you think - do I REALLY want to do  this.
 YEP ! Think carefully. Linux assumes you know what you're doing, and is seriously unforgiving if you don't.

---

### Post by dkolars on 2011-05-10
Yep, I'm hip to the reasoning behind all the security, but I'm a retired NT admin, and learned on a Commodore 64...  It's just a pain to have to do it for what I consider pretty mundane tasks...

Plus, I tried to change my password to something shorter, and it wants longer, thank you... so tried a longer one, and it's "too close to the existing password"... which baffled me, as my current pw has caps, lc, and #'s... the one I wanted was all lc, no caps or #'s.  Duh...  So, stuck with the pw I originally chose and will grin and bear it...  I used to have a Win program that would remember text strings and input one of them using customizable key strokes...  I miss that program!!  :-)

---

