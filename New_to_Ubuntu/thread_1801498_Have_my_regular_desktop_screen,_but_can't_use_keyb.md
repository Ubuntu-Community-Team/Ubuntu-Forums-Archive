---
title: "Have my regular desktop screen, but can't use keyboard to log in."
date: 2011-07-10
forum: New to Ubuntu
---

### Post by altheablue on 2011-07-10
Hello all. I'm hoping you can help with a silly question. I'm running 11.04 Natty on a Windows PC in wubi. I'm running Natty in Classic mode if that matters.

When I rebooted my computer today, I now have my normal desktop, but asking for my password because "[t]he login keyring did not get unlocked when you logged into your computer." The problem is I can't use the keyboard, so I can't log in. the mouse works with a few things but not many (probably just because I'm not logged in).

I booted into Windows and the keyboard works there.

The only change I made to my computer that I know of before rebooting is that I installed [f.lux]("http://stereopsis.com/flux/"), and it is running as a start-up process. Of course I don't know that that's the issue.

I can boot into recovery mood; I just don't know what to do once I'm there. If I knew how to kill a process, I'd try killing f.lux from recovery mode, but I've searched and can't seem to figure out how to do that.

Any help would be much appreciated. Thanks.

---

### Post by jtarin on 2011-07-10
I wouldn't think f.lux is the problem as I run it and have never had problems, but you never know. It doesn't start until you login as a user though.You can use the terminal and issue the command "top" to see running processes. If you see f.lux note its pid number then hit the "K" key for kill, then enter the pid number and then hit enter and answer yes.

---

### Post by altheablue on 2011-07-10
Thanks! I did what you said and f.lux isn't listed, so now I know what the problem isn't, which is good. Thanks for your help. :)

---

### Post by jtarin on 2011-07-10
[B]Does the message look similar to this:
[/B]
```
The title bar of the window says "Unlock Login Keyring"

First line says 
"Enter password to unlock your login keyring."

Second line says 
"The login keyring did not get unlocked when you logged into your computer."

Last line says 
"Password: ___________________"

Two buttons underneath this say "Cancel" and "OK"


```

---

### Post by altheablue on 2011-07-10
Yep, exactly that. But I can't click on the password entry field, or type. 
This is a weird one. I feel like it's something small and silly, but I couldn't say what.

---

### Post by jtarin on 2011-07-10
Do you have a wireless connection with a password?

---

### Post by jtarin on 2011-07-10
You can set things back to "normal" by going to /home/yourusername/.gnome2/keyrings and deleting the file default.keyring

Ok from what I understand you cannot get to the desktop???
If this is the case, at the login window open another virtual terminal by using the key combination. "Ctrl + Alt + F1-F6" this will give you a virtual terminal.Now login in as yourusername and you will be in your /home/username directory. Now "cd .gnome2/keyrings. Note the "."(dot) before the filenames.
Now in the terminal type "ls" and this should show you all files and directories within "keyrings".If you can see the file "default.keyring" issue the command "rm default.keyring". This will delete the file. Now you can issue the command "cd" and at the prompt enter the key combination Ctrl + Alt + F7, which will bring you back to a graphical environment. You might be able to login at this time but its doubtful before rebooting, so reboot and see how things went. 


 
I hate these keyring managers (KDE has "wallet") and if I cannot uninstall them, I found that if you enter a blank password, they generally go away after asking "Shall I store the password somewhere?".

---

### Post by altheablue on 2011-07-10
It's actually a desktop with a wired connection. I tried what you said but there was no "login.keyring", only a "default.keyring" and "keyring store" (I think). I removed "default.keyring," and rebooted, but that didn't have any effect. Curiouser and curiouser...

Also, I swear I think f.lux *is* running, but I could be hallucinating because I've been looking at too many screens. ;)

i may try removing the key.store or whatever it was. Thank you so much for all your help! :)

eta:i mean there was login, but not default. I'm sleepy. ;)

---

### Post by altheablue on 2011-07-13
I apologize for bumping this. I dropped the problem for a few days and now I'm trying to solve it again. To summarize, I have the window that says 
1st line: "Enter password to unlock your login keyring."  
2nd line: "The login keyring did not get unlocked when you logged into your computer."

I have tried jtarin's advice above, but I don't have a "default.keyring" listed under .gnome2/keyrings.

I've been reading about others having various issues with the keyring, but my problem is I can't even get to it. My keyboard works, I can open a virtual terminal, etc., but I cannot enter anything into the password box on my desktop. (I have rebooted.)

As always, any help much, much appreciated.

ETA: Actually, now I have the "Choose password for new keyring" box because I tried this:

```
killall -9 gnome-keyring-daemon
rm -fr ~/.gnome2/keyrings
```

---

### Post by jtarin on 2011-07-13
Choose a new password.....one that you are able to remember.

---

### Post by altheablue on 2011-07-13
No sorry, I mean I *physically* can't enter the password. I know my password, but somehow the keyboard will not function for this purpose.

Don't worry about it. I'm sure it's something stupid.

---

### Post by jtarin on 2011-07-13
[http://www.deanmarshall.co.uk/deans-blog/90/158-ubuntu-1104-mouse-and-keyboard-issues.html](http://www.deanmarshall.co.uk/deans-blog/90/158-ubuntu-1104-mouse-and-keyboard-issues.html)

---

### Post by altheablue on 2011-07-14
Thanks for all your help. Unfortunately, that code didn't help on my  system - I typed it in about 4 times and it didn't bring up what it was  supposed to - but at least now I have areas to research. I haven't had  much time to do that b/c of work. Thanks again. :)

---

### Post by altheablue on 2011-07-14
Well, I figured it out - sort of. It's Compiz. It has an issue that I haven't figured out yet, but [this]("http://www.khattam.info/solved-compiz-text-input-problem-in-ubuntu-11-04-natty-narwhal-alpha-1-2010-12-04.html") got me on the right track. Apparently compiz had crashed or is crashing, drivers, not sure but that's the general gist. Working ok right now though (I'm afraid to write that).

So I'm going to mark this solved and hope that it is! :)

jtarin, thanks for all your help. :cheers: <--should be a smilie.

---

