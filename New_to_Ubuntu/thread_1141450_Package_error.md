---
title: "Package error"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by lexe-cc on 2009-04-28
Hi,

i have a problem with a package that didnt install correctly. Unfortunatly its not an official ubuntu package. (a .deb file i picked up at the adobe website)

i tried to install adobe-flashplugin using "install_flash_player_10_linux.deb". For some reason my computer froze up and the package didnt install correctly. I tried to remove the package in several ways but without any luck.

This is what i get:
```
lexe@lexe-laptop:~$ sudo apt-get remove adobe-flashpluginReading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
```

i appreciate any help on this one ..
Thanks in advance!
Lexe

---

### Post by hesjnet on 2009-04-28
Maybe you'll want to try aptitude?
```
sudo aptitude remove adobe-flashplugin
```

are you sure this is the name of the package?

---

### Post by lexe-cc on 2009-04-28
Same response:
```
lexe@lexe-laptop:~$ sudo apt-get remove adobe-flashplugin
[sudo] password for lexe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
```

im 100% sure thats the package's name. i also tried: 
```
sudo dpkg --remove --force-remove-reinstreq adobe-flashplugin
```
without any luck.

appreciate your help!

---

### Post by lexe-cc on 2009-04-28
no one?

---

### Post by Zoowey on 2009-04-28
Go into synaptic and in one of the menu options it'll say something like "Fix broken packages" click on that and then hit apply, it should reinstall any broken packages or remove them automatically. If it reinstalls them successfully you should be able to uninstall them if you wish.

If it finds no broken packages try searching for flash within synaptic and if it's there mark it for "complete removal" then hit apply.

Hope this helps.

---

### Post by lexe-cc on 2009-04-28
i tried it before, the problem now is that i cant even open synaptic because of the package.
i think its a big problem because its a package thats not in the repositories.

im not exactly the ubuntu-expert but im not a noob as well (ubuntu user for 2.5 years now) :p 
but i dont have a clue on this one ...
its really annoying because i cant install anything at the moment ...

---

### Post by Zoowey on 2009-04-28
Try completely restarting the computer and then see if synaptic works.

---

### Post by lexe-cc on 2009-04-28
have tried it as well .. no luck :(

---

### Post by Zoowey on 2009-04-28
Wow... sorry. I've had packages mess up during install, and have had many that aren't in the repository fail as well, but never I seen such a negative effect. Only the package itself should be messed up, not the entire installation system.

Specifically what did you try to do to uninstall the package?

---

### Post by lexe-cc on 2009-04-28
i tried 
"sudo apt-get remove"
"sudo dpkg --remove --force-remove-reinstreq"

tried to fix broken dependencies through terminal "sudo apt-get check"

i tried to reinstall the .deb package by double clicking it. giving me the following error: "could not open 'install_flash_player_10_linux.deb'"
"The package might be corrupted or you are not allowed to open the file. Check the permissions of the file."

i never had this many problems before .. seems like it always comes down to the last sentence: 
"E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it."

i sure hope somebody can help me ..
anyways, thanks for you help and patience!

---

### Post by Zoowey on 2009-04-28
Try this in the terminal.

type cd then type the folder where the flash package is in. For example if the package is on your desktop type "cd desktop"

Then use this command.

sudo dpkg -i --force-overwrite install_flash_player_10_linux.deb

---

### Post by lexe-cc on 2009-04-28
```
lexe@lexe-laptop:~/Desktop$ sudo dpkg -i --force-overwrite install_flash_player_10_linux.deb 
(Reading database ... 112795 files and directories currently installed.)
Preparing to replace adobe-flashplugin 10.0.22.87-1 (using install_flash_player_10_linux.deb) ...
update-alternatives: error or eof reading /var/lib/dpkg/alternatives/iceape-flashplugin for update_mode ()
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
update-alternatives: error or eof reading /var/lib/dpkg/alternatives/iceape-flashplugin for update_mode ()
dpkg: error processing install_flash_player_10_linux.deb (--install):
 subprocess new pre-removal script returned error exit status 2
postinst called with argument `abort-upgrade'
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 install_flash_player_10_linux.deb

```

again, failure ..

---

### Post by Zoowey on 2009-04-28
OK.

Once more do cd desktop and try this command.

sudo dpkg --purge install_flash_player_10_linux.deb

---

### Post by lexe-cc on 2009-04-28
```
lexe@lexe-laptop:~/Desktop$ sudo dpkg --purge adobe-flashplugin
dpkg: error processing adobe-flashplugin (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 adobe-flashplugin

```

specifying the file didnt work, i had to specify the package name ..
again it calls for a reinstall .. but i can't make it reinstall :(

---

### Post by Zoowey on 2009-04-28
When you try to open synaptic you said it wont open. But why, like does give you an error. Specifically what happens when you try to open it.

---

### Post by lexe-cc on 2009-04-28
it brings up an messagebox saying: 
An error occurred
The following details are provided:

```
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

```

---

### Post by Zoowey on 2009-04-28
Ok, this time don't link any folders, no cd desktop or anything like that.

Open a new terminal and run this command.

sudo dpkg -- configure -a

---

### Post by lexe-cc on 2009-04-28
that worked, it left no output though ..

---

### Post by Zoowey on 2009-04-28
Cool. Can you open up synaptic and install packages now? I recommend you go into synaptic and check for broken packages and uninstall flash if it's still installed.

---

### Post by lexe-cc on 2009-04-28
i still can't open synaptic. the same error message occurs ..
but i check for broken packages through the terminal. (sudo apt-get check)
again it leaves:
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

this is starting to irritate me .. :)

---

### Post by Zoowey on 2009-04-28
Well you said it worked, what exactly worked?

---

### Post by lexe-cc on 2009-04-28
the following command worked: (it didnt responded with errors)
sudo dpkg --reconfigure -a

pfffffffff ...
again i appreciate your help

---

### Post by Zoowey on 2009-04-28
Well what the commands suppose to do is clear the apt cache, so most likely It wouldn't return any errors but if you still cant install anything or open synaptic then apparently it didn't work.

---

### Post by Zoowey on 2009-04-28
I guess maybe now you could try restarting your computer again after using the command. It may work.

---

### Post by lexe-cc on 2009-04-28
i tried what you said but it didnt work. Seems like its a very hard error to fix ..
i just reinstalled ubuntu because i thought it would make things easier .. and it did.

Sorry that all your advice didnt help me fix my problem but im very thankfull!

thanks again and sorry for the inconvenience ..

---

### Post by MaxIBoy on 2009-05-21
Sorry to bump an old thread, but I had the exact same problem, and I found a solution, so I'm cross-posting here, in case someone else finds this thread who has the same problem. 

[http://www.linuxquestions.org/questions/debian-26/sid-adobe-flasplugin-is-reinstall-required-but-apt-cant-find-archive-for-it-727572/](http://www.linuxquestions.org/questions/debian-26/sid-adobe-flasplugin-is-reinstall-required-but-apt-cant-find-archive-for-it-727572/)

---

### Post by Keeper of the Keys on 2009-10-12
I'm bumping this old thread as no solution has been offered and it should be as regular users may run into this problem.

**How and why can they run into this?:**
When a user visits a site like youtube.com it autodetects the lack of flash and does not offer the browser embedded flash instead presenting the user with a link to the adobe website where they can download and install the not so good (broken) package from adobe.com

Now they have a system that will not upgrade anymore, from their perspective it might as well be broken because they can't even install software anymore.

Unless the user visits a page that is embedding flash the usefull ubuntu dialog that properly installs flash will never be shown and you can't expect a regular (new) user to dive into a terminal and type "apt-get install flashplugin-installer".

I recently installed 9.10 on the laptop of a friend of mine and with all my knowledge of debian and ubuntu could not solve this problem for him over the phone, when he gets me the laptop I will probably try it the ultimate hackish way: editing the dpkg database and deleting the files manually.
However I am hoping that a better solution will be offered here soon, otherwise I will attempt to make a script out of the actions I needed to do so that a fix script can be gotten, bu no promises.

---

### Post by Donnchad on 2009-10-19
I was having this error and fixed it by doing:

```
sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
sudo dpkg-reconfigure adobe-flashplugin --force
sudo dpkg --purge --force-all adobe-flashplugin
```

---

### Post by Keeper of the Keys on 2009-10-19
Ok, I also solved it, slightly different:

I ran and apt update. (after which the dist upgrade also decided to work again)

Then I edited the prerm file (/var/lib/dpkg/info/adobe-flashplugin.prerm), it contains a line:
```

VARIANTS="iceape iceweasel mozilla firefox xulrunner midbrowser xulrunner-addons"

```
Which is the culprit in the failure as update-alternatives fails.

After commenting the line out (adding a '#' to the beginning of the line) removing the package using
```

apt-get remove --purge adobe-flashplugin

```
worked.

---

### Post by nosoupforyou on 2009-11-02
Thank you so much, you just saved my Ubuntu installation! I had mistakenly thought the version from Adobe's web site was newer and I was having trouble with a specific site so I though I would give it a try, figuring I can always just remove it later, not realizing the damage it would cause.

---

### Post by aPaSv5 on 2009-11-17
I had a machine with the same error, only it's spiraled out of control and now I can't do anything -- none of the fixes work.

At first, I decided that I'd install the Adobe flash player from their website as I was unable to get sound while watching a video online.

Having recalled downloading the .tar.gz file in the past, I opted for that version, only to find that the only file contained in the .tar.gz was a single library -- useless without the install script.

Then I decided to try the .deb file, but the install resulted in the very same error as had happened to the original poster of this thread.

I don't really recall specifically what it was that I did after that, but now I can't do anything -- every time I try to mess with the package repository in any way, using any of the supplied programs, I get the whole "E: The package flashplugin-nonfree needs to be reinstalled, but I can't find an archive for it." error.

I've tried editing the .prerm file, but to no avail. Then I tried Donnchad's fix above, and it seemed to work, but I was then left without the flash player, so I tried to (I think) install the swfdec flash player, but that didn't play the video, so then I tried gnash with the same result. Then I tried to install flashplugin-nonfree, again, to no avail.

Now I'm pretty much back where I started and Donnchad's fix no longer works. I even tried (temporarily) removing all the .prerm and other files, but again with no result.

I have tried numerous command-line (and otherwise) means of removing or installing packages, and none of them work. I've tried to use dpkg, apt-get, and aptitude to purge, remove, fix, re-install, and all that, and nothing worked.

---

### Post by aPaSv5 on 2009-11-18
Scratch that, I just re-installed after an hour or two of messing around with the thing.

---

### Post by IanVaughan on 2009-12-19
This is so f-ing pathetic, I just wanted to get a "flash" player, ok, so maybe Adobe isnt the geeks/linux-expects choice, but as a windows user, its what I lean too.

And after reading through 4 pages of problems that I am having, I still cannot update or install.

 
Synaptic Package Manager :> 
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.


> 
sudo dpkg -i --force-all 'install_flash_player_10_linux.deb' 
Selecting previously deselected package adobe-flashplugin.
(Reading database ... 117889 files and directories currently installed.)
Preparing to replace adobe-flashplugin 10.0.32.18-1 (using .../install_flash_player_10_linux.deb) ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing install_flash_player_10_linux.deb (--install):
 subprocess new pre-removal script returned error exit status 2
postinst called with argument `abort-upgrade'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /install_flash_player_10_linux.deb

sudo aptitude purge adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  adobe-flashplugin{p} libnspr4-dev{u} libnss3-dev{u} 
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 13.3MB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
dpkg: error processing adobe-flashplugin (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 adobe-flashplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Writing extended state information... Done



---

### Post by webchimp on 2010-01-20
> **Donnchad said:**
> I was having this error and fixed it by doing:

```
sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
sudo dpkg-reconfigure adobe-flashplugin --force
sudo dpkg --purge --force-all adobe-flashplugin
```

Thank you so much, had tried a couple of other solutions with no success, but this cleared up the problem and I was able to re-install flash through the software center.

---

### Post by kimota.nomis@gmail.com on 2010-04-09
> **Donnchad said:**
> I was having this error and fixed it by doing:

```
sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
sudo dpkg-reconfigure adobe-flashplugin --force
sudo dpkg --purge --force-all adobe-flashplugin
```
Thank you [Donnchad]("http://ubuntuforums.org/member.php?u=618561")! I was having a similar issue with a broken [Portable Linux]("http://rudd-o.com/new-projects/portablelinux") package.

---

