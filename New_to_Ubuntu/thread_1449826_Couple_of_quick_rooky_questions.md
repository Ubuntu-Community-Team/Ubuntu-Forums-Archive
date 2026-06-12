---
title: "Couple of quick rooky questions"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by Tidus0515 on 2010-04-08
First...whenever I sudo nautilus to browse as root...it permanently gives sudo access therefore on. For example...I run terminal and sudo nautilus. Password prompt and then it opens up the root browser. But when I exit and I go close terminal and later sudo something else it no longer asks me for my password. It, for some reason, I guess saves my previous entry for the future entries. How do I change this? It goes away after rebooting and requires me to reenter my password again but once I sudo nautilus and enter password it continues to no longer require passwords for sudo commands. How odd. 

Another thing. I have my "secret don't want anybody to see" files encrypted and password protected with cryptkeeper. But....I removed the launcher from the menu settings and deleted it off the list so nobody can see it. I copied the launcher to a hidden folder then chmod 000 the folder so I have to be in sudo nautilus in order to even navigate to the launcher of cryptkeeper to load it. Is this safe enough? This is why I am wondering about the above question because I sudo nautilus to get to my hidden stuff lol. thanks!

---

### Post by phidia on 2010-04-08
Take a look at the man pages for sudo from the community docs [here]("http://manpages.ubuntu.com/manpages/hardy/man8/sudo_root.8.html").
I think that will give you more to think about with your security needs. As far as sudo not asking for a password there is a default time set in-I think it's only a few minutes-so once having entered your password you won't have to until that time is up.
See [this manpage]("http://manpages.ubuntu.com/manpages/hardy/man8/sudo.8.html") for the timestamp options.

---

### Post by sisco311 on 2010-04-08
After using sudo the authorization is kept for a brief period (15 minutes by default). You can set the timestamp_timeout in the sudoers file. 
To edit the file, run:
```
sudo VISUAL=gedit visudo
```

Set the timout to 0 to always prompt for a password:
```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset,**timestamp_timeout=0**

# Host alias specification
...
```

Setting a "private home" for your user should be more than enough to prevent other users from accessing your files:
```
chmod 0700 $HOME
```

See:
[uhelp]community/FilePermissions[/uhelp]
[thread=510812]Ubuntu Security[/thread]

---

### Post by undecim on 2010-04-08
> **sisco311 said:**
> Setting a "private home" for your user should be more than enough to prevent other users from accessing your files:
```
chmod 0700 $HOME
```

I'd like to point out that this only keeps out other people logged onto the system. If someone were to steal your computer and look at the drive directly, or even just use a live cd, they could still access your files, so encryption is still a good idea for personal files. 

Also, removing the cryptkeeper launcher from your menu won't take it out of everyone else's menu if there are multiple user accounts on the computer.

---

### Post by Tidus0515 on 2010-04-08
thank you for all your replies! Gosh I love this community already...such nice people not like others! Anyways, yes my user name is the only one in existance so chmod 0700 probably wouldn't suffice. And there isn't any other menus in which the encyptor program would appear. So then what do you think is that a good idea? chmod 000 to a folder and then sudo nautilus to browse to the launcher of the encrypt program? Or is there a way to give the gnome browser root permissions to avoid having to sudo nautilus everytime. 

I learned that sudo -k can kill the time needed for a password but I didn't know you could edit the actual timestamp to 0....I am gonna check that out. Thanks guys you are awesome!

Also...if you have any further suggestions to making it harder for someone to find those files I am all ears! :) thanks again!

Edit: Yes I edited the timestamp using your recommendation and it worked! Now it requires a password each time! awesome!

---

### Post by da burger on 2010-04-08
Two things. Firstly when launching graphical applications your should really use gksudo instead of sudo.
Secondly this is a very weak security measure but it might help you a bit. If you rename a file to have a dot in front of it it becomes hidden. Whilst it is easy to make these visible again someone would have to know that there were hidden files.

---

### Post by Tidus0515 on 2010-04-08
This works too! Thanks a lot for the .folder hidden tip! Had to look around though for the ctrl H hot key command. awesome! One more thing...after I do sudo su in terminal to access root...can anybody tell me how to return to the sudoer acct without exiting terminal?

---

### Post by mcduck on 2010-04-08
> **Tidus0515 said:**
> This works too! Thanks a lot for the .folder hidden tip! Had to look around though for the ctrl H hot key command. awesome! One more thing...after I do sudo su in terminal to access root...can anybody tell me how to return to the sudoer acct without exiting terminal?

Use the "exit" command. :)

And, by the way, to open a root session in a terminal you'd better use "sudo -i" instead of "sudo su" or "sudo -s". That way root user's environment will be set correctly and you don't risk possibly messing your actual user account with root permissions.

Edit: Also, you don't really have to worry about people seeing the Cryptkeeper in the menu, as the actual encrypted files can be anywhere, and even if somebody finds them (or Cryptkeeper in your menu) he won't be able to read the files without knowing the password you set in Cryptkeeper. That's pretty much the very idea of encrypting files...

---

### Post by Steven_S on 2010-04-08
> **da burger said:**
> Two things. Firstly when launching graphical applications your should really use gksudo instead of sudo.
Secondly this is a very weak security measure but it might help you a bit. If you rename a file to have a dot in front of it it becomes hidden. Whilst it is easy to make these visible again someone would have to know that there were hidden files.

Great tip - thanks! 

And a little question in-between: why is gksudo different / safer than sudo? I read that comment all the time, but sofar, I haven't come across the reason why...

---

### Post by sisco311 on 2010-04-08
> **Tidus0515 said:**
> This works too! Thanks a lot for the .folder hidden tip! Had to look around though for the ctrl H hot key command. awesome! One more thing...after I do sudo su in terminal to access root...can anybody tell me how to return to the sudoer acct without exiting terminal?

Instead of sudo su use:
```
sudo -i
```
to exit from the root shell type: 
```
exit
```or press Ctrl+d.

See: 
[uhelp]community/RootSudo[/uhelp]
And or a brief overview of some of the differences between su, su -, and sudo -{i,s} [unutbu's post]("http://ubuntuforums.org/showpost.php?p=6188826&postcount=4").

---

### Post by mcduck on 2010-04-08
> **Steven_S said:**
> Great tip - thanks! 

And a little question in-between: why is gksudo different / safer than sudo? I read that comment all the time, but sofar, I haven't come across the reason why...

gksudo is made to be used with graphical applications, so it loads root user's settings for graphical apps correctly. Sudo doesn't know anything about GUI stuff, and you end running graphical applications with root's permissions, but using your own user's profile and configuration files. This can cause programs overwriting your normal user's configuration files with root permissions, with the result that you aren't able to change the settings or use the program any more as your normal user. Or even log into your user account at all, in worst situations.

While some programs don't cause any problems when started with sudo (Gedit doesn't which is why you so often see people telling you to run "sudo gedit"), others do and it's just easier and simpler to always use "gksudo" with GUI apps tan to try to rember which apps work and which break things if started with sudo.

Pretty much the same thing with "sudo -i" for starting a root session in terminal.

Simple "sudo" is only really good for executing a single command.

---

### Post by Tidus0515 on 2010-04-08
> **mcduck said:**
> Use the "exit" command. :)

And, by the way, to open a root session in a terminal you'd better use "sudo -i" instead of "sudo su" or "sudo -s". That way root user's environment will be set correctly and you don't risk possibly messing your actual user account with root permissions.

Edit: Also, you don't really have to worry about people seeing the Cryptkeeper in the menu, as the actual encrypted files can be anywhere, and even if somebody finds them (or Cryptkeeper in your menu) he won't be able to read the files without knowing the password you set in Cryptkeeper. That's pretty much the very idea of encrypting files...


Ok I think I understand now to use sudo -i instead of sudo su or sudo -s, but why is it exactly better? I am not sure I understand the difference and what I may potentially harm when using sudo su instead. But I will use sudo -i from now on...I just want to know what it is I am risking by using sudo su. And yes you are right it may be encrypted but seeing the encryption program in the menu leads people to think that you are hiding something. I'd rather that only I know I'm hiding something. E.I. if my bud sees that in the system tools menu, he may not be able to find it but he will think "ok this guy has something hidden but damn I don't know the password" whereas the other method nobody knows the better.

---

### Post by mcduck on 2010-04-08
> **Tidus0515 said:**
> Ok I think I understand now to use sudo -i instead of sudo su or sudo -s, but why is it exactly better? I am not sure I understand the difference and what I may potentially harm when using sudo su instead. But I will use sudo -i from now on...I just want to know what it is I am risking by using sudo su. And yes you are right it may be encrypted but seeing the encryption program in the menu leads people to think that you are hiding something. I'd rather that only I know I'm hiding something. E.I. if my bud sees that in the system tools menu, he may not be able to find it but he will think "ok this guy has something hidden but damn I don't know the password" whereas the other method nobody knows the better.
from sudo manual:
> 
The -i (simulate initial login) option runs the shell specified in
the passwd(5) entry of the user that the command is being run as.
The command name argument given to the shell begins with a - to
tell the shell to run as a login shell. sudo attempts to change to
that user&#8217;s home directory before running the shell. It also ini&#8208;
tializes the environment, leaving TERM unchanged, setting HOME,
SHELL, USER, LOGNAME, and PATH, and unsetting all other environment
variables. Note that because the shell to use is determined before
the sudoers file is parsed, a runas_default setting in sudoers will
specify the user to run the shell as but will not affect which
shell is actually run. 

So, using "sudo -i" works *exactly* as if you had just logged in as root. "sudo su" and "sudo -s" don't. For example "sudo -s" still uses your normal users configuration files and environment variables.

For example run "sudo -s", and then "echo $HOME" (which tells the current user's home directory). Then exit, and repeat this time using "sudo -i" instead. First one reports the home directory as your normal user's home, while second one gives root's home directory.

---

### Post by Tidus0515 on 2010-04-08
> **mcduck said:**
> from sudo manual:


So, using "sudo -i" works *exactly* as if you had just logged in as root. "sudo su" and "sudo -s" don't. For example "sudo -s" still uses your normal users configuration files and environment variables.

For example run "sudo -s", and then "echo $HOME" (which tells the current user's home directory). Then exit, and repeat this time using "sudo -i" instead. First one reports the home directory as your normal user's home, while second one gives root's home directory.
Makes perfect sense now. So then using sudo su or -s, any modifications will be made to the sudoers home folder which may cause a disagreement of permissions if apps are installed under those environments...whereas sudo -i makes the adjustments to the root home folder instead. Am I understanding this correctly? I have been using sudo su for a bit (couple of days) but have not made any installations just to open certain files..I should be ok no? As long as I continue using sudo -i from now on? Thanks for your help btw...

---

### Post by Paddy Landau on 2010-04-08
It's not recommended to use sudo -i, but rather to use sudo (or gksu) each time you need to run a command as root.

The reason is really simple: You don't forget that you're logged in as root!

I have never had the need or even the desire to use sudo -i.

---

### Post by mcduck on 2010-04-08
> **Tidus0515 said:**
> Makes perfect sense now. So then using sudo su or -s, any modifications will be made to the sudoers home folder which may cause a disagreement of permissions if apps are installed under those environments...whereas sudo -i makes the adjustments to the root home folder instead. Am I understanding this correctly? I have been using sudo su for a bit (couple of days) but have not made any installations just to open certain files..I should be ok no? As long as I continue using sudo -i from now on? Thanks for your help btw...

yes, you have understood it correctly. Using wrong command runs the programs with root's permissions, but using your normal user's home directory and configuration files. So if the programs save any settings to the config files they overwrite your user's files instead of writing into root's config files.

So just use gksudo and sudo -i and you don't worry about such problems.

Of course Paddy Landau's point about using "sudo" on each command instead of running a root session is also valid one, but I personally never leave a root session open any longer than for the time I really need it anyway, and I have also configured the prompt to be different color for different users (green for my normal user, red for root. In addition I always set the background color in Nautilus to red for root user) so there's no chance of ever mistaking which user is logged in a terminal. This kind of things pretty much depend on the person who's actually using the computer.

---

### Post by Tidus0515 on 2010-04-08
ok awesome. Thanks a bunch guys for clearing this up for me. I really appreciate it. Now I'm running into another minor issue i'd like to work around. If I run the cryptkeeper under the gksudo nautilus window I get a set of keys icon whereas if I run it from normal I get the padlock. now I understand this is because of the root/normal use of nautilus and the different program settings. Fine...I get that. My issue is this. I have an encrypted folder...and the folder within the encrypted folder I want to chmod it to 000 to require a root nautilus to go into that folder within the encrypted folder. For instance, "Stuff" is the encrypted folder and ".asd" is the folder I want to chmod. When mounting stuff through cryptkeepor I run "sudo chmod 000 stuff/.asd" and it gives me a permissions error. I figured since it was encrypted...so I pulled ".asd" out of "stuff" and put it in "home" and ran "sudo chmod 000 .asd" and it successfully works. However, since I chmodded it I now need root nautilus to cut it back into the "stuff" folder. however, root nautilus does not see the "stuff" folder...odd....any ideas?

---

### Post by mcduck on 2010-04-08
The problem is that if you use "gksudo nautilus" to start the file manager, then not only the file manager but also every program you open through it will run as root. So you have configured Cryptkeeper as your normal user, but you end running it as root.

My suggestion is that instead of hiding the program launcher into a directory owned by root you just get rid of the launcher completely, and instead just use a terminal or the Run dialog (opened with Alt-F2) to start the Cryptkeeper. That would also be less work to get it started than your current approach is. If you are worried about other people seeing the startup command you could even create a less suspicious alias for Cryptkeeper and use that to start it.

..although it might be a less work to simply not let other people use your own account, and instead either create a separate user account for them to use or log your friends into the Guest session (click the shutdown button in top right corner of the screen and select "Guest Session") when they want to use your computer.. :)

---

### Post by Tidus0515 on 2010-04-08
> **mcduck said:**
> The problem is that if you use "gksudo nautilus" to start the file manager, then not only the file manager but also every program you open through it will run as root. So you have configured Cryptkeeper as your normal user, but you end running it as root.

My suggestion is that instead of hiding the program launcher into a directory owned by root you just get rid of the launcher completely, and instead just use a terminal or the Run dialog (opened with Alt-F2) to start the Cryptkeeper. That would also be less work to get it started than your current approach is. If you are worried about other people seeing the startup command you could even create a less suspicious alias for Cryptkeeper and use that to start it.

..although it might be a less work to simply not let other people use your own account, and instead either create a separate user account for them to use or log your friends into the Guest session (click the shutdown button in top right corner of the screen and select "Guest Session") when they want to use your computer.. :)

I like the alt f2 idea...but how do you assign a different alias to a program? And upon doing so.....will it still launch if "cryptkeeper" is entered instead of the alternative alias?

And I guess I did not make myself clear in my question. I understand the whole running things as root/user things now, what I am wondering is if there is a way to chmod 000 a folder within the encrypted folder (when executed as regular user) to need root permissioned nautilus to access it. For some reason, since the cryptkeepor was executed under the normal user environment, the root nautilus window doesn't list that directory when browsing.

---

### Post by sisco311 on 2010-04-08
Oh, I guess I understand now, you let others to use your primary (admin) account & you want to hide your encrypted files from them. 

Then why, as mcduck already suggested, don't you create a second account for them?

Or you could create a second "super secret" account where you can store the encrypted files.

---

### Post by Tidus0515 on 2010-04-08
> **sisco311 said:**
> Oh, I guess I understand now, you let others to use your primary (admin) account & you want to hide your encrypted files from them. 

Then why, as mcduck already suggested, don't you create a second account for them?

Or you could create a second "super secret" account where you can store the encrypted files.

It's not that I let others use my computer as I do not, it's just I am a frequent torrent user and have some files that are of questionable legality and simply want them to be extra extra hidden just in case anything ever happened to my computer. (take it to a repair shop or something). 

The goal that I am seeking is to chmod 000 a folder located within an encrypted folder (when cryptkeeper is executed as normal user) to browse it with a root nautilus. Is this possible? 

Or..how do I change program names. I would hate for someone to see that I have cryptkeeper by just hitting alt f2 and them putting in cryptkeeper. Can I change the name/command of cryptkeeper to something else?

---

### Post by mcduck on 2010-04-08
> **Tidus0515 said:**
> I like the alt f2 idea...but how do you assign a different alias to a program? And upon doing so.....will it still launch if "cryptkeeper" is entered instead of the alternative alias?

And I guess I did not make myself clear in my question. I understand the whole running things as root/user things now, what I am wondering is if there is a way to chmod 000 a folder within the encrypted folder (when executed as regular user) to need root permissioned nautilus to access it. For some reason, since the cryptkeepor was executed under the normal user environment, the root nautilus window doesn't list that directory when browsing.

Aliases can be defined in your Bash configuration files, like ~/.profile and ~/.bashrc. Just add something like this to the end of the file:
```
alias nothingsuspicious=cryptkeeper
```

And yes, the original command will still work, alias just defines an alternative name for the same command. But you can of course remove Cryptkeeper from the menu and if you never use the original command then it would be pretty hard for anybody to figure it out unless they are specifically looking for it.

The other problem is probably related to how EncFS and Fuse work, the directory where the unencrypted files are visible doesn't actually exist anywhere, which is why root (or any other user) can't see it. The only directory that really is there on the file system is the encrypted one. I'm not sure if there's any way around that, I doubt it was ever intended to work for anything else than encrypting single user's files.

edit: if you also want to stop the original "cryptkeeper" command from working, it's actually possible to create an alias with the same name, and make it do something else than start the cryptkeeper. for example "alias cryptkeeper='echo "The program Cryptkeeper is currently not installed. You can install it by typing: sudo apt-get install cryptkeeper"' would pretty much make it seem as if Cryptkeeper wasn't installed.. ;)

edit2: actually doing both those aliases wouldn't probably actually work, as the actual command for one alias would be the same as alias for the other command. You'd end with both commands running the echo thing.. I suppose there must be a way around that but I can't think of one right now. Perhaps a symbolic link for /usr/bin/cryptkeeper, with a different name and then just setting an alias to hide the original cryptkeeper command would do the trick but I haven't got Cryptkeeper installed so I'm not quite sure if it would work correctly when started from a symlink with a different name.

---

### Post by Tidus0515 on 2010-04-08
> **mcduck said:**
> Aliases can be defined in your Bash configuration files, like ~/.profile and ~/.bashrc. Just add something like this to the end of the file:
```
alias nothingsuspicious=cryptkeeper
```And yes, the original command will still work, alias just defines an alternative name for the same command. But you can of course remove Cryptkeeper from the menu and if you never use the original command then it would be pretty hard for anybody to figure it out unless they are specifically looking for it.

The other problem is probably related to how EncFS and Fuse work, the directory where the unencrypted files are visible doesn't actually exist anywhere, which is why root (or any other user) can't see it. The only directory that really is there on the file system is the encrypted one. I'm not sure if there's any way around that, I doubt it was ever intended to work for anything else than encrypting single user's files.

Ok. That makes sense. The only possible functions that may to solve my minor issue are: Is there a way to completely rename an application? and is there a way to give root authority to GUI commands like (open) or (cut) and (paste) when navigating through the user nautilus window. If not...then I give up on the subject and am satisfied with what I have. Thanks!

---

### Post by mcduck on 2010-04-08
If you install the "nautilus-gksu" -package you'll get an option to open a file as root in the right-click menu (I'm not sure how well this works with EncFS, you could try if you want to). But you can't change the permissions nautilus runs with, it either runs as one user or as other, not both. So no Copy/Paste as root when you run the Nautilus as your own user.

..what comes to renaming a command, I was quicker than you, see my edited post above.. ;)

(by the way you can even make the aliases system-wide if you define them in /etc/bashrc or /etc/profile, but in that case be *very* careful with what you do so that you don't break anyhting. Remeber that all the launchers and other programs will still try to use the original names for commands, they don't know about any aliases)

---

### Post by Tidus0515 on 2010-04-08
> **mcduck said:**
> Aliases can be defined in your Bash configuration files, like ~/.profile and ~/.bashrc. Just add something like this to the end of the file:
```
alias nothingsuspicious=cryptkeeper
```And yes, the original command will still work, alias just defines an alternative name for the same command. But you can of course remove Cryptkeeper from the menu and if you never use the original command then it would be pretty hard for anybody to figure it out unless they are specifically looking for it.

The other problem is probably related to how EncFS and Fuse work, the directory where the unencrypted files are visible doesn't actually exist anywhere, which is why root (or any other user) can't see it. The only directory that really is there on the file system is the encrypted one. I'm not sure if there's any way around that, I doubt it was ever intended to work for anything else than encrypting single user's files.

edit: if you also want to stop the original "cryptkeeper" command from working, it's actually possible to create an alias with the same name, and make it do something else than start the cryptkeeper. for example "alias cryptkeeper='echo "The program Cryptkeeper is currently not installed. You can install it by typing: sudo apt-get install cryptkeeper"' would pretty much make it seem as if Cryptkeeper wasn't installed.. ;)

edit2: actually doing both those aliases wouldn't probably actually work, as the actual command for one alias would be the same as alias for the other command. You'd end with both commands running the echo thing.. I suppose there must be a way around that but I can't think of one right now. Perhaps a symbolic link for /usr/bin/cryptkeeper, with a different name and then just setting an alias to hide the original cryptkeeper command would do the trick but I haven't got Cryptkeeper installed so I'm not quite sure if it would work correctly when started from a symlink with a different name.
  
Ok I am following you kind of but not really. I understand the issue with the two aliases causing a problem when launched. But.....step back for a second. I have yet to find out how to create one alias. I cannot find ~/.profile or ~/.bashrc. Where are these? I've hit ctrl h to show hidden files but no go. I'm running ubuntu 9.10. And if you know how to make a symbolic link for another program then can you explain how to do that? There are no other applications running the command (as I installed it after a stable system was running) so I don't mind breaking the original command. I'm sure if you can do a symbolic link for another app then it might be the same principal when applied to cryptkeeper.

---

### Post by mcduck on 2010-04-08
> **Tidus0515 said:**
> Ok I am following you kind of but not really. I understand the issue with the two aliases causing a problem when launched. But.....step back for a second. I have yet to find out how to create one alias. I cannot find ~/.profile or ~/.bashrc. Where are these? I've hit ctrl h to show hidden files but no go. I'm running ubuntu 9.10. And if you know how to make a symbolic link for another program then can you explain how to do that? There are no other applications running the command (as I installed it after a stable system was running) so I don't mind breaking the original command. I'm sure if you can do a symbolic link for another app then it might be the same principal when applied to cryptkeeper.

Both ~/.profile and ~/.bashrc are hidden files inside your home directory, and they should definitely be there by default. If for some reason the files don't exist, you can just create them.

To make the symlink first check what the executable file for Cryptkeeper is. (I'll assume here that it's "/usr/bin/cryptkeeper", which will most likely be correct).

Then just open a terminal and run "sudo ln -s /usr/bin/cryptkeeper /usr/bin/nothingsuspicious". You might have to make the link executable afterwards, by running "sudo chmod +x /usr/bin/nothingsuspicious".

After that you should be able to run cryptkeeper using the name of the symlink you created, and hide the original cryptkeeper command with an alias. 

(by the way, you can test the aliases by just running the same alias command in a terminal. It will only work for that terminal window and disappear when you close the terminal, which is why you need to add it into one of those configuration files to make it permanent)

---

### Post by Tidus0515 on 2010-04-08
> **mcduck said:**
> Both ~/.profile and ~/.bashrc are hidden files inside your home directory, and they should definitely be there by default. If for some reason the files don't exist, you can just create them.

To make the symlink first check what the executable file for Cryptkeeper is. (I'll assume here that it's "/usr/bin/cryptkeeper", which will most likely be correct).

Then just open a terminal and run "sudo ln -s /usr/bin/cryptkeeper /usr/bin/nothingsuspicious". You might have to make the link executable afterwards, by running "sudo chmod +x /usr/bin/nothingsuspicious".

After that you should be able to run cryptkeeper using the name of the symlink you created, and hide the original cryptkeeper command with an alias. 

(by the way, you can test the aliases by just running the same alias command in a terminal. It will only work for that terminal window and disappear when you close the terminal, which is why you need to add it into one of those configuration files to make it permanent)
Sir you are definitely helping me out greatly here. Almost there. I have successfully created the symlink. So now two executables run the program and they are "cryptkeeper" and "hide123" (lol). I have aliased cryptkeeper to return "this program sucks" on the terminal only and am ready to apply it permanently. So...which file do I edit? the bash or the profile? (btw the reason I couldn't find them b4 was because I was looking for folders not actual files)

---

### Post by sisco311 on 2010-04-08
> **Tidus0515 said:**
> It's not that I let others use my computer as I do not, it's just I am a frequent torrent user and have some files that are of questionable legality and simply want them to be extra extra hidden just in case anything ever happened to my computer. (take it to a repair shop or something). 



Then changing the permissions of the file doesn't provide any extra security. If they have physical access they have root access anyway.

---

### Post by Tidus0515 on 2010-04-08
> **sisco311 said:**
> Then changing the permissions of the file doesn't provide any extra security. If they have physical access they have root access anyway.

really? without knowledge of my admistrator password? How does that work? Because I have been having to put in my password for every sudo root enabling command I have been giving. and my root doesn't have a pw so they can't login as root.

Changing the permissions would work so I would have to "open as adminstrator" or "gksudo nautilus" in order to open the folder that was chmodded to 000. and that would cause a password to be needed. ...so...someone with my computer couldn't access that folder...as they would have my user permissions and not root...at least not without my pw.

---

### Post by sisco311 on 2010-04-08
> **Tidus0515 said:**
> really? without knowledge of my admistrator password? How does that work? Because I have been having to put in my password for every sudo root enabling command I have been giving. and my root doesn't have a pw so they can't login as root.

Changing the permissions would work so I would have to "open as adminstrator" or "gksudo nautilus" in order to open the folder that was chmodded to 000. and that would cause a password to be needed. ...so...someone with my computer couldn't access that folder...as they would have my user permissions and not root...at least not without my pw.

Recovery mode (init=/bin/bash kernel parameter), a LiveCD...

[thread=989517]Physical access is root access[/thread]

Encryption is your greatest asset. Just use a strong password.

---

### Post by Tidus0515 on 2010-04-08
> **sisco311 said:**
> Recovery mode (init=/bin/bash kernel parameter), a LiveCD...

[thread=989517]Physical access is root access[/thread]

Encryption is your greatest asset. Just use a strong password.

Good point...but no physical access does NOT automatically mean root access my friend. Set a pw on root so recovery prompts for pw (or simply remove recovery from boot menu). Then...change boot order in bios to boot from hd first and set a pw to be required in order to change the boot sequence or to manually boot from a source.

No live cd option
No recovery option
muahah

---

### Post by sisco311 on 2010-04-08
removing the CMOS battery and cutting power from the machine for 15 minutes resets the BIOS.

---

### Post by Tidus0515 on 2010-04-08
> **sisco311 said:**
> removing the CMOS battery and cutting power from the machine for 15 minutes resets the BIOS.
Even on laptops?

---

### Post by sisco311 on 2010-04-08
> **Tidus0515 said:**
> Even on laptops?

yes, you can disassemble a laptop too.

---

### Post by Tidus0515 on 2010-04-08
> **sisco311 said:**
> yes, you can disassemble a laptop too.
well at any rate....the files are encrypted.:)..the only reason I was wanting to be able to chmod the launcher-containing folder was to hide the fact that I was hiding something...if that makes sense. So...if someone happens to get around all the little blocks...they still need the encryption password...ha!

Now..the recovery root access problem in grub..that isn't present in grub 1.97 is it? I just rebooted and tried it out and could not for the life of me figure out how to access root using the recovery menu. I already password protected grub so if they want to push 'e' or load windows they have to use a password. I think the recovery thing is fixed in the new grub?

---

### Post by Tidus0515 on 2010-04-08
> **mcduck said:**
> Both ~/.profile and ~/.bashrc are hidden files inside your home directory, and they should definitely be there by default. If for some reason the files don't exist, you can just create them.

To make the symlink first check what the executable file for Cryptkeeper is. (I'll assume here that it's "/usr/bin/cryptkeeper", which will most likely be correct).

Then just open a terminal and run "sudo ln -s /usr/bin/cryptkeeper /usr/bin/nothingsuspicious". You might have to make the link executable afterwards, by running "sudo chmod +x /usr/bin/nothingsuspicious".

After that you should be able to run cryptkeeper using the name of the symlink you created, and hide the original cryptkeeper command with an alias. 

(by the way, you can test the aliases by just running the same alias command in a terminal. It will only work for that terminal window and disappear when you close the terminal, which is why you need to add it into one of those configuration files to make it permanent)
this is working well. I thank you for all the help you have provided me. The only quirk is that it is only working when running cryptkeeper from terminal. When I launch it from terminal it gives me the programmed error. Cool. all is well there. However, when I run it from alt f2..it loads. Is there another file I can modify so that this hack also applies to GUI commands? Thanks.

---

### Post by mcduck on 2010-04-09
> **Tidus0515 said:**
> this is working well. I thank you for all the help you have provided me. The only quirk is that it is only working when running cryptkeeper from terminal. When I launch it from terminal it gives me the programmed error. Cool. all is well there. However, when I run it from alt f2..it loads. Is there another file I can modify so that this hack also applies to GUI commands? Thanks.

put the alias stuff into ~/.profile, and it should work even outside of terminals (although you need to log out and back again before it starts to work, since .profile is only executed when you log in, while .bashrc runs every time you open a terminal.

---

### Post by Tidus0515 on 2010-04-09
> **mcduck said:**
> put the alias stuff into ~/.profile, and it should work even outside of terminals (although you need to log out and back again before it starts to work, since .profile is only executed when you log in, while .bashrc runs every time you open a terminal.

Did this....still getting a positive execution of the program when using alt f2 launch method. Here is the end of my .profile:
```

    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
alias cryptkeeper='echo "The program Cryptkeeper is currently not installed. You can install it by typing: sudo apt-get install cryptkeeper"'

```I don't know why it is not working?

---

### Post by mcduck on 2010-04-09
> **Tidus0515 said:**
> Did this....still getting a positive execution of the program when using alt f2 launch method. Here is the end of my .profile:
```

    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
alias cryptkeeper='echo "The program Cryptkeeper is currently not installed. You can install it by typing: sudo apt-get install cryptkeeper"'

```I don't know why it is not working?

I just tried it, and indeed the Alt-F2 dialog doesn't seem to care about aliases...

In that case you could simply try renaming the cyptkeeper's executable file itself to something else, with a bit of luck things might still work without any problems and you wouldn't even need any aliases or symlinks..

---

### Post by Tidus0515 on 2010-04-09
> **mcduck said:**
> I just tried it, and indeed the Alt-F2 dialog doesn't seem to care about aliases...

In that case you could simply try renaming the cyptkeeper's executable file itself to something else, with a bit of luck things might still work without any problems and you wouldn't even need any aliases or symlinks..
  
After trying to find all the roads around we finally found the solution! My friend....thank you for your help. Who would have imagined it would have been such a simple solution. Aliases and symlinks were not even needed. A simple rename and alt f2 no longer recognizes the software as "cryptkeeper". Just renamed under gksudo nautilus and voila! Yes! Thank you thank you!

---

### Post by mcduck on 2010-04-09
Great that it worked for you, while it's simple it sure isn't as smooth way to handle this as I'd like but there's no problems then I suppose it's OK. 

You might run into problems if there are any updates for Cryptkeeper, though, as one of it's files now has different name than what the package management expects, but in that case just rename the executable file back to it's original name when you install the update and back again afterwards.

---

### Post by Tidus0515 on 2010-04-09
> **mcduck said:**
> Great that it worked for you, while it's simple it sure isn't as smooth way to handle this as I'd like but there's no problems then I suppose it's OK. 

You might run into problems if there are any updates for Cryptkeeper, though, as one of it's files now has different name than what the package management expects, but in that case just rename the executable file back to it's original name when you install the update and back again afterwards.

makes sense. that's not hard though. Once again thank you for your help.

---

