---
title: "Messed up Must Reinstall Need File Help"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by Elaphae on 2011-06-16
I really messed up my installation. Details on what I tried and my computer in three messages on this thread:
[http://ubuntuforums.org/showthread.php?t=1782737&highlight=Elaphae](http://ubuntuforums.org/showthread.php?t=1782737&highlight=Elaphae)

Looks like I have to reinstall and I am trying to save some of my files. When I boot off the CD I can get into the other Ubuntu files and copy them over to the windows partition. BUT some files are marked with an 'X' and will not copy due to permissions. I never did anything to lock or protect these files/folders. Most are photographs I have taken, some edited with GIMP.

Is there some way to get these files to copy? As in the long posts referred to I cannot log into Ubuntu but the CD works. I have already copied a number of files over to the Windows partition and they open in windows with no problem (pdf, jpeg, stuff I have Windows versions of the creator program for).

Also I use Thunderbird for my mail and would like to save a couple of hundred messages but I cannot find where Thunderbird has stored them - help!

Everything worked so well till I messed with it, if I can get Ubuntu reinstalled and working I'll never try to 'fix' anything again. Can anyone help me save the data?

---

### Post by jtarin on 2011-06-16
They are marked that way as they are owned by root. Use ```
sudo
``` before your commands in the terminal to manipulate by the commandline or ```
gksudo nautilus
``` to manipulate through the file manager.

---

### Post by oldfred on 2011-06-17
Your Thunderbird files are in .thunderbird in you /home/#USER or your name.. Change Nautilus view to show hidden files.

I always copy the entire profile which is xxxxxxx.default. and edit profile.ini with the copied profile. You usually have to start thunderbird to create a new x..default folder & profile.ini then edit the profile.ini and change to your saved copy of xxxxx.default.

I regularly copy the entire profile from my desktop to my laptop to travel & copy back. 

Update to tb3
[http://ubuntuforums.org/showthread.php?t=1349889](http://ubuntuforums.org/showthread.php?t=1349889)
new 
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

I also do the same for my Firefox profile. Copy entire profile from one computer to anther and back when traveling. Then I have all my bookmarks & configurations the same.

---

### Post by Elaphae on 2011-06-17
Jtarin:
The files I moved I just dragged and dropped. I am too new to free up the files with an 'X' using your directions w/o more detailed steps. I think you have me about half way there but I think I need more details as I don't know what to add (if anything) to the commands. I would prefer not to lose these and am hesitant to experiment. (In my original thread I was just trying to get sound out of my headphones, I thought I was following the directions - now I am reinstalling what I broke).

---

### Post by Elaphae on 2011-06-17
Oldfred:
About 5:45 am here, I'll wake up a bit and see if I can get both profiles. I am using the newest Thunderbird release My main problem is I know so little, the library here has only one out of date book on Ubuntu (9.something).

---

### Post by jtarin on 2011-06-17
> **Elaphae said:**
> Jtarin:
The files I moved I just dragged and dropped. I am too new to free up the files with an 'X' using your directions w/o more detailed steps. I think you have me about half way there but I think I need more details as I don't know what to add (if anything) to the commands. I would prefer not to lose these and am hesitant to experiment. (In my original thread I was just trying to get sound out of my headphones, I thought I was following the directions - now I am reinstalling what I broke).
[Here's a link]("http://www.liberiangeek.net/2010/09/add-open-administrator-nautilus-context-menu-ubuntu-10-10-maverick-meerkat/") to guide you into "Add Open as Administrator" on Nautilus Context Menu. This will work on all versions....but I can't guarantee on 11.04. Don't use it. After adding this you will be able to open directories and files as administrator. Be careful how you use it. It's a GUI, but you should learn to do it by commandline also. You will need the commandline one day to repair your system.:p
If you don't have internet connection let me know and I can give you directions for writing a script for this.

---

### Post by Elaphae on 2011-06-17
I have a connection but am only able to use Ubuntu off the cd - and have only the one cd drive. WIll give this a try later this morning :)

---

### Post by Elaphae on 2011-06-19
Still working on it, Nautilis, profile files, owned by root files. Much here that I have not really had to work with before.

---

### Post by Elaphae on 2011-06-19
Update (I only have 10.10 installed):
Nothing works. Running of the cd I don't seem to be able to install Nautilus. Screen shots go to desk top then when I try and copy them to disk that fails (I don't think that they are really written to the desk top to begin with as that would require writing to the cd).

Tried gksudo Nautilus in terminal, failed message started: 
"Failed to get current CK session..."

I would still like to claim the emails from the hidden thunderbird file but cannot see it. My photos are less important at this point. 
Right click does not show any option to show hidden.
I suspect the main problem is my lack of experience with Ubuntu, Terminal and the rest of it. Still need help!

---

### Post by Elaphae on 2011-06-19
I DID manage to find (make unhidden) the .thunderbird and other hidden files by using 'ctrl+h'! Alas, .thunderbird is owned by the root and I cannot copy it as yet. Close to wit's end and would just reinstall if I did not want the 200 or so emails that are a bit important.

When I was 18 this would have been exciting, at 30 a challenge to be won, now (past 50) I just want to get back to getting my work done. Let the challenge be actually being able to work with Ubuntu. :)

---

### Post by Elaphae on 2011-06-20
Still stuck...

---

### Post by Elaphae on 2011-06-20
Not solved, searching for a way to get unstuck

---

### Post by nothingspecial on 2011-06-20
> **Elaphae said:**
> 

Tried gksudo Nautilus in terminal

Try it with a lowercase n

---

### Post by jtarin on 2011-06-20
Use the Live CD.....boot to the desktop and open a terminal.
Follow [these directions]("https://help.ubuntu.com/community/Grub2#ChRoot") for using the CHROOT method. This will change you to the root/owner of those files. You will then be able to move them off disk. Follow steps #1-7.....then skip #8,9,10. When finished with your file manipulation do step #11 to exit the CHROOT environment. At step #7 is where you will proceed to locate your files then move them. Remember you are root so you have control.Remember also that that file is hidden so unhide it. Any more help you need post back. I would suggest you print out those instructions. Type the commands exactly. If you type a command and you get an error check it and re-type. If it still errors note the error and post here.

---

