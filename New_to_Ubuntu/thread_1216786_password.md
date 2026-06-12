---
title: "password"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by need2no on 2009-07-18
I just installed ubuntu 9.04 a few days ago - all works well but I don't remember setting a password - I have a name, login name, and checked the box to login automatically since I'm the only user. 

The update manager wants to update but requests a password which I can't supply other than login name.

I haven't anything of importance saved yet.

Is my only option to reinstall ubuntu and start over with a new password?

---

### Post by LewRockwell on 2009-07-18
I believe during installation a username and password are requested/required to proceed with the installation

unless it's a "do or die" perhaps you could give yourself a day or two to try and remember what password you used

.

---

### Post by doas777 on 2009-07-18
do you know your password? if so, put in your users password, and it will do your bidding. confused me at first as well.

check this out:  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

if you don't know your password, you will have to reset it. 
reboot your PC, and at the grub menu, boot into recovery mode.
once you have a terminal interface, issue this command:
```
passwd <username> (you will be prompted to enter and confirm the password)
reboot

```

you may have to reapply the autologin after you get back in.

have fun

---

### Post by theozzlives on 2009-07-18
Boot in recovery mode > go to root prompt > passwd *username*
Enter your new password.

---

### Post by The Tronyx on 2009-07-18
What you may actually want to do is boot into single user mode or the recovery console and manually reset the password you initially assigned.  this can be done with the passwd command.

---

### Post by need2no on 2009-07-18
I can't recall the original password so tried to follow your advice. 

Thanks - your directions seem simple enough and it only took me 3 tries (rebooting) to get to the command line (had to look up what a grub was - I'm **really** a beginner) and it's been a long while since I did anything DOS-like.

Finally booted in recovery mode and still have a problem.

There were two lines that had recovery mode after them - so I highlighted the first one and went to the command line.

passwd wasn't recognized - used tab to see possible commands - had to use password (the whole word). Then it prompted for a password, which I entered. Then I got "Error 32, must be authenticated"

I was precise - no typos. Am I misunderstanding something?

Is the command line supposed to look like:

Grub> _

That's what I saw as the command line.

---

### Post by Arand on 2009-07-18
1. Boot computer so you get to a menu looking like this:```
Ubuntu 9.04, kernel 2.6.28-13-generic
Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
Ubuntu 9.04, memtest86+
```2. Then just arrow down to the first "recovery mode" option there and press enter to boot it. (If your menu looks different, don't worry, just take the _first_ recovery entry).

3. You should get to a prompt which looks like this:```
root@computername:~#
```("computername" is whatever you named it)
Here is where you should issue the command:```
passwd username
```(Where "username" is the username of your user)

...
I'm afraid you dived in a bit too deep there :)
The ```
Grub>_
```...is the grub command line interface (I think it's called that) which allows you to specify custom boot options, should you want to. It's definitely a handy thing to know about, but it does not dabble in login passwords at all.

EDIT: Dang, realised the image broke page layout badly, replaced with text code and updated description to match.

---

### Post by need2no on 2009-07-19
Thanks for the feedback. I got to a recovery mode line - pressed enter and got a menu - entered a choice saying ROOT - DROP TO ROOT SHELL  and got a prompt like this:

root@ computername-desktop:~#

tried to enter the code but didn't see any typing - pressed enter anyway.

Got another prompt line - entered the code again - still don't see anything.

Tried just entering the command passwd  by itself

Tried entering the actual password by itself

At some point got a line saying:  unknown user "my password"

I've used command lines in DOS in the early days of PCs but could always see what command I was typing and an immediate response. Should it be the same here?

Anyway, nothing good is happening and I don't know how to exit - ESc doesn't work.:confused:

---

### Post by NOTAGEEK on 2009-07-19
[http://www.howtogeek.com/howto/ubuntu/find-a-forgotten-password-saved-in-firefox/](http://www.howtogeek.com/howto/ubuntu/find-a-forgotten-password-saved-in-firefox/)


try this---maybe helpful...

---

### Post by need2no on 2009-07-19
Thanks - the problem's not a firefox password but the original user password. I don't save any other passwords for auto logins.

---

### Post by Cheesemill on 2009-07-19
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by need2no on 2009-07-19
This is probably exactly what I need - thanks - Ill try again.

---

### Post by need2no on 2009-07-19
I have a couple of questions before reinstalling ubuntu 9.04 on my old Dell. I did originally install it as the only OS. Inspite of many tries, I haven't been able to replace the user password I've forgotten.

1. When I boot to recovery mode - I still get the Dell screen and option to get into the Dell shell first - should it still be there? At least now I wait for Grub to load before hitting esc.

2. In recovery mode, I can now follow the clear and simple instructions to go to the root prompt but the prompt I get is not   root@computername:~#   but rather it is   root@computername-desktop:~#    Are they the same thing? Did I do something else weird on installation other than forget to note the user password?

3. When I type a command after the prompt (which I can never see), it doesn't seem to "take" (or maybe is really slow?) - when I hit enter, I get another prompt, sometimes several - and finally get a response.

I did type in  ls /home and confirmed that there was only one user.

Did manage to put in a new password and retype new UNIX password. Finally I get a line saying:

passwd: Authentication token manipulation error

I hit enter

passwd: passwprd unchanged.

I hate to give up!

Any advice before I bail?

---

### Post by Arand on 2009-07-19
2. computername-desktop is just as it should be, doesn't really matter (I might have been wrong earlier since I did not look in the root prompt specifically.

Also, yes, you will have to select "drop to root console" (or something similar after choosing recovery mode)


3. Do remeber, that everytime you enter passwords in a unix-based shell, you will see no feedback for the password letters, i.e. letters are accepted but there are no visual ******* to show the "letters".

From that error (passwd: Authentication token manipulation error) the most common cause would be that your retyping confirmation did not match the first you typed in. So just try again?

- Arand

---

