---
title: "No sound in You Tube"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by susanpenter on 2009-06-26
I am having problems with internet sounds.  Amarok and the system sounds are all fine it is just internet based ones.  

As suggested in a previous post I have made sure that I exited from Amarok before trying to play internet sounds.


Thanks for any help.

Susan

---

### Post by billgoldberg on 2009-06-26
Hmmm.

Do you have flash player installed or gnash or swfdec?


Did you try using ALSA or OSS instead of PULSEAUDIO?

Exiting Amarok should not be necessary.

In older versions sometimes libflashsupport was needed. I don't think this is still the case, but you can install it and see if it helps.

---

### Post by credobyte on 2009-06-26
No sound at all or no sound if something else ( eg. Amarok ) is running ?

---

### Post by s.fox on 2009-06-26
Hi,

You could try the [multimedia how to]("http://ubuntuforums.org/showthread.php?t=766683").  Its pretty comprehensive 

-Ash R

---

### Post by susanpenter on 2009-06-26
Well I though I may have solved it by installing flash non free extra sound but there is no change. I checked out multimedia how to but it seems so complex that i may risk wrecking my whole system uninstalling and re-installing things.  At the moment all the computer sounds work except flash based internet ones, I don't want to risk loosing all the sounds by randomly trying to follow this list.

My sound was working recently but I have upgraded to Swiftfox FF RC2 so this may have had an effect on the situation?

Thanks for any user friendly suggestions.

Susan

---

### Post by susanpenter on 2009-06-26
Well I though I may have solved it by installing flash non free extra sound but there is no change. I checked out multimedia how to but it seems so complex that I may risk wrecking my whole system uninstalling and re-installing things.  At the moment all the computer sounds work except flash based internet ones, I don't want to risk loosing all the sounds by randomly trying to follow this list.

My sound was working recently but I have upgraded to Swiftfox FF RC2 so this may have had an effect on the situation?

Thanks for any user friendly suggestions.

Susan

---

### Post by wpshooter on 2009-06-26
Do you have the **_FULL_** version of Adobe FlashPlayer for Linux available at the Adobe Acrobat site installed ?

---

### Post by kansasnoob on 2009-06-26
> **susanpenter said:**
> Well I though I may have solved it by installing flash non free extra sound but there is no change. I checked out multimedia how to but it seems so complex that I may risk wrecking my whole system uninstalling and re-installing things.  At the moment all the computer sounds work except flash based internet ones, I don't want to risk loosing all the sounds by randomly trying to follow this list.

My sound was working recently but I have upgraded to Swiftfox FF RC2 so this may have had an effect on the situation?

Thanks for any user friendly suggestions.

Susan

You didn't mention which version of Ubuntu you're using. Is it Ubuntu? or Xubuntu or Kubuntu? Is it 8.04, 8.10, or 9.04?

Also, why did you change to Swiftfox?

---

### Post by susanpenter on 2009-06-26
My version is mentioned in the sidebar it is Ubuntu 9.04 and I changed to Swiftfox because I wanted to use features of Firefox 3.5 that are unavailable in version 3.0.11 that comes with Ubuntu


I will check that I have the FULL version of Adobe Flash player and report back.  As I can watch the picture with no proble I expect that I do though.

---

### Post by susanpenter on 2009-06-26
I went to the download page for Adobe Flash but my package installer told me that I have a later version of flash already installed.

---

### Post by shizumasa14 on 2009-06-26
do the latest updates then...

```

sudo apt-get install ubuntu-restricted-extras

```

---

### Post by GregA on 2009-06-26
If you don't start/run amarok - does streaming sound work?  Also, if you exit amarok, and re-start your system, will streaming work then?  

I'm still running Hardy Heron (8.04), and I've noticed the sound engine can get hijacked by Rhythmbox or Banshee - until a restart is done, or if I never opened those in the current session.

By the way, in gnome, I can run the "Audacious" music player and it won't hijack the sound and streaming still works later.  Maybe Audacious and XMMS (in Kubuntu) use different sound drivers.

---

### Post by susanpenter on 2009-06-26
> **shizumasa14 said:**
> do the latest updates then...

```

sudo apt-get install ubuntu-restricted-extras

```

I already have the latest version installed

---

### Post by susanpenter on 2009-06-26
> **GregA said:**
> If you don't start/run amarok - does streaming sound work?  Also, if you exit amarok, and re-start your system, will streaming work then?  



Even without opening Amarok streaming sound is not working..... it was a few days ago!

Audacious doesn't look to support i pods like Amarok does or have many of the other good features come to that!

---

### Post by kansasnoob on 2009-06-26
> **susanpenter said:**
> My version is mentioned in the sidebar it is Ubuntu 9.04 and I changed to Swiftfox because I wanted to use features of Firefox 3.5 that are unavailable in version 3.0.11 that comes with Ubuntu


I will check that I have the FULL version of Adobe Flash player and report back.  As I can watch the picture with no proble I expect that I do though.

In 9.04 you can install Firefox 3.5. It's in the repos!

---

### Post by lovinglinux on 2009-06-26
> **kansasnoob said:**
> In 9.04 you can install Firefox 3.5. It's in the repos!

Only version b4pre. Swiftfox is rc2.

---

### Post by kansasnoob on 2009-06-26
Well, where I was going with this was that I've cured my 9.04 sound problems by installing this repo:

[https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa)

Don't forget the gpg key!

And making sure that if I type "flash" into the Synaptic search window I only have "adobe-flashplugin" and "ubuntu-restricted-extras31" installed.

Then reconfigure pulseaudio by following the Jaunty steps here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

It's worked for me every time!

But I've not tried it with Swiftfox!

---

### Post by susanpenter on 2009-06-26
> **kansasnoob said:**
> Well, where I was going with this was that I've cured my 9.04 sound problems by installing this repo:

[https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa)

Don't forget the gpg key!

And making sure that if I type "flash" into the Synaptic search window I only have "adobe-flashplugin" and "ubuntu-restricted-extras31" installed.

Then reconfigure pulseaudio by following the Jaunty steps here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

It's worked for me every time!

But I've not tried it with Swiftfox!

Hi this sounds like it will be useful but I'm not sure what you mean by: Don't forget the GPG key? How do I find out what the key is and where should I use it.

Sorry but I am not really much of a coder...

---

### Post by nwadams on 2009-06-26
umm. if you go into synaptics and search for youtube i believe there is a package that allows websites like youtube to play their sound correctly. I'm not on my ubuntu box so i can't confirm the exact name of the package.

---

### Post by Therion on 2009-06-26
If you're SURE you've installed the Adobe plugins open Synaptic and search on **swfdec**.  You should get two hits on this search.

Mark both packages for removal if they're installed.

While in Synaptic search on **gnash**.  Anything "gnash" related should also be marked for removal.

This should solve the problem.

---

### Post by susanpenter on 2009-06-27
> **Therion said:**
> If you're SURE you've installed the Adobe plugins open Synaptic and search on **swfdec**.  You should get two hits on this search.

Mark both packages for removal if they're installed.

While in Synaptic search on **gnash**.  Anything "gnash" related should also be marked for removal.

This should solve the problem.

Thanks for this but none of the swf or gnash files were installed to begin with so they didn't need removing.

This is starting to get very puzzling and mildly annoying!

---

### Post by susanpenter on 2009-06-27
To complicate matters further I have opened Epiphany web browser out of interest and You Tube had sound there so it is therefore isolated to a problem within Firefox.

---

### Post by krow436 on 2009-06-27
I've had this problem before.  Almost every time it is fixed for me by installing libflashplayer.  That may have a dash in there somewhere, I don't remember for sure, but just try installing that package.

---

### Post by susanpenter on 2009-06-27
> **krow436 said:**
> I've had this problem before.  Almost every time it is fixed for me by installing libflashplayer.  That may have a dash in there somewhere, I don't remember for sure, but just try installing that package.

This is already installed

---

### Post by peacechicken on 2009-07-02
> **susanpenter said:**
> This is already installed

I'm having the exact same problem, none of these solutions is helping :(

---

### Post by susanpenter on 2009-07-04
This is interesting, when I go to the Adobe page to download the lastest Flash player, the package manager tells me I have a more recent version than that and yet that version is 10.? and when I go to about:plugins it says:
    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

So I am curious as to how I can upgrade it if the package manager won't let me?

Cheers,

Susan

---

### Post by unutbu on 2009-07-04
susanpenter, it seems there are a couple of different versions of flash floating around. I notice that a number of threads discussing how to solve sound issues begins with removing
packages. I suspect the reason for this is because having more than one installed can cause problems.

All solutions seem to follow the same theme: delete everything related to problem X and then reinstall package Y.

See for example:
[http://ubuntuforums.org/showpost.php?p=5913037&postcount=5](http://ubuntuforums.org/showpost.php?p=5913037&postcount=5)
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by susanpenter on 2009-07-04
I have tried this method of uninstalling everything related to flash and re-installing it from the 10.x current page and yet the about plugin list still says I have 
File name: libflashplayer.so
Shockwave Flash 9.0 r124

next idea please....
thanks,

Susan

---

### Post by unutbu on 2009-07-04
What is the output of 
```

locate libflashplayer
ls -l $(locate libflashplayer.so)

```

---

### Post by susanpenter on 2009-07-04
> **unutbu said:**
> What is the output of 
```

locate libflashplayer
ls -l $(locate libflashplayer.so)

```

/home/susan/.mozilla/plugins/libflashplayer.so
/home/susan/.mozilla.backup/plugins/libflashplayer.so
/opt/Adobe AIR/Versions/1.0/Resources/libflashplayer.so
/usr/lib/adobe-flashplugin/libflashplayer.so

---

### Post by unutbu on 2009-07-04
How about run
```

ls -lR "/opt/Adobe AIR/" > adobe.txt
ls -lR /usr/lib/adobe-flashplugin/ > usrlib.txt
ls -lR /etc/alternatives > alternatives.txt
```

This will list all the files in /opt/Adobe AIR/, /usr/lib/adobe-flashplugin, and /etc/alternatives and dump the output in files called adobe.txt, usrlib.txt and alternatives.txt. Post each of these files as attachments.

Since I don't know how these files were installed, I'm looking for the safest/cleanest way to uninstall these files. The output might help us do that. 

Also, post the output of 
```

ls -l $(locate libflashplayer.so)
```

---

### Post by susanpenter on 2009-07-04
Here is the output of the second one I will work through the others afterwards.

susan@susan-desktop:~$ ls -l $(locate libflashplayer.so)
ls: cannot access /opt/Adobe: No such file or directory
ls: cannot access AIR/Versions/1.0/Resources/libflashplayer.so: No such file or directory
-rwxr-xr-x 1 susan susan  8115888 2009-06-25 16:28 /home/susan/.mozilla.backup/plugins/libflashplayer.so
-rwxrwxr-x 1 susan susan  8115888 2008-03-24 18:02 /home/susan/.mozilla/plugins/libflashplayer.so
-rw-r--r-- 1 root  root  10089232 2009-02-07 00:15 /usr/lib/adobe-flashplugin/libflashplayer.so

---

### Post by susanpenter on 2009-07-04
I added the three rows of code one at a time within the terminal but it just mooved to the next line, no text files were opened, see
```

susan@susan-desktop:~$ ls -lR "/opt/Adobe AIR/" > adobe.txt
susan@susan-desktop:~$ ls -lR /usr/lib/adobe-flashplugin/ > usrlib.txt
susan@susan-desktop:~$ ls -lR /etc/alternatives > alternatives.txt
susan@susan-desktop:~$

```

---

### Post by unutbu on 2009-07-04
Right. They do not print anything to the terminal; instead files are created. Using a filebrowser, you should now have 3 new files splattered unceremoniously in your home account:  adobe.txt, usrlib.txt, alternatives.txt.

Next time you click the reply button in this thread, scroll down to about midway and  you'll see a button called "Manage Attachments". Click that and post the three files here as attachments.

---

### Post by susanpenter on 2009-07-04
Here are two of them , the alternatives is apparently too big for the forum to allow.

Susan

---

### Post by unutbu on 2009-07-04
Okay, then run 
```

ls -lR /etc/alternatives | bzip2 > alternatives.txt.bz2
```
and then post alternatives.txt.bz2 instead.

---

### Post by susanpenter on 2009-07-04
Here is the file,

I'm glad you're so knowledgeable!

---

### Post by unutbu on 2009-07-04
Let's try this:
```

mkdir ~/junk
mv /home/susan/.mozilla/plugins/libflashplayer.so ~/junk
```

This will move the libflashplayer.so file out of your .mozilla directory and place it in a directory called "junk". Start up Firefox and see if sound works. If it does, then you can delete the entire junk directory.

If it doesn't work, we'll move on uninstalling /usr/lib/adobe-flashplugin/libflashplayer.so and then reinstalling Flash 10.

---

### Post by susanpenter on 2009-07-04
> **unutbu said:**
> Let's try this:
```

mkdir ~/junk
mv /home/susan/.mozilla/plugins/libflashplayer.so ~/junk
```

This will move the libflashplayer.so file out of your .mozilla directory and place it in a directory called "junk". Start up Firefox and see if sound works. If it does, then you can delete the entire junk directory.

If it doesn't work, we'll move on uninstalling /usr/lib/adobe-flashplugin/libflashplayer.so and then reinstalling Flash 10.
I've followed the first step and restarted Firefox but no joy.

It may be worth mentioning that I have a few Firefox's installed.  There is the original one through the package manager.version 3.1 then there is swiftfox 3.5 RC2 through the package manager and also final release 3.5 installed straight into my home directory  - in case this makes a difference.

---

### Post by unutbu on 2009-07-04
I don't think it matters which firefox you use -- I think they all read ~/.mozilla.

Back in post #26 you mentioned Firefox reporting that when you type
```
about:plugins
```

 into the Firefox location field, you see
```

Shockwave Flash 9.0 r124

```
Is this still the same?

Also, please post the output of 
```

apt-cache policy flashplugin-nonfree
uname -a

```

---

### Post by susanpenter on 2009-07-04
yes the about : plugins is still showing the same and the information output is:
```

flashplugin-nonfree:
  Installed: (none)
  Candidate: 10.0.22.87ubuntu2
  Version table:
     10.0.22.87ubuntu2 0
        500 http://ftp.ticklers.org jaunty/multiverse Packages

```

---

### Post by unutbu on 2009-07-04
Before we try removing /usr/lib/adobe-flashplugin/libflashplayer.so, let's try one more simple thing:

Close Firefox. Then run in a terminal:
```

mv ~/.mozilla ~/.mozilla_old
```

This will move your entire .mozilla folder to .mozilla_old. 
Now restart Firefox. Firefox will notice that there is no ~/.mozilla folder, and should generate a new one with "factory default" settings.

Then type 
```

about:plugins
```

in the URL location field again and see if it lists anything about Shockwave Flash.
If it does, what version does it show?

Of course, try a youtube video and see if you have sound.

If that does not work, please post the output of these commands:
```

ps axuw | grep firefox
dpkg --get-selections | grep flash
dpkg -S /usr/lib/adobe-flashplugin/libflashplayer.so

```

---

### Post by lovinglinux on 2009-07-04
> **unutbu said:**
> Before we try removing /usr/lib/adobe-flashplugin/libflashplayer.so, let's try one more simple thing:

Close Firefox. Then run in a terminal:
```

mv ~/.mozilla ~/.mozilla_old
```

This will move your entire .mozilla folder to .mozilla_old. 
Now restart Firefox. Firefox will notice that there is no ~/.mozilla folder, and should generate a new one with "factory default" settings.

Please see note below:

> **[color=#CC0000]Note:[/color]** I don't know why everyone recommends moving, renaming or deleting ~/.mozilla folder to solve Firefox issues. The ~/.mozilla folder is also the place where other Mozilla applications might store their profiles (Sunbird, etc), so deleting this folder will delete their settings too. 

Firefox profiles are stored under ~/.mozilla/firefox folder. So if you need to remove a Firefox profile to fix a problem, then delete, rename or move ~/.mozilla/firefox not ~/.mozilla.

---

### Post by unutbu on 2009-07-04
Thanks for the info, lovinglinux, but it appears to be wrong -- at least under Intrepid.
I just downloaded thunderbird and it appears it saves its configuration files in ~/.mozilla-thunderbird, not in ~/.mozilla.

I haven't downloaded Sunbird. Do you know from experience that it saves configuration files in ~/.mozilla?

---

### Post by lovinglinux on 2009-07-04
> **unutbu said:**
> Thanks for the info, lovinglinux, but it appears to be wrong -- at least under Intrepid.
I just downloaded thunderbird and it appears it saves its configuration files in ~/.mozilla-thunderbird, not in ~/.mozilla.

I haven't downloaded Sunbird. Do you know from experience that it saves configuration files in ~/.mozilla?

It appears that Thunderbird is an exception. You are not the first one to point that out. I should remove it from my tutorial :)

Nevertheless, Sunbird stores it's settings there. I have it installed. Additionally, I also have an "eclipse" settings folder under mozilla, which I don't know where it came from :)

Anyway, there is no good reason to move ~/.mozilla, when you can achieve the same results by moving just ~/.mozilla/firefox. Firefox 3.5 stores the profiles under ~/.mozilla/firefox-3.5.

---

### Post by susanpenter on 2009-07-04
> **unutbu said:**
> Before we try removing /usr/lib/adobe-flashplugin/libflashplayer.so, let's try one more simple thing:

Close Firefox. Then run in a terminal:
```

mv ~/.mozilla ~/.mozilla_old
```

This will move your entire .mozilla folder to .mozilla_old. 
Now restart Firefox. Firefox will notice that there is no ~/.mozilla folder, and should generate a new one with "factory default" settings.

Then type 
```

about:plugins
```

in the URL location field again and see if it lists anything about Shockwave Flash.
If it does, what version does it show?

Of course, try a youtube video and see if you have sound.

If that does not work, please post the output of these commands:
```

ps axuw | grep firefox
dpkg --get-selections | grep flash
dpkg -S /usr/lib/adobe-flashplugin/libflashplayer.so

```

I have checked about : plugins and it is still showing the 9.x as before and there is still no sound...

Here is the first 
```

susan@susan-desktop:~$ ps axuw | grep firefox
susan    15369  0.0  0.0   1872   540 ?        S    23:44   0:00 /bin/sh /home/susan/firefox 3.5/firefox
susan    15372  0.0  0.0   1872   548 ?        S    23:44   0:00 /bin/sh /home/susan/firefox 3.5/run-mozilla.sh /home/susan/firefox 3.5/firefox-bin
susan    15376  9.0  7.9 292856 81452 ?        Sl   23:44   0:27 /home/susan/firefox 3.5/firefox-bin
susan    15742  0.0  0.0   3340   808 pts/0    S+   23:49   0:00 grep firefox

```
the second
```

adobe-flashplugin				install
flashplugin-installer				deinstall

```
and the third
```

adobe-flashplugin: /usr/lib/adobe-flashplugin/libflashplayer.so

```
I assume I will be able to get back all my extensions etc without having to re-install them all!

---

### Post by lovinglinux on 2009-07-04
> **susanpenter said:**
> I have checked about : plugins and it is still showing the 9.x as before and there is still no sound...

If you installed flash 10 but Firefox still shows Flash 9, then follow the instructions below:

> **lovinglinux said:**
> 
Some video issues are caused by conflicting plug-ins. It's not a good idea to have multiple plug-ins for the same type of content.

To remove conflicting flash plug-ins and install only the one from Adobe Open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash && sudo apt-get install flashplugin-nonfree 
```



More Firefox tweaks and tips in the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by susanpenter on 2009-07-04
> **lovinglinux said:**
> If you installed flash 10 but Firefox still shows Flash 9, then follow the instructions below:



More Firefox tweaks and tips in the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

I have followed these instructions and there is still no sound.....

and still this from about : plugins

    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

---

### Post by lovinglinux on 2009-07-04
I went through all the posts in the thread to try to understand your situation. I will try to help, but I need some additional information and I need you to follow all my instructions without skipping any steps.

What we are going to do?

1 - Restore your old profile and backup it appropriately so you can keep your extensions and settings
2 - Remove all Firefox versions, except the official one
3 - Remove all flash plugins that might be causing the problem
4 - Restore the applications you need and the necessary plugins

First I need to know were your original Firefox profile was and which Firefox you was using the extensions?

The Firefox 3.0.11 profile resides under ~/.mozilla/firefox
The Firefox 3.5 profile resides under ~/.mozilla/firefox-3.5
The Swiftfox profile is the same as Firefox 3.0.11

I understand you already moved the /.mozilla folder. The problem is that I don't know how many times you moved or rename it after so many suggestions in the thread.

It seems that you have

/home/susan/.mozilla/ - which the current home of Firefox profiles
/home/susan/.mozilla.backup/ - which seems to have the original profiles
/home/susan/.mozilla_old/ - which is probably a backup of a clean profile

Please confirm this. Also, open them and check if there are any firefox-3.5 folder inside. It would be also helpful if you could inspect all firefox folders inside them and check which one has more files inside the extensions folder. This we can determine which one is the original profile with all your extensions.

I also need to know which Firefox you want to keep, not counting the original Firefox 3.0.11? Keep in mind that it seems the original Firefox 3.0.11 will soon be updated to 3.5. So there is no reason to keep those extra versions, unless you can't wait.

Are you still using Swiftfox? Do you know which version it is: swiftfox-prescott, swiftfox-i686, swiftfox-athlon64-32bit?

---

### Post by susanpenter on 2009-07-04
Thanks Lovinglinux.  I am quite happy to work through the steps but I have to go to bed now as it is 1am here and I have to be out in the morning.  When I get back I will start working on it and be in contact again tomorrow.

Thanks,

Susan

---

### Post by lovinglinux on 2009-07-04
> **susanpenter said:**
> thanks lovinglinux.  I am quite happy to work through the steps but i have to go to bed now as it is 1am here and i have to be out in the morning.  When i get back i will start working on it and be in contact again tomorrow.

Thanks,

susan

ok

---

### Post by lovinglinux on 2009-07-04
> **lovinglinux said:**
> ok

Feel free to send me a PM when you are ready.

---

### Post by Ajat on 2009-07-05
Hi, excuse i'm joining.. since i also have the same problem (i did everything told on this thread and got the same result as susanpeter)..

But I think I've made a "progress" , i'm using kubuntu 9.04 Jaunty package.

I typed ```
 sudo apt-get install padevchooser 
``` 
then the PulseAudio is installed.

Then I opened System Settings - Multimedia - 
I choose PulseAudio for all Audio Output (Notification,Music,Video,Communication,Games,Accesbility)
Then when I click the "test" button, I hear a "robotic" sound (at least a sound from my speaker)
 
I open YouTube with firefox, I hear similar sound (that Robotic sound)

Maybe if we can configure the PulseAudio to get the clear sound then the problem is resolved.
But i have no idea about how to configure it.

thanks.. i'm glad to hear another progress.

---

### Post by susanpenter on 2009-07-05
Hi I have some time to work through this now.

I do have these:
/home/susan/.mozilla/ - which the current home of Firefox profiles
/home/susan/.mozilla.backup/ - which seems to have the original profiles
/home/susan/.mozilla_old/ - which is probably a backup of a clean profile

although the backup and old seem to be the same within.
I think the top i the one I am using now. 
I probably do not need to re-use old ones as I have re-installed the most vital extensions into this clean one and it is running much faster.

Although my bookmarks are safe online it may be useful to have those back though.

The top one does not have any FF 3.5 folders inside the others do.

I want to keep using the FF 3.5 version, i have not used Swiftfox since I installed FF3.5, I'm not sure which version it is but I' leaning towards the third option.

---

### Post by lovinglinux on 2009-07-05
> **susanpenter said:**
> Hi I have some time to work through this now.

I do have these:
/home/susan/.mozilla/ - which the current home of Firefox profiles
/home/susan/.mozilla.backup/ - which seems to have the original profiles
/home/susan/.mozilla_old/ - which is probably a backup of a clean profile

although the backup and old seem to be the same within.
I think the top i the one I am using now. 
I probably do not need to re-use old ones as I have re-installed the most vital extensions into this clean one and it is running much faster.

Although my bookmarks are safe online it may be useful to have those back though.

The top one does not have any FF 3.5 folders inside the others do.

I want to keep using the FF 3.5 version, i have not used Swiftfox since I installed FF3.5, I'm not sure which version it is but I' leaning towards the third option.

OK. Let's get started. Instead of posting a big tutorial, I will post some steps and wait for your confirmation, OK?

Please inform me about any errors you get in the Terminal output.

First, let's backup the profiles:

```
zip -r $HOME/mozilla-backup.zip $HOME/.mozilla/ $HOME/.mozilla.backup/ $HOME/mozilla_old/
```

This will save a zip file in your home directory containing all three mozilla folders.

Now delete the unnecessary mozilla folders

```
rm -fr /home/susan/.mozilla.backup
rm -fr /home/susan/.mozilla_old
```

Now open /home/susan/.mozilla/plugins/  and delete all flash related files form it.

Please inform when done.

---

### Post by lovinglinux on 2009-07-05
I think maybe it's better to do this by PM, instead of posting. What do you think?

---

### Post by lovinglinux on 2009-07-05
After completing the steps from post [#55](http://ubuntuforums.org/showpost.php?p=7564550&postcount=55), let's remove the unnecessary Firefox versions:

```
sudo apt-get remove swiftfox-prescott swiftfox-i686 swiftfox-athlon64-32bit firefox-3.1 firefox-3.5 adobe-flashplugin flashplugin-installer flashplugin-nonfree flashplugin-nonfree-extrasound libflashsupport swfdec-mozilla mozilla-plugin-gnash

```

The terminal will probably say there a few packages are not installed. Don't worry, I'm including them because I'm not sure which ones you have.

It seems that you have a Firefox 3.5 on your home folder right?

Delete that too. Did you took any steps to make the Firefox launcher load the version from your home directory or you click the Firefox executable inside it?

If you changed the launcher, revert it to the original **firefox %u**

---

### Post by lovinglinux on 2009-07-05
After completing the steps from post [#57](http://ubuntuforums.org/showpost.php?p=7564680&postcount=57)

Let's install flash again than Firefox 3.5 official release from Mozilla.

Run this command:

```
sudo apt-get install flashplugin-nonfree flashplugin-nonfree-extrasound
```

Go to [http://www.getfirefox.com](http://www.getfirefox.com) and download the official release for your system. It should detect your system specs and give you the right package. Save the file ins your home directory. The file name should be firefox-3.5.tar.bz2. Don't change it.

Now run the following commands:

```
sudo tar -jxvf firefox-*.tar.bz2 -C /opt
rm firefox-*.tar.bz2
sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```


Start Firefox and check the version through the menu "Help >> About Mozilla Firefox". It should say "Forefox version 3.5" and display something like *Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1) Gecko/20090705 Firefox/3.5* at the bottom.

Then open "Tools >> Addons", select the plugin tab, click over the "Shockwave Flash" plugin and check it's version. It should be 10.0 r22.

Now visit [http://www.youtube.com/watch?v=oHg5SJYRHA0](http://www.youtube.com/watch?v=oHg5SJYRHA0) and check if you have video and sound.

---

### Post by susanpenter on 2009-07-05
sorry I hadn't noticed that you were posting on the board as well.

When I put in the delete command from #57 I got this code:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package swiftfox-prescott

```

It looks like ot only accepted the first of the string....

---

### Post by lovinglinux on 2009-07-05
> **susanpenter said:**
> sorry I hadn't noticed that you were posting on the board as well.

When I put in the delete command from #57 I got this code:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package swiftfox-prescott

```

It looks like ot only accepted the first of the string....

Ok, but the rest of were removed right?

---

### Post by susanpenter on 2009-07-05
no swiftfox is still in the internet menu

---

### Post by lovinglinux on 2009-07-05
> **susanpenter said:**
> no swiftfox is still in the internet menu

Not necessarily. Sometimes it just go away from the menu when you log out and login again. Anyway, let's brake that command into parts. Run each one separately and post any errors:

```
sudo apt-get remove swiftfox-prescott 
sudo apt-get remove swiftfox-i686 
sudo apt-get remove swiftfox-athlon64-32bit 
sudo apt-get remove firefox-3.1 
sudo apt-get remove firefox-3.5 
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-installer
sudo apt-get remove flashplugin-nonfree
sudo apt-get remove flashplugin-nonfree-extrasound
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
```

---

### Post by susanpenter on 2009-07-05
I've followed #62 and then #58 and I now have version 3.5 with sound!!!!!!!!!

Amazing thank you - however I only have the extension that I had added into the new version so I still need to get back the bookmarks that we archived away.  I'm not as bothered about extensions as I can re get anything else I need but I've realized that there were bookmarks that are not in my external saved file.....

---

### Post by lovinglinux on 2009-07-05
> **susanpenter said:**
> I've followed #62 and then #58 and I now have version 3.5 with sound!!!!!!!!!

Amazing thank you - however I only have the extension that I had added into the new version so I still need to get back the bookmarks that we archived away.  I'm not as bothered about extensions as I can re get anything else I need but I've realized that there were bookmarks that are not in my external saved file.....

You are welcome. I'm glad it worked.

Did you liked the RickRoll'd video? :)

OK. Let's restore your bookmarks backups. Run the following commands:

```
mkdir ~/bookmarksbackup
mkdir ~/bookmarksbackup/tmp
unzip ~/mozilla-backup.zip */bookmarkbackups/*.json -d ~/bookmarksbackup
rm -fr ~/bookmarksbackup/tmp
mv ~/bookmarksbackup/home/susan/.mozilla/firefox/*/bookmarkbackups/*.json ~/bookmarksbackup
rm -fr ~/bookmarksbackup/home

```

This will copy all your bookmark backups to the foler ~/bookmarkbackup.

Then open Firefox, go to "Bookmarks >> Organize Bookmarks" then click "Import and Backup", then "Restore", then "Chose File", then browse the folder bookmarkbackup on your home directory and chose whichever backup you want.

---

### Post by susanpenter on 2009-07-05
> **lovinglinux said:**
> You are welcome. I'm glad it worked.

Did you liked the RickRoll'd video? :)

OK. Let's restore your bookmarks backups. Run the following commands:

```
mkdir ~/bookmarksbackup
mkdir ~/bookmarksbackup/tmp
unzip ~/mozilla-backup.zip */bookmarkbackups/*.json -d ~/bookmarksbackup
rm -fr ~/bookmarksbackup/tmp
mv ~/bookmarksbackup/home/susan/.mozilla/firefox/*/bookmarkbackups/*.json ~/bookmarksbackup
rm -fr ~/bookmarksbackup/home

```

This will copy all your bookmark backups to the foler ~/bookmarkbackup.

Then open Firefox, go to "Bookmarks >> Organize Bookmarks" then click "Import and Backup", then "Restore", then "Chose File", then browse the folder bookmarkbackup on your home directory and chose whichever backup you want.

Unfortunately this hasn't worked it must be a back up from the new installation

---

### Post by susanpenter on 2009-07-05
All is ok, I searched through the backup zip and found the latest backup file.

Many thanks for all your help.

Susan

---

### Post by lovinglinux on 2009-07-05
> **susanpenter said:**
> All is ok, I searched through the backup zip and found the latest backup file.

Many thanks for all your help.

Susan

You are welcome.

Now visit [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567) and take a look at the backup section to avoid future problems. Firefox profiles can become corrupted very often.

---

### Post by Aviendha09 on 2009-08-19
I followed (read) this thread since I have the same problem. Is the solution to stick with firefox shiretoko? It seems in the end susan no longer uses swiftfox ! I have the latest flashplayer, I installed the extrasound bit. But no sound yet. I just switched to pulse audio, lets see...

edit: nope.  "applications using sound" flashes like crazy, volume is on high.

---

