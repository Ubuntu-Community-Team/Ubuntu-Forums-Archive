---
title: "How do I uninstall a program"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by Stigg on 2009-08-13
Hi, I'm hoping that somebody can help me uninstall BBC iPlayer desktop.  Idownloaded it no problem from the BBC website just by clicking 'download' and following the instructions.  However, I can't remove it.  I cannot find it add/remove or Synaptic Package Manager.  I have looked at threads on the forum but can't find/understand anything to help me.  I have just installed Ubuntu 9.04.  Thanks

---

### Post by mkrahmeh on 2009-08-13
you can find the synaptic under system -> administration -> synaptic package manager

or you can use the terminal by typing 
```
sudo dpkg -P *program_name*
```
which will ask you for your password

---

### Post by ubudog on 2009-08-13
You can't find it on Synaptic because it's probably not in the repository.  Just try doing ```
sudo apt-get remove iPlayer
``` Maybe that will work.  I'm not sure.  Hope that helps! :P

---

### Post by Stigg on 2009-08-13
I tried

rick@rick-laptop:~$ sudo apt-get remove iPlayer
[sudo] password for rick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package iPlayer
rick@rick-laptop:~$

---

### Post by credobyte on 2009-08-13
> **Stigg said:**
> I tried

rick@rick-laptop:~$ sudo apt-get remove iPlayer
[sudo] password for rick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package iPlayer
rick@rick-laptop:~$

Do what [mkrahmeh]("http://ubuntuforums.org/member.php?u=555934") said - you can't use aptitude to uninstall custom .deb packages ;)

---

### Post by ubudog on 2009-08-13
> **Stigg said:**
> I tried

rick@rick-laptop:~$ sudo apt-get remove iPlayer
[sudo] password for rick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package iPlayer
rick@rick-laptop:~$

Ok.  Open a terminal and do ```
locate iPlayer
```  Do you see anything about iPlayer? :P

---

### Post by Stigg on 2009-08-13
The program appears in accessories and on Desktop, where Icould select and delete it.  Would this work?

---

### Post by Stigg on 2009-08-13
rick@rick-laptop:~$ locate iplayer
/etc/opt/Adobe AIR/AIR Applications/1.0/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1
/home/rick/Desktop/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.desktop
/opt/BBC iPlayer Desktop/share/bbc_iplayer_desktop.swf
/opt/BBC iPlayer Desktop/share/META-INF/AIR/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.desktop
/opt/BBC iPlayer Desktop/share/META-INF/AIR/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.directory
/opt/BBC iPlayer Desktop/share/META-INF/AIR/image128x128/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.png
/opt/BBC iPlayer Desktop/share/META-INF/AIR/image16x16/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.png
/opt/BBC iPlayer Desktop/share/META-INF/AIR/image32x32/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.png
/opt/BBC iPlayer Desktop/share/META-INF/AIR/image48x48/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.png
/usr/share/app-install/desktop/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.desktop
/usr/share/applications/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.desktop
/usr/share/applnk/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.desktop
/usr/share/icons/gnome/128x128/apps/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.png
/usr/share/icons/gnome/16x16/apps/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.png
/usr/share/icons/gnome/32x32/apps/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.png
/usr/share/icons/gnome/48x48/apps/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.png
/usr/share/icons/hicolor/128x128/apps/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.png
/usr/share/icons/hicolor/16x16/apps/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.png
/usr/share/icons/hicolor/32x32/apps/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.png
/usr/share/icons/hicolor/48x48/apps/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.png
/var/lib/dpkg/info/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.copyright
/var/lib/dpkg/info/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.list
/var/lib/dpkg/info/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.postinst
/var/lib/dpkg/info/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.prerm
rick@rick-laptop:~$

---

### Post by 3rdalbum on 2009-08-13
Do you know for sure that the package is called "iPlayer"? It sorta looks like the package might be called "bbciplayerdesktop"

According to the BBC, it's an Adobe Air program and is installed via Debian package. If you go to Synaptic and click the Origin button, you should find it under one of the "Local" entries.

Or try this command:

```
apt-cache search iplayer
```

That finds all packages that mention the phrase "iplayer".

---

### Post by ubudog on 2009-08-13
> **Stigg said:**
> The program appears in accessories and on Desktop, where Icould select and delete it.  Would this work?

Are those the only two locations?

EDIT: I just saw your above post.  nm about this.

---

### Post by ronaldprettyman on 2009-08-13
> **Stigg said:**
> rick@rick-laptop:~$ locate iplayer
/etc/opt/Adobe AIR/AIR Applications/1.0/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1
/home/rick/Desktop/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.desktop
/opt/BBC iPlayer Desktop/share/bbc_iplayer_desktop.swf
/opt/BBC iPlayer Desktop/share/META-INF/AIR/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.desktop
/opt/BBC iPlayer Desktop/share/META-INF/AIR/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.directory
/opt/BBC iPlayer Desktop/share/META-INF/AIR/image128x128/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.png
/opt/BBC iPlayer Desktop/share/META-INF/AIR/image16x16/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.png
/opt/BBC iPlayer Desktop/share/META-INF/AIR/image32x32/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.png
/opt/BBC iPlayer Desktop/share/META-INF/AIR/image48x48/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.png
/usr/share/app-install/desktop/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.desktop
/usr/share/applications/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.desktop
/usr/share/applnk/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.desktop
/usr/share/icons/gnome/128x128/apps/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.png
/usr/share/icons/gnome/16x16/apps/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.png
/usr/share/icons/gnome/32x32/apps/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.png
/usr/share/icons/gnome/48x48/apps/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.png
/usr/share/icons/hicolor/128x128/apps/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.png
/usr/share/icons/hicolor/16x16/apps/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.png
/usr/share/icons/hicolor/32x32/apps/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.png
/usr/share/icons/hicolor/48x48/apps/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.png
/var/lib/dpkg/info/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.copyright
/var/lib/dpkg/info/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.list
/var/lib/dpkg/info/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.postinst
/var/lib/dpkg/info/bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1.prerm
rick@rick-laptop:~$

apt-cache search iplayer

or you could do it the dirty way
rm -rf `locate iplayer`

---

### Post by ubudog on 2009-08-13
Go to System>Preferences>Main Menu then go on Accessories and click iPlayer.  Then click on Properties and post the command the launcher uses.  :P

---

### Post by wojox on 2009-08-13
```
dpkg -l | grep "adobe"
```

```
sudo dpkg -r <AIR and adobe-certs package names found from previous command>
```

---

### Post by Stigg on 2009-08-13
I did:- Go to System>Preferences>Main Menu then go on Accessories and click iPlayer. Then click on Properties and post the command the launcher uses

Is this what I should be looking for?
'/opt'/'BBC iPlayer Desktop'/bin/'BBC iPlayer Desktop'

---

### Post by MattM11 on 2009-08-13
When I installed the iPlayer I also ended up with an "Adobe Air Uninstaller" option in my Accessories menu - this gives me the option to remove it. Failing that... I'd just use the Terminal to navigate to my /opt folder (where the bulk of the programme seems to be stored) and delete the BBC iPlayer folder.

---

### Post by Stigg on 2009-08-13
Thanks, I didn't realise that the Adobe uninstaller could remove the BBC iPlayer.  The BBC icons are still there but nothing happens when I click on them

---

### Post by Stigg on 2009-08-13
Unfortunately the thing still seems to be there if I cliick on the icon on the toolbar at the top!

---

### Post by MattM11 on 2009-08-13
I think your only option is to remove it manually. 

Just use the Terminal to navigate to the /opt folder and delete the iPlayer folder.

cd /opt

then:

sudo rm -r BBC iPlayer Desktop

(Assuming that's where it's located on your system).

Then, if you need to, you can use the "Edit Menus" option to delete the icons in the accessories menu.

---

### Post by ubudog on 2009-08-13
> **MattM11 said:**
> I think your only option is to remove it manually. 

Just use the Terminal to navigate to the /opt folder and delete the iPlayer folder.

cd /opt

then:

sudo rm -r BBC iPlayer Desktop

(Assuming that's where it's located on your system).

Then, if you need to, you can use the "Edit Menus" option to delete the icons in the accessories menu.

Yes.  That would be the best option.  :P

---

### Post by Stigg on 2009-08-13
Have tried the above with no luck, maybe I'm doing something wrong.

rick@rick-laptop:/opt$ sudo rm -r BBC iPlayer Desktop
rm: cannot remove `BBC': No such file or directory
rm: cannot remove `iPlayer': No such file or directory
rm: cannot remove `Desktop': No such file or directory
rick@rick-laptop:/opt$

---

### Post by ubudog on 2009-08-13
Do ```
cd /opt
``` then do ```
ls
```  Post the results. :P

---

### Post by Stigg on 2009-08-13
If I type ls this comes up

rick@rick-laptop:/opt$ ls
BBC iPlayer Desktop

What should I do next?

---

### Post by MattM11 on 2009-08-13
My fault - try:

sudo rm -r "BBC iPlayer Desktop"

instead. (Without the quotation marks the terminal treats it as three different folders: BBC, iPlayer and Desktop!).

---

### Post by ubudog on 2009-08-13
> **MattM11 said:**
> My fault - try:

sudo rm -r "BBC iPlayer Desktop"

instead. (Without the quotation marks the terminal treats it as three different folders: BBC, iPlayer and Desktop!).

Yes.  Hope that works.  Good luck! :P

---

### Post by Stigg on 2009-08-13
Still no go, Sorry to be a pain

rick@rick-laptop:/opt$ sudo rm -r "BBC iPlayer Desktop"
rm: cannot remove `BBC iPlayer Desktop': No such file or directory

---

### Post by MattM11 on 2009-08-13
Odd.

I just tried it on mine (wasn't using the iPlayer much anyway) and it worked no problem. I hate to sound patronising, but are you sure you typed it right? :confused: Otherwise I'm at a bit of a loss.

---

### Post by ubudog on 2009-08-13
> **Stigg said:**
> Still no go, Sorry to be a pain

rick@rick-laptop:/opt$ sudo rm -r "BBC iPlayer Desktop"
rm: cannot remove `BBC iPlayer Desktop': No such file or directory

You have to do rm -r BBC\ and hit tab then hit enter and it should work.

---

### Post by t0p on 2009-08-13
Try this:

```
sudo rm -rf /opt/BBC\ iPlayer\ Desktop/
```

---

### Post by Stigg on 2009-08-13
Don't worry about being patronising I'm a bit of a numpty when it comes to computers, this is only the second time that I have entered terminal. I could just think that it doesn't matter that I still have iplayer on the computer, but I have a bee in my bonnet and can't give up, plus I am learning more this way and that's no bad thing.
  I did however copy and paste the script you posted so that I had less chance of making a mistake.
  Thanks for your time and patience.

---

### Post by t0p on 2009-08-13
> **Stigg said:**
> Don't worry about being patronising I'm a bit of a numpty when it comes to computers, this is only the second time that I have entered terminal. I could just think that it doesn't matter that I still have iplayer on the computer, but I have a bee in my bonnet and can't give up, plus I am learning more this way and that's no bad thing.
  I did however copy and paste the script you posted so that I had less chance of making a mistake.
  Thanks for your time and patience.

Have you tried pasting into the terminal the command that *I* suggested just now?  That should remove the BBC iPlayer Desktop folder from your system.  I can't think of any reason why it wouldn't work.  So please try it and post some feedback.

---

### Post by Stigg on 2009-08-13
Sorry, I'm not ignoring you t0p, just trying to feed the kids and put them to bed.

I did try it and.....

rick@rick-laptop:/opt$ sudo rm -rf /opt/BBC\ iPlayer\ Desktop/
rick@rick-laptop:/opt$ 

nothing happened?????

---

### Post by ubudog on 2009-08-13
> **Stigg said:**
> Sorry, I'm not ignoring you t0p, just trying to feed the kids and put them to bed.

I did try it and.....

rick@rick-laptop:/opt$ sudo rm -rf /opt/BBC\ iPlayer\ Desktop/
rick@rick-laptop:/opt$ 

nothing happened?????

Something happened....It worked!  Do ls and post again.

---

### Post by wojox on 2009-08-13
If it looks like that it worked ls and see.

---

### Post by ubudog on 2009-08-13
You will probably still have the launcher in Accessories so to delete it, go to System>Preferences>Main Menu and click on Accessories and click on iPlayer and click Delete.  Hope that helps! :P

---

### Post by Stigg on 2009-08-13
Hi ubudog, tried ls and...

rick@rick-laptop:/opt$ ls
rick@rick-laptop:/opt$ 

  there is still, however, an icon at the top and if I click it it opens iPlayer.

---

### Post by Stigg on 2009-08-13
I just right clicked the icon at the top, exited, and it has gone.  The icon on desktop doesn't do anything nor does the icon on accessories.  I think you've done it, thank you .  I'll try rebooting and see if I can find iPlayer.  You guys have been great, thanks for the help.

---

### Post by ubudog on 2009-08-13
> **Stigg said:**
> Hi ubudog, tried ls and...

rick@rick-laptop:/opt$ ls
rick@rick-laptop:/opt$ 

  there is still, however, an icon at the top and if I click it it opens iPlayer.

Well you got rid of the file.  Try going on Applications>Accessories>iPlayer.  It shouldn't start from there now.  I don't know why it still opens.  Right click the icon and select properties.  Paste the command in a new post. We'll get it eventually.  :)

EDIT: Nevermind about everything I just said.  I didn't see your above post.

---

### Post by MattM11 on 2009-08-13
Blimey, 4 pages trying to delete a folder! :)

When computers decide to make life complicated they really go for it.

---

### Post by ubudog on 2009-08-13
> **Stigg said:**
> I just right clicked the icon at the top, exited, and it has gone.  The icon on desktop doesn't do anything nor does the icon on accessories.  I think you've done it, thank you .  I'll try rebooting and see if I can find iPlayer.  You guys have been great, thanks for the help.

Any time.  If you need me just PM me.

---

### Post by ubudog on 2009-08-13
> **MattM11 said:**
> Blimey, 4 pages trying to delete a folder! :)

When computers decide to make life complicated they really go for it.

ha ha :lolflag:

---

### Post by Stigg on 2009-08-13
I don't know too much about all this but if the window was already open and minimised, clicking the icon at the top may have just maximised the window again, even though the program had been uninstalled.  It has gone now and none of the desktop/accessories icons open anything.  If I just delete the remaining icons I think we've erased all trace of it.

---

### Post by ubudog on 2009-08-13
You may like this [http://www.linuxcommand.org/](http://www.linuxcommand.org/) It may help you learn a little more about the terminal. :P

---

### Post by ubudog on 2009-08-13
> **Stigg said:**
> I don't know too much about all this but if the window was already open and minimised, clicking the icon at the top may have just maximised the window again, even though the program had been uninstalled.  It has gone now and none of the desktop/accessories icons open anything.  If I just delete the remaining icons I think we've erased all trace of it.

Yep.  Finally.  All that just remove a program.  :P

---

### Post by Stigg on 2009-08-13
I've already made a fool of myself so what the hell, ubudog what do you mean by PM?

---

### Post by ubudog on 2009-08-13
> **Stigg said:**
> I've already made a fool of myself so what the hell, ubudog what do you mean by PM?

Private Message

---

### Post by ubudog on 2009-08-13
Just click on my name beside a post I have made and then click something involving a Private Message

---

### Post by MattM11 on 2009-08-13
> I've already made a fool of myself...

Shortly after installing Ubuntu for the first time I tried to uninstall KDE-desktop (which I'd installed to test out). It proved slightly more tricky than expected and - because I didn't bother asking for help - I managed to foul up my GNOME-desktop so badly that I had to give in and do a clean reinstall of Ubuntu.

*That* was foolish. :)

The terminal commands take a bit of getting used to. I'm still learning them. Ubudog's guide looks great.

---

### Post by am7555 on 2009-08-13
Have you tried using under applications the add/remove?

---

### Post by ubudog on 2009-08-13
> **am7555 said:**
> Have you tried using under applications the add/remove?

Read all the other posts.  We already have it solved, but thanks anyway! :P

---

### Post by shantiq on 2010-03-24
> **3rdalbum said:**
> Do you know for sure that the package is called "iPlayer"? It sorta looks like the package might be called "bbciplayerdesktop"

According to the BBC, it's an Adobe Air program and is installed via Debian package. If you go to Synaptic and click the Origin button, you should find it under one of the "Local" entries.

Or try this command:

```
apt-cache search iplayer
```That finds all packages that mention the phrase "iplayer".


[FONT=Century Gothic][SIZE=2][COLOR=Blue][B]ok third album you have the answer

1. [/B][/COLOR][/SIZE][/FONT]```
apt-cache search iplayer
```[FONT=Century Gothic][SIZE=2][COLOR=Blue][B]
2.  if you scroll down you will find the name of YOUR iplayer each one has an ID number 
 [/B][/COLOR][/SIZE][/FONT]```
bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1
```[FONT=Century Gothic][SIZE=2][COLOR=Blue][B]


3. then run the usual  

[/B][/COLOR][/SIZE][/FONT]```
sudo apt-get remove bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1
```[FONT=Century Gothic][SIZE=2][COLOR=Blue][B]not exactly simple and helping the user but that is the way to do it
took me a while to work it out
[/B][/COLOR][/SIZE][/FONT]

---

### Post by 1991sudarshan on 2010-03-24
you can uninstall it by using the synaptic package manager or by typing the below command in the terminal

**$sudo apt-get remove <package>**

---

### Post by 3rdalbum on 2010-03-24
> **shantiq said:**
> [FONT=Century Gothic][SIZE=2][COLOR=Blue][B]ok third album you have the answer

1. [/B][/COLOR][/SIZE][/FONT]```
apt-cache search iplayer
```[FONT=Century Gothic][SIZE=2][COLOR=Blue][B]
2.  if you scroll down you will find the name of YOUR iplayer each one has an ID number 
 [/B][/COLOR][/SIZE][/FONT]```
bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1
```[FONT=Century Gothic][SIZE=2][COLOR=Blue][B]


3. then run the usual  

[/B][/COLOR][/SIZE][/FONT]```
sudo apt-get remove bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1
```[FONT=Century Gothic][SIZE=2][COLOR=Blue][B]not exactly simple and helping the user but that is the way to do it
took me a while to work it out
[/B][/COLOR][/SIZE][/FONT]

If I was a moderator, I'd say:

Necromancing. Locked.

But I'm not a moderator, so I'll just say that it was frustrating reading all those other replies when I'd already answered the question. Obviously I was the only one who actually bothered to take a look at the removal instructions on the BBC website.

---

