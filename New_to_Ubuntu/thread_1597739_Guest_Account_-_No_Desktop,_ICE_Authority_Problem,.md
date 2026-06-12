---
title: "Guest Account - No Desktop, ICE Authority Problem, problem w/configuration server"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by Amanda8404 on 2010-10-15
Hi Everyone,

I am trying to get a guest account working on my laptop (I upgraded to Lucid Lynx recently from an old version, its not a fresh install). They show up after entering the password, and then all that is on the screen is a desktop background with no panels or anything, it's totally blank. There were several error messages, and I don't know if they are referring to one problem or not- I can create a new thread for each if they are seperate. I figured out part of it but will describe all of them below - 

1.) First it said "Nautilus could not create the following required folders: /home/guest/Desktop, and /home/guest/.nautilus", and "Before running Nautilus, please create these folders or set permissions such that Nautilus can create them". I created those folders, so now when I try to sign in those messages don't show up anymore. I would like it if someone could explain about giving nautilus permission, though. 

2.) "Could not update ICE authority file /home/guest/.ICEauthority". I saw another thread which suggested putting this in the terminal: 
sudo chown test:test /home/test/.ICEauthority 
sudo chmod 600 /home/test/.ICEauthority

However, I can't open the terminal when I'm signed in as guest because the screen is blank. Can I do it from my other log in (which is perfectly fine), or can I use the keyboard to open the terminal somehow in the guest account?

3.) "There is a problem with the configuration server. (/usr/lib/libgconf24/gconfsanity-check-2 existed with status 256). 

My skill level is basic enough that I was very proud of myself for making new folders in the terminal, so thanks for any ideas!

Amanda

---

### Post by guyal on 2011-04-17
Any help with this??? I have the same problem, but even worst - it happens to me in the ***only*** account I have, so I cannot open terminal at all.

Help, please!!!   :frown:

---

### Post by Amanda8404 on 2011-04-17
I have never been able to figure it out and just gave up. There are a lot of threads about ICE authority (what is that?) that suggest changing the permissions, but I can't figure out how to do that without being able to get into the terminal. That also doesn't seem to actually work for everyone...

Do you know what you did that caused it to happen? I had never tried to use a Guest Account before so I have no idea when it became impossible.

---

### Post by john.soper on 2011-04-17
Hi, I have the same issue as @guyal.

New install of 10.10.  I chose to have the one user account created with a password at logon and to have the home folder of that user encrypted.

Then after using the account for a while, checked of the option that said something like 'login without password'.  After that on my next reboot... I chouldn't login to my account. 

Please see this link for the series of screen shots I took of the errors I'm getting ([here]("http://www.dropbox.com/gallery/22777150/1/ubuntu-issue?h=e57fb6")).

The very last screen I get on attempting to log in is just blank... and it stays blank indefinitely... till I reboot the computer.

Please... any assistance would be greatly appreciated.  I'm about ready to just re-install to try and solve the issue.

John

---

### Post by guyal on 2011-04-17
john.soper, looks like you took your screenshots in my computer... ;)

Anyway, in a magical way (ha, I don't like this way, it leaves me with no clue about what happened. Still, better than not solving at all.....) I managed to fix my problem.

Here what I did:

[LIST]
[*]Entered in a recovery mode (then you have a console - hip hip hurray!!)
[*]did [FONT=Courier New]touch[/FONT] for this mysterious missing file .ICEauthority (created a new file)
[*]chmod 700 to my home directory (from some reason it was 500)
[/LIST]
Then I turned it off and on again.
Working, but - NOTHING under my home directory!!! Lost everything - environment, documents, desktop...
So I changed the password again (this is how everything started), this time through console ([FONT=Courier New]sudo passwd[/FONT]) and restarted again.

Guess what - magic!! Everything returned.

So now my big big question mark - what the hell happened???
If somebody has a clue, please let me know. It is very strange, at least I got it to work. 
Tomorrow I buy a new external hard-drive... ;)

---

### Post by Amanda8404 on 2011-04-17
It would be really cool if someone was able to explain what it all means to us newbies - a lot of times I am able to fix things in these weird ways but I feel like I haven't learned very much so the next time there is a problem I don't know where to start. Also I don't make any progress on describing problems to other people because I am not sure what the important details were the last time. Reading through the tutorials doesn't help with learning the basic troubleshooting stuff because the problems are often so specific. That would be a neat Ubuntu book - taking common problems that people have on the forums and explaining the mechanics behind them instead of just how to fix them. At least for those of us who are interested in learning more about how the operating system really works.

---

### Post by john.soper on 2011-04-17
Thanks for your post guyal.  I was able to boot into rescue console mode and log into my jhsoper account. 

I ran the commands suggested... then rebooted and tried to login again at the GUI... no dice! :(

I think my problem has to do with the fact that I chose to encrypt my home directory and since I'm not prompted for my password on login of the GUI, my home directory isn't decrypted and then the GUI login process cannot find the files in my home directory and freezes.

Since I can get access to my files in my home directory when I login via the rescue console, does anyone out there know if there is a setting in a file somewhere in my home directory that I can edit to allow the GUI to prompt me for my password again?

Thanks again for any help offered!

John

---

### Post by RJ12 on 2011-04-17
> **john.soper said:**
> Thanks for your post guyal.  I was able to boot into rescue console mode and log into my jhsoper account. 

I ran the commands suggested... then rebooted and tried to login again at the GUI... no dice! :(

I think my problem has to do with the fact that I chose to encrypt my home directory and since I'm not prompted for my password on login of the GUI, my home directory isn't decrypted and then the GUI login process cannot find the files in my home directory and freezes.

Since I can get access to my files in my home directory when I login via the rescue console, does anyone out there know if there is a setting in a file somewhere in my home directory that I can edit to allow the GUI to prompt me for my password again?

Thanks again for any help offered!

John

You are absoulutley right, since your home folder is encrypted it can't access your files. I wish there was more of a warning when turning on autologin....

---

### Post by john.soper on 2011-04-17
So... anyone know how I get the GUI login process to prompt me for my password again so that my home directory gets decrypted?

I have access to all files when I login under the rescue console... so I'm sure there's a setting in some file somewhere that I should be able to edit to allow me to do this again.

Thanks,
John

---

### Post by Leppie on 2011-04-17
John,
try booting into the recovery console and then issue the following coommands (presuming your username is jhsoper as you indicated before):
```
mv /home/jhsoper/.ICEauthority /home/jhsoper/.ICEauthority.bak
passwd jhsoper
```
type in the new password twice and reboot.

---

### Post by john.soper on 2011-04-17
Thanks for the suggestion Leppie.  

Gave it a try... didn't help.  Same issue when I try to login via the GUI.  It won't prompt me for the password then is gets the series errors as I originally posted and then just blank background.

---

### Post by Leppie on 2011-04-17
sorry to hear it didn't work, you could try to remove the automatic login by booting into the recovery console and issue this command:
```
dpkg-reconfigure gdm
```

---

### Post by john.soper on 2011-04-17
Leppie... thanks for all your help.

Did the wimpy thing and re-installed Ubuntu over-top of what I had.

I'm back up and running again!!

Thanks again,
John

---

### Post by Leppie on 2011-04-18
haha, well glad you've got a working system again :)

---

