---
title: "could not update ICEauthority"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by sendmethatstuff on 2008-12-25
Hi Everybody
im prety new to this game   so please be patient 
i chose to learn about ubuntu   for the community support 
some of th e staff i work with suggested 
it to me    seems good so far 

    BUT 
when i start i get this message 

could not update ICEauthority file/ home/


it seems to take a long time to get started 
and now with the shut down button does not do a thing 


your help is valued 

:P

---

### Post by Elfy on 2008-12-25
Hi - you could try this - boot into recovery mode from the grub menu. Choose root prompt from the menu, then run these one at a time

```
chown user:user /home/user/.ICEauthority
chmod 644 /home/user/.ICEauthority
exit
```

You must replace user with your username

Now resume from the recovery menu.

---

### Post by deadlockedgamer on 2009-10-12
I have this issue in karmic without the speed or shut down issue. It appears i may have accidentally deleted the folder when showing hidden files. The .ICEauthority file is not there any clue how to fix it?

---

### Post by Terentius on 2009-11-08
I had this problem to in Karmic.

Then I looked if I had the file and it was there.

The problem I had was that I did not have the rights of that file.

So then I changed the rights with GNOME commander from root to my username.

And when I tried to log in again everything was fine and I did not get the error message again.

---

### Post by WuIsMe on 2009-11-09
I've found that, since it's a permissions issue, its possible to log in with the root account, however, when i tried finding the ICEauthority file, it wasn't where I thought it would be.

Does anyone know where find the file?

Also, I boot up with lilo, so how do u access the recovery console from there?

Update: did a search, found a file of same name at /var/lib/gdm/ gonna try changing permissions & see what happens.

---

### Post by Terentius on 2009-11-11
I found the file in my home directory "/home/username/" then I checked "show hidden files" and there it was.

---

### Post by NewKidOnTheBlock on 2010-02-12
> **WuIsMe said:**
> I've found that, since it's a permissions issue, its possible to log in with the root account, however, when i tried finding the ICEauthority file, it wasn't where I thought it would be.

Does anyone know where find the file?

Also, I boot up with lilo, so how do u access the recovery console from there?

Update: did a search, found a file of same name at /var/lib/gdm/ gonna try changing permissions & see what happens.

Hi guys,

New to Linux and loving every minute of it...!

I could also only find the .ICEauthority file in the above-mentioned folder, copied it to my home directory, changed owner and permissions but still seem to be getting the problem...any further ideas?

thx

---

### Post by ario on 2010-02-12
> **forestpiskie said:**
> Hi - you could try this - boot into recovery mode from the grub menu. Choose root prompt from the menu, then run these one at a time

```
chown user:user /home/user/.ICEauthority
chmod 644 /home/user/.ICEauthority
exit
```

You must replace user with your username

Now resume from the recovery menu.

I tried your commands. But just said there is no such file or directory .ICEauthority
My home folder is now empty. just a file named Access-Your-Private-Data.desktop and a README.txt file
I don't know what to do:(

---

### Post by mikewhatever on 2010-02-12
> **ario said:**
> I tried your commands. But just said there is no such file or directory .ICEauthority
My home folder is now empty. just a file named Access-Your-Private-Data.desktop and a README.txt file
I don't know what to do:(

Have you used the correct username, i.e., your real username instead of 'user'? If your home folder is really empty, you maght consider creating a different user instead. From the recovery mode, enter;

adduser username admin

---

### Post by IanVaughan on 2010-03-23
[None of this worked for me!]("http://ubuntuforums.org/showthread.php?p=9016355")

---

### Post by ario on 2010-03-31
Hi guys. I've solved mine. I've booted my pc with a live cd (you say sysresccd) and mounted my root "/" folder. Navigated trough my home folder with it file browser and saw that there were neither .ICEauthority file or folder nor any of my home folder files and folders. Just a file that told me your home folder was encrypted and you must decrypt it by hand to access your files.
This was happened to me and preventing gnome to access any of my personal files in my home folder. Then it used to show that ugly error message.
**Because one day before I've tried to changed my password without any sucess** and so ubuntu tried to first change the encryption passphrase of my home folder that I've set it to be encrypted when I installed my ubuntu. It has changed my passphrase but didn't changed configuration files needed to handle with ecryptfs encryption software and so didn't changed the main password of my user.*(It must be a bug. Maybe we should report it!)*
Now I had my user that continued to login with my old password and my encrypted home folder that needed my new pass phrase to be decrypted.
[B]Thus I've created a new user in my ubuntu. Logined in the new user. I can not remember what commands I exactly entered to access my lost home folder but something like this:
[/B]```
mount -t ecryptfs /home/<lost user encrypted files folder> /home/<new user name>/<some temporary created folder>

```[B]
to manually decrypt my personal files.[/B]
I can remember that my encrypted files were in a location like "/home/.ecryptfs" or etc. and it was a hidden file that I needed to use "View\Show hidden files" in nautilus file manager window to see it. Then it asked my passphrase and I guessed that it must be the password that I've tried to set it as new password of my lost user. It asked some questions and I've tried the default answers except I can remember that I've selected <y> for "Enable file name encryption".
After all it mounted my personal data successfully. Quick I've copied all the stuff in my old home folder "/home/<lost username>" logged out of new user and simply logged in to my old user and said my thanks to God!
Hope this helps.

---

### Post by Flos Headford on 2010-04-08
I have no encrypted folders, so I missed out on some of the woes outlined above. But I did try a method to get rid of the "Could not update ICEauthority file ~/.ICEauthority" and the ensuing error messages. What worked for me was this:
Use a Ubuntu distribution ("live") CD to arrive at a command line interface. Use this to ensure all folders in your home folder (/home/username) have appropriate permissions, and show you their contents when you issue an "ls" command. Then delete the .ICEauthority entry, and a repeat which occurs at /var/lib/gdm (if you're using using Gnome).
Then remove nautilus with ```
sudo apt-get remove nautilus
``` and remove any nautilus folder or file which might remain in your home directory. Then you reboot with ```
sudo shutdown -r now
``` and get back to a command line as before. Then reinstall nautilus by ```
sudo apt-get install nautilus
sudo shutdown -r now
``` and remove the CD. If you are as lucky as me, the system boots and takes you to a login form, after which all is once more tickety-boo.
Best of luck,
Flos

---

### Post by Flos Headford on 2010-04-08
This worked for me:
Use a Ubuntu Live CD to boot up, and choose a command-line (shell) option.
With this, set your $HOME directory (/home/username) permissions to something appropriate (I used 755) and make sure all directories can be listed with the "ls" command. Then remove nautilus with ```
sudo apt-get remove nautilus
``` and delete the .ICEauthority entry in $HOME, and possibly in /var/lib/gdm. Then reboot with ```
sudo shutdown -r now
``` When you choose the same option on boot-up, from the command line you can use ```
sudo apt-get install nautilus
sudo shutdown -r now
``` and retrieve the CD a bit smartish. I do hope you get a clean straight boot and login, as I did!
With thanks to all who helped me,
Phil

---

### Post by mx32 on 2010-04-17
> **forestpiskie said:**
> Hi - you could try this - boot into recovery mode from the grub menu. Choose root prompt from the menu, then run these one at a time

```
chown user:user /home/user/.ICEauthority
chmod 644 /home/user/.ICEauthority
exit
```

You must replace user with your username

Now resume from the recovery menu.

This worked to me. I had the "no update message" and no sound controls.
Now it works fine. thanks.

---

### Post by wasabishot on 2010-04-18
Hello guys
been working on this for many hours and getting desperate.

so its like that
i had this error messege mentioned on top, then got to have the other error messeges related to nautilus and all that.
then i tried to do what said above: entered the live cd. tried to figure out how to open terminal from there, couldn't, so booted from recovery, did all the chown and chmod, deleted bot .ICEauthority files, removed nautilus , restarted, installed nautilus, restarted.

ANNND now it's WORSEEEE
i get the login screen, try to log in, it seems woking, but then going back to the login screen... and so on................

now im working thanks to the ubuntu tryout of the live cd....
without any ability to access my desktop

please help!!!!!!!!!

---

### Post by mjcritchie on 2010-04-20
I have had the same problem twice, both times after updating (currently running 64bit Karmic).

Tried various solutions on the net, but this is the only one that worked for me:

Open a terminal and run:

> sudo chown -R user:user /home/user/.*

Where user is your user_name. This should change ownership of all the hidden files and directories in your home directory to: user:user, as they should be.

This comes courtesy of tommcd over at [this]("http://www.linuxquestions.org/questions/ubuntu-63/karmic-9-10-with-separate-home-partition-caused-could-not-update-iceauthority-798084/") post on LinuxQuestions.org

---

### Post by kuric on 2010-04-27
Thank you, mjcritchie!

[COLOR="Sienna"][B]sudo chown -R user:user /home/user/.*
(Where user is your username)[/B][/COLOR]

This worked for me too. The ICEauthority problem occurred after installing Wine under Ubuntu 9.10. Now it's solved.

**NEW:** Actually, I found out the same problem happens on Ubuntu 10.04 after installing Veetle Player (Wine was not the problem after all). If you install Veetle as root you got this issue on the next reboot.

---

### Post by kaspin on 2010-04-30
[FONT="Comic Sans MS"][COLOR="Blue"][SIZE="2"]My error message referred to "/home/xx/.ICEAuthority" (where xx is my user name). Being simplistic (should that be simple?) I tried clicking the following:
Places/computer/File system/home
In the home directory I right clicked on my user file, selected properties/permissions. I then changed "folder access" to read "Create and delete files" under sections "Owner", "Group", and "Others" . Close. Problem sorted....
Kaspin[/SIZE][/COLOR][/FONT]

---

### Post by blinchi on 2010-05-09
> **kuric said:**
> Thank you, mjcritchie!

[COLOR=Sienna][B]sudo chown -R user:user /home/user/.*
(Where user is your username)[/B][/COLOR]

This worked for me too. The ICEauthority problem occurred after installing Wine under Ubuntu 9.10. Now it's solved.

**NEW:** Actually, I found out the same problem happens on Ubuntu 10.04 after installing Veetle Player (Wine was not the problem after all). If you install Veetle as root you got this issue on the next reboot.
I've got Ubuntu 10.04 64 bits version, and i installed the Veetle player like you ( and this damn  error appears :'( ) , i've tryed to put this command
[COLOR=Sienna][B]sudo chown -R user:user /home/user/.*

and i've got this : 

chown: cannot access `/home/user/./.gvfs': Permission denied
chown: cannot access `/home/user/.gvfs': Permission denied

*in user appears my real user 


Please someone knows what's happening and how to fix it ? ( i'm new in ubuntu / Linux ) Thank you , and sorry for my english ^^

[/B][/COLOR][COLOR=Sienna][B]NOTE!!!
I've fixed the problem (vertle program problem ) un-instaling all vlc  stuffs and rebooting my computer 

I hope this help someone with my same problem :)
[/B][/COLOR]
[COLOR=Sienna][/COLOR]

---

### Post by haylocki on 2010-05-11
H, wasabishot,

Probably to late to help you now, but this might help someone else.

I also had the same problem as you.

I managed to fix it by :

1) reboot in recovery mode
2) select the option to "drop to root shell prompt with networking"
3) log in as my user. (Does not require the .ICEauthority file)
4) sudo apt-get install ubuntu-desktop

For me step 4 caused four or five packages to be installed, and this fixed the login, logout problem.

Cheers, Ian

---

### Post by codamoda on 2010-06-04
Blinchi,

Thanks, I've been trying to fix this problem for a day now, and it turns out it was because of my installation of Veetle (which didn't work anyway, since I use 64 bit Ubuntu).  I thought this was due to my installation of Flock web browser, but in the end it wasn't the case.

**I simply uninstalled my VLC player**, and now I don't have the ICEauthority message at startup, and my sound works (I was having the "Waiting for sound system to respond" message) and my desktop isn't screwy anymore (shutdown icon, time disappearing on menu bar).

---

### Post by joanluc+ on 2010-06-15
Hi all
I got a similar message on a ubuntu 10.04 box but the file's path differ : "Could not update ICEauthority file /var/lib/gdm/.ICEauthority" 
that file's owner is root, but the message is coming before the opening of a session when the system is launching Xorg so i think it should not be a problem?

Then i got an other message (in french as the system is in french - nobody's perfect - "Il y a un problème avec le serveur de configuration (/usr/lib/libgconf2-4/gconf-sanity-check-2 a quitté avec l'état 256)") that means there's a problem with configuration server /usr/lib/libgconf2-4/gconf-sanity-check-2 that stopped with error status 256, then i noticed the network is not working, it was first configured with DHCP , i tried to change it by manually assign an address - the good one as our network has fixed addresses - but that assignement does'nt work.

Are these 3 problemes linked together ?

---

### Post by joanluc+ on 2010-06-15
The owner of /var/lib/gdm was root, i changed it to gdm so i haven't the messages anymore but i still have no network.

---

### Post by philinux on 2010-06-15
> **joanluc+ said:**
> The owner of /var/lib/gdm was root, i changed it to gdm so i haven't the messages anymore but i still have no network.

You need to create your own specific Thread.

Closed.

---

