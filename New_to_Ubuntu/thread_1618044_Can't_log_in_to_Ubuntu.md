---
title: "Can't log in to Ubuntu"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by Jay7 on 2010-11-10
Hi, I'm absolutely new to Linux. I just installed Ubuntu 10.10. I changed the settings of the default user to "Admin". Then I rebooted the system but whenever I want to log in the desktop flashes for a fraction of a second and then I get logged out and redirected back to the login screen again. The system has just one user. Any idea of how to fix it other than re-install the system? Thanks.

---

### Post by Spice Weasel on 2010-11-10
[LIST=1]
[*]Press Ctrl+Alt+F2
[*]Log in with your username and password
[*]Create a new account by typing "sudo adduser username"
[*]Enter "sudo service gdm restart"
[*]Press Ctrl+Alt+F7
[/LIST]

---

### Post by toekneewood on 2010-11-10
Ctrl+Alt+F1
This is a command line example of how to create a new user
```

sudo useradd -m YOUR-LOGIN-NAME -p your_password -d /home/YOUR-LOGIN-NAME -s /bin/bash
Actual example:
sudo useradd -m tony -p password -d /home/tony -s /bin/bash
then to set your password
passwd tony
Then Ctrl+Alt+F7

```

---

### Post by Jay7 on 2010-11-10
Cheers guys, you're stars! Will try it when I get home tonight.

---

### Post by Jay7 on 2010-11-10
Pressing Ctrl+Alt+F1 or Ctrl+Alt+F2 in the login screen crashes the system and the computer freezes. A bit worrying to be honest. I am going to give it another try with a fresh Ubuntu install but if it happens again I will have to try a different distribution or switch back to Windows I'm affraid. :(

---

### Post by Jay7 on 2010-11-14
I really want Ubuntu to work on my PC... however, it has been some of the most frustrating experience I've ever had so far.

I installed Ubuntu 10.10 and set up Apache, PHP, MySQL and phpMyAdmin. It worked fine straight after the install. However, a couple of days later, when I wanted to log in, I logged in, the desktop flashed for about half a second and then the login scren appeared again. I tried CTRL+ALT+F1...F12 as advised here, but I only got a screen with top row of pixels in random colours, middle of the sceen in login background colours and bottom of the scren blue. CTRL+ALT+F7 didn't help. Rebooting the computer got me to the same loop.

I re-installed Ubuntu and got exactly the same situation a couple of days later. It is really frustrating. 

I tried searching but couldn't find any useful info. Can anyone point me to the right direction please? Thank you.

---

### Post by Jay7 on 2010-11-14
OK, now I found out that if I press CTRL+ALT+F1...F12 apart of F8, the screen will become weird (as described earlier). Pressing CTRL+ALT+F8 reverts to the login page.

From what I've read I should get a terminal and should be able to type in the commands toekneewood and Spice Weasel posted earlier... I'm not seeing the black screen though.

Could it be something to do with the graphic card and drivers? I dn't know what graphic card I have in this machine and I have no idea how to find out.

Edited: That's crazy, sometimes F8 helps, sometimes F9... it doesn't seem to be consistent and changes after unsuccessful logins.

Help please!

---

### Post by Jay7 on 2010-11-14
I managed to log in to the computer as root and created a new user. Now I can log in as the new user as well but I can't access the account of the original user. When I try o log in as the original user I get logged out immediatelly as before. So, where do I go from here? How can I 'fix' whatever is broken in the original user's account? Any advice will be appreciated. Thanks.

---

### Post by apollothethird on 2010-11-14
> **Jay7 said:**
> OK, now I found out that if I press CTRL+ALT+F1...F12 apart of F8, the screen will become weird (as described earlier). Pressing CTRL+ALT+F8 reverts to the login page.

Anything above CTRL+ALT+F7 by default won’t do anything.  If you’ve experimented with the system where they might mean something the process of your experiments might have broken something.  But I’m sure that’s pretty unlikely.  You’re probably too impatient to allow the screen to change and hitting a lot of commands at the same time.

Looking at the thread it appears that you jumped the gun and started over rather than being patient for a response to help you resolve the original problem.  The system probably wasn’t broken.  There is a good chance you might have been hitting the CTRL+ALT+FKey incorrectly.  You might have been doing something similar to hitting the CTRL+ALT+F7 key which kept you on the X windows screen.  Then while never releasing the CTRL and ALT key when through all the Function keys.  You have to release the CTRL and ALT key to start over for a different screen.

Quickly starting over without identifying what you’re doing wrong might consistently bring you back to the point of where you do something wrong.  If you take the time to identify what the problem is, it might spare you from some frustration.

> From what I've read I should get a terminal and should be able to type in the commands toekneewood and Spice Weasel posted earlier... I'm not seeing the black screen though.

Could it be something to do with the graphic card and drivers? I dn't know what graphic card I have in this machine and I have no idea how to find out.

Edited: That's crazy, sometimes F8 helps, sometimes F9... it doesn't seem to be consistent and changes after unsuccessful logins.

Help please!

CTRL+ALT+F8 and CTRL+ALT+F9 never do anything.  There’s a chance that you’re seeing the results of a different key sequence by the time you hit those keys.

> **Jay7 said:**
> I managed to log in to the computer as root and created a new user. Now I can log in as the new user as well but I can't access the account of the original user. When I try o log in as the original user I get logged out immediatelly as before. So, where do I go from here? How can I 'fix' whatever is broken in the original user's account? Any advice will be appreciated. Thanks.

You can try to recreate the defaults by changing the original home directory of the first account to something different.  Then create another directory by the exact name of the original home account.  Then change the owner of this new directory to the name of the original account.

Now when you login to the original account the login session should recreate the defaults for that account.  You can then go to the renamed directory and pick out the things that you need and bring them over to the new directory.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Jay7 on 2010-11-15
Thanks apollothethird, you guessed correctly, I am quite impatient. Changing the home directory sounds simple as you describe it but for someone with no previous experience with linux it is quite a challange. I suppose I have to read more about users and priviages. Seems like I managed to 'lock' an account (now both accounts) and that's why I can't log into them. I could log to the new account and then switch to the old one from the new one. Then I changed the user type and checked the "do not ask for login in startup" option and I have both accounts locked now. At least I know how to create a new account. :-)

By the way, the ALT+CTRL+F1...F7 still break the screen and ALT+CTRL+F8 or sometimes F9 revert it back to the original login screen even if I am patient and let the system plenty of time before I press different buttons.

Just downloading openSUSE, will try it as well and see if I get stucked as I am with Ubuntu.

I appreciate your help.

---

