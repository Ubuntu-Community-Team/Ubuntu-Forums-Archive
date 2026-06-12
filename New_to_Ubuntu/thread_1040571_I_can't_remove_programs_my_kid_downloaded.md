---
title: "I can't remove programs my kid downloaded"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by jalehtor on 2009-01-15
My son downloaded "Big Green Help," "Play Wizard 101," and "Limewire." The first two are on the desktop; I haven't a clue where Limewire is. I'm trying to remove all three programs. I looked in the add/remove programs on applications and searched on Synaptic, and couldn't find them on either list. How do you locate and remove programs on Ubuntu other than through add/remove or Synaptic? Is there something I'm missing? :confused:

---

### Post by HermanAB on 2009-01-15
These are probably Windows programs that won't even run on Linux.  So simply hunt down the files and delete them: Right click, Delete.

If you have no idea where something is do a search from a terminal:
$ sudo find / -name *lime*

Then remove it with 'rm', but be CAREFUL!  It is probably best to just forget about it and not risk finding and deleting it.

Cheers,

Herman

---

### Post by linkmaster03 on 2009-01-15
There should be a LimeWire folder somewhere (probably in his /home folder) that contains all the files. The other two sound like Windows games installed through WINE. Look in the WINE menu to see if there is an uninstall entry by those games.

---

### Post by handydan918 on 2009-01-15
Limewire makes a Linux version, and it is a .deb. 
Try doing ```
sudo apt-get remove limewire
```

wizard 101 appears to be windows only. Don't sweat it too much, that means it can't do anything to your system.

If you really want to find it, try ```
sudo updatedb && locate wizard
```
This will take a few minutes...

The big green weenie seems to be a windows only scam as well, so again, don't let it peg yer paranoia meter.

---

### Post by jalehtor on 2009-01-15
Thank you for letting me know that these will not hurt my computer; I was worried about viruses etc. Btw, I located Wizard on the terminal and on Wine and uninstalled it. The program, however, is still on my desktop. Is there something else you're supposed to do?

---

### Post by HotShotDJ on 2009-01-15
> **jalehtor said:**
>  How do you locate and remove programs on Ubuntu other than through add/remove or Synaptic? Is there something I'm missing? :confused:Just delete the files and possibly the kid's home directory.  He could not have possibly actually installed the software system-wide, because he would have to have administrative (sudo) privileges, which no sane person would grant to any other system user, and certainly not to a child, tween, or teen.

You DIDN'T give anybody administrative privileges on your computer?  Right?

---

### Post by jalehtor on 2009-01-15
:oops: Well...I mean, he doesn't have my password, but he doesn't have a home directory, and apparently he managed to install this stuff without having access to my pw. What do you mean by "system-wide" as opposed to his "home folder"? If he managed to install a program so that it works, doesn't that mean system wide by definition?

---

### Post by Bölvaður on 2009-01-15
cd ~/.wine/drive_c/Program Files    note that ~ is your home folder
rm -R....wizzard thingy...

you can delete the rest of the games if there are any leftovers. And you can search your registry ~/.wine/drive_c/windows/regedit.exe, if you must. But these programs will probably not be able to do anything as they have no rights, user installed programs only have user rights.. not super user :)

---

### Post by HotShotDJ on 2009-01-15
> **jalehtor said:**
> :oops: [SIZE="1"]Hotshot, actually, yep, I did.[/SIZE]Oh dear.  Well, you'll have to change your password immediately.

System --> Administration --> Users and Groups.  Click on the Unlock button (near bottom right of Users Settings dialog box). Enter your current password and click "Authenticate"

Now, highlight your user name and click "Properties" -- Under the Account tab, you'll notice three groupings... scan down to the grouping labeled "Password."  Tick off "Set password by hand" and enter a new password and then again in the confirmation box.  Click OK.

While you are in there, create Limited User Accounts for everybody else in your family.  Click on "Add User" And fill in the blanks.  Be sure to assign unique passwords to each account.  Do NOT make any changes to the User Privileges tab or the Advanced tab.  Click on OK.  Repeat for each user.

Keep your own account's password (which has administrative privileges) to yourself to avoid this problem in the future.

---

### Post by HotShotDJ on 2009-01-15
> **jalehtor said:**
> If he managed to install a program so that it works, doesn't that mean system wide by definition?Not necessarily.  Many applications can be installed in the user's own directory for use by that user alone.  Only the system administrator can install applications that can be shared by all users (system-wide).

---

### Post by mjheagle8 on 2009-01-15
i second that hotshot. you should only let your kid on with a limited rights account. i would highly reccomend make a new account for him to use. dont ever let anyone use the super user account other than the super user themself.  and dont give anyone the superuser password.

---

### Post by niteshifter on 2009-01-15
> **jalehtor said:**
> :oops: Well...I mean, he doesn't have my password, but he doesn't have a home directory, and apparently he managed to install this stuff without having access to my pw. What do you mean by "system-wide" as opposed to his "home folder"? If he managed to install a program so that it works, doesn't that mean system wide by definition?

This means:

You've your computer set to automatically log **you** in on startup - that  is, no password is needed, no login screen presents itself.

If that is not the case, then your young'un does indeed have your password. Children are observant - more so than we adults would care to admit at times.

If you are setup for auto-login, now you know why that's discouraged ;)

---

### Post by jalehtor on 2009-01-15
I'm changing the mess as we speak; I've learned my lesson. One problem, however: World of Warcraft does not show up on his account, which is about the only thing he does on the computer (other than downloading strange programs, that is).

---

### Post by mjheagle8 on 2009-01-15
glad we could help!

---

### Post by HotShotDJ on 2009-01-15
> **jalehtor said:**
> I've learned my lesson. One problem, however: World of Warcraft does not show up on his account, which is about the only thing he does on the computer (other than downloading strange programs, that is).He will have to install it in his own account.  It is a windows program using WINE -- Applications that use WINE are installed on a per-user basis, not system-wide.  He won't need administrative privileges to do it.

I join mjheagle8 in being pleased to be able to help.  Of course, I don't blame you for having "learned your lesson" the hard way... I fully blame Microsoft for encouraging home users to believe that it is ok to set up computers that way.  (Boy, is your son going to be MAD when he tries to do an administrative task and discovers he no longer has authorization.  Please take pictures so we can enjoy the laugh with you.)
:popcorn:

---

### Post by jalehtor on 2009-01-15
LOL! He's a sweet kid, but he's not terribly careful about where he travels online.

---

### Post by mjheagle8 on 2009-01-15
thats unfortunate. oh the pain of not being a super user. haha

---

### Post by jalehtor on 2009-01-15
:lolflag:You know...parents need a chance to feel special now and then. Anyhow, no major harm done, and further harm prevented thanks to you guys. Thanks again.

---

### Post by richg on 2009-01-15
Be nice to your kids. They will choose your nursing home. :wink:

Rich

---

### Post by HotShotDJ on 2009-01-15
> **richg said:**
> Be nice to your kids. They will choose your nursing home. :wink:LOL, Rich! I have a living will and long-term care insurance -- I intend to remain the "superuser" to the bitter end.
:lolflag:

---

### Post by pieisgood4589 on 2009-01-15
> **jalehtor said:**
> Thank you for letting me know that these will not hurt my computer; I was worried about viruses etc. Btw, I located Wizard on the terminal and on Wine and uninstalled it. The program, however, is still on my desktop. Is there something else you're supposed to do?

Heheheh, you really don't have to worry about viruses on Linux. :guitar:

---

### Post by mjheagle8 on 2009-01-15
thats the way to go! specify one so you know where you're going! haha

---

### Post by HotShotDJ on 2009-01-15
> **jalehtor said:**
> LOL! He's a sweet kid, but he's not terribly careful about where he travels online.Hehehe... I know the feeling.  Kids will be kids, even the sweet ones. :)  Some other things to consider to make sure he doesn't accidentally mess up your system:

Password protect GRUB (to prevent him booting into recovery mode, which has administrative access to the entire system): [http://ubuntuforums.org/showthread.php?t=7353](http://ubuntuforums.org/showthread.php?t=7353)

Set your BIOS to not allow booting from removable media AND password protect the BIOS --  this is hardware specific, so you'll need to consult your computer's user manual to learn how to do this.

And remember, while all the things we've talked about in this thread are helpful in securing your system against accidental or even malicious problems, nothing replaces good supervision (I know you know that, but I always say it anyway).

---

### Post by handydan918 on 2009-01-15
> **HotShotDJ said:**
> Hehehe... I know the feeling.  Kids will be kids, even the sweet ones. :)  Some other things to consider to make sure he doesn't accidentally mess up your system:

Password protect GRUB (to prevent him booting into recovery mode, which has administrative access to the entire system): [http://ubuntuforums.org/showthread.php?t=7353](http://ubuntuforums.org/showthread.php?t=7353)

Set your BIOS to not allow booting from removable media AND password protect the BIOS --  this is hardware specific, so you'll need to consult your computer's user manual to learn how to do this.


None of which will prevent anyone with physical access to the computer from owning it in under 15 minutes anyway....

---

### Post by mjheagle8 on 2009-01-15
yeah, if you have physical access to a machine there's nothing anyone can do to stop you from taking it over. they can only make it harder or take longer.

---

### Post by HotShotDJ on 2009-01-16
> **handydan918 said:**
> None of which will prevent anyone with physical access to the computer from owning it in under 15 minutes anyway....

> **mjheagle8 said:**
> yeah, if you have physical access to a machine there's nothing anyone can do to stop you from taking it over. they can only make it harder or take longer.

We're talking about making sure his son, who is a sweet kid and who wouldn't purposefully hack the computer, doesn't mess things up.  Of course, physical access to the hardware is pretty much "game over" with a malicious hacker.  No argument here.

---

### Post by mjheagle8 on 2009-01-16
> **HotShotDJ said:**
> We're talking about making sure his son, who is a sweet kid and who wouldn't purposefully hack the computer, doesn't mess things up.  Of course, physical access to the hardware is pretty much "game over" with a malicious hacker.  No argument here.

haha this is true.

---

