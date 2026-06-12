---
title: "Can't access my files anymore"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by aj_the_first on 2009-06-29
I'll try to make a long story short...
I am brand new to Ubuntu, and practically brand new to Linux. I love it, and I will never go back, BUT, users certainly have the ability to screw some stuff up without knowing it! None of the operating system protecting itself from users mistakes like windows...
 
Okay, My wife gave me her computer, which she was running Ubuntu on. She has all sorts of movies and pictures that I want access to on her user profile (sarah), so I created a new profile for myself (aj), and tried to access her files. Couldn't do it. So I logged back onto her profile (sarah) and changed the permissions on the folders so any user could have full access to them. Logged back in on my profile (aj) and found I couldn't still couldn't access them anyway. So I restarted just in case this is windows-style and needed a re-boot after any changes... it wouldn't boot correctly and gave this error on start-up:
 
[COLOR=black][FONT=Verdana]User's $HOME/.dmrc file is being ignored. This prevents the default sessin and language from being saved. File should be owne dby user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users[/FONT][/COLOR]
 
I searched Ubuntu forums and found this thread:
 
[COLOR=black][FONT=Verdana][http://ubuntuforums.org/showthread.php?t=371052](http://ubuntuforums.org/showthread.php?t=371052)[/FONT][/COLOR]

[COLOR=black][FONT=Verdana][SIZE=1]and used the CLI commands listed in that thread and typed them from the root prompt in GRUB, in recovery mode.[/SIZE][/FONT][/COLOR]
[SIZE=1]These are the commands I used:[/SIZE]
[SIZE=1][COLOR=black][FONT=Verdana]sudo chmod 644 /home/sarah/.dmrc[/FONT][/COLOR][/SIZE]
[SIZE=1][COLOR=black][FONT=Verdana]sudo chown sarah /home/sarah/.dmrc[/FONT][/COLOR][/SIZE]
[SIZE=1][COLOR=black][FONT=Verdana]sudo chmod -R 700 /home/sarah[/FONT][/COLOR][/SIZE]
[SIZE=1][COLOR=black][FONT=Verdana]sudo chown -R sarah /home/sarah[/FONT][/COLOR][/SIZE]

[SIZE=1]Well, I boot without the error now, but now neither user, not sarah or AJ, can access the media files in the video and picture folders of the home folder. I can view them, but when I try to open them, the player or viewer just closes immediately, just like they did when the aj user profile doesn't have permissions.[/SIZE]

[SIZE=1]What comes next besides backing up 110 GB of media and then reloading the operating system?[/SIZE]

Thanks,
AJ

---

### Post by achase79 on 2009-06-29
my idea would be to move the files out of the home folder to something like "/shared"

```
sudo mkdir /shared
cd /shared
sudo mv /home/sarah/Video /shared
sudo mv /home/sarah/Pictures /shared
sudo chmod 777 -R /shared

```

---

### Post by aj_the_first on 2009-06-29
Well, I created the folder and moved the subfolders over like you showed in the commands, and it is all set up like that now, but... still can't access the media with the sarah profile.  The player just opens and then immediately closes.  At least now I can access it with the aj profile though.
I guess I messed something up in the sarah profile, though I wouldn't even know where to begin since there are no error messages, unless there is a system log that saves error messages that don't appear to the user.
 
How about this for odd though:
 
Under the sarah profile I can enable the visual effects inside the user preferences > appearance.  But if I try to enable them in the aj profile, then it says "desktops effects could not be enabled"
 
When I first enabled the effects on the sarah profile it worked no problem, but I went ahead and disabled them.  Then on another boot-up I decided I liked them, tried to enable them, and I got this same "could not be enabled" error message, but rebooted, tried again, and got a "driver could not be found" message, so I rebooted again, and it worked.
 
basically, I find that everytime I reboot, things are just a little different.  And the computer isn't even online or getting updates, it just...  changes; just a little different everytime.  Like reaching in a bag of skittles: always sweet and chewy, but not exactly the same flavor...

---

