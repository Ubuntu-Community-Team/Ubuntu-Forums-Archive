---
title: "Hulu."
date: 2009-09-30
forum: New to Ubuntu
---

### Post by mastermael on 2009-09-30
I am completely new to ubuntu, and tried to watch a show on 
[COLOR=Red]hulu[/COLOR].com all i got was a black screen, i have tried looking it up, but have had little sucess. anyone able to help me?

---

### Post by zeroseven0183 on 2009-09-30
Does the website need Adobe Flash Player to view the movies?

If yes, you can download the .deb file and install it from [Adobe Flash Player (Ubuntu)]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb%29")

---

### Post by QIII on 2009-09-30
I could send you to the "terminal", but I'll be kind and send you to a GUI.

Go to System | Administration | Synaptic Package Manger.

You will be asked for your password.  Don't panic.  That's the same password you use to sign in.

It will take a minute or two to create a search index if this is your first time using Synaptic.

When you can, use the "Quick search" box and type in "flashplugin".

You should get two selections.  Flashplugin-installer and flashplugin-nonfree.

Select them both and select "Mark for installation", then click Apply.

After a few moments, the packages will be applied.

Now search for "swfdec" and "gnash" and if they are checked mark them for removal and apply.

Now, when you go to a flash website, flash will be installed.

We won't get into 32/64 bit flash at this point.  That is a class for later.

---

### Post by QIII on 2009-09-30
> **zeroseven0183 said:**
> Does the website need Adobe Flash Player to view the movies?

If yes, you can download the .deb file and install it from [Adobe Flash Player (Ubuntu)]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb%29")


For someone who describes himself as new to Ubuntu, instructions like that are likely to be somewhat less than helpful...

---

### Post by zeroseven0183 on 2009-09-30
> **QIII said:**
> For someone who describes himself as new to Ubuntu, instructions like that are likely to be somewhat less than helpful...

Yeah right, thank you for the lesson professor.

---

### Post by mastermael on 2009-09-30
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
this is the error i get when trying to use the package manager, i have limited knowledge of the terminal. i did not run the installation of this computer. 

i have already installed the adobe flash player, as it hasnt stopped he blackness i see i thought it was not the probleam

---

### Post by QIII on 2009-09-30
> **zeroseven0183 said:**
> Yeah right, thank you for the lesson professor.

Yeah.  No problem.  35 years ago I considered myself a computer expert.  It wears off.

By the way.  If he has a 64 bit machine, are you going to explain to him what the message he receives means?

---

### Post by QIII on 2009-09-30
Go to Applications | Accessories | Terminal and type

```
sudo dpkg --configure -a
```

You will be asked for your password again.  Type it in, but you won't see any characters rendered in the terminal.

Did you remove swfdec and gnash?

---

### Post by mastermael on 2009-09-30
the only plugins i see are: Adobe-flashplugin, and flashplugin-nonfree

---

### Post by QIII on 2009-09-30
Did you run dpkg --configure -a?

---

### Post by mastermael on 2009-09-30
that i did, thats the only reason i can now run the package manager, before i couldnt do that and this time i got no error

Fyi, maybe will have no impact but i jumped from version 4 something straight to 8.04. as this is a sperate harddisc in my *box* my windows recently crash (again) so i decided to fully switch to a linux software. i hadnt used this harddisc in sometime.

---

### Post by zeroseven0183 on 2009-09-30
What happens if you watch movies on other websites like YouTube?
Do you encounter the same error?

---

### Post by QIII on 2009-09-30
Disk and Ubuntu version are not likely culprits.

Could you go to 

[http://www.adobe.com/products/flashplayer/](http://www.adobe.com/products/flashplayer/)

and tell me if you can see the flash media there?

---

### Post by mastermael on 2009-09-30
yes, it apperently played but i did not see/hear it, and youtube gave an option to upgrade for better playback feature

---

### Post by QIII on 2009-09-30
What browser are you using?

If Firefox, open a new tab and type about:plugins in the nav bar.

Scroll down and look for Flash and see if you have an entry like "Flash 10.0 r32"

Sorry, the smiley face thing is irritating!  "about" followed by a colon followed by "plugins"

---

### Post by mastermael on 2009-09-30
**Shockwave Flash**

 File name:  libswfdecmozilla.so Shockwave Flash 9.0 r100 

Like this?

---

### Post by QIII on 2009-09-30
You are apparently using swfdec, which conflicts with Flash.

Go back to Synaptic and search for "swfdec".  Select it for removal and apply.

We'll see if that works.  If not, we may have to remove flash and reinstall.  I'm not sure if the repositories for Hardy have Flash 10, but I would assume they do...


Edit:  I didn't proof read before posting.  swfdec may take out the GNOME dependencies if you use "complete removal", which I corrected to "removal".  Before you reboot, go to the terminal and type

```
sudo apt-get install ubuntu-desktop
``` 

before you end up cursing all night.

---

### Post by mastermael on 2009-09-30
I wandered off and did some stuff myself after you told me to remove swfdec. it now works for youtube, i am checking hulu right after i post this. 
IT WORKS!
Thank You So Much For Your Help!

---

### Post by QIII on 2009-09-30
BE SURE to do the reinstall of the gnome desktop if you used "complete removal".  Bonehead mistake on my part, since in my first post I said "removal".

If you haven't removed the desktop, the worst that will happen is that you will be given a message that you already have the newest version.

If you reboot and it's gone, all you have to do is type the command I gave above into the command line to restore it.

Jot the command down just in case.


When you get comfortable with Ubuntu and have had a chance to kick the tires, we can work through making sure you have the 64 bit version -- but only if you have a 64 bit machine.  The 64 bit version of Flash is much, much better.

---

### Post by mastermael on 2009-09-30
I jotted it down, THANK YOU SO MUCH FOR ALL THE HELP YOU GAVE ME! 
i will ask for your help if i get in more trouble with ubuntu =)

---

### Post by QIII on 2009-09-30
There are a thousand people here who have vastly greater wisdom than I do.  And it's a collective effort, so there are a lot of people around to help.

Cheers!  And welcome to Ubuntu.

---

### Post by mastermael on 2009-10-05
BUMP,

my Hulu stopped working, and other advice, i went through most of this stuff again.

---

### Post by tom.swartz07 on 2009-10-05
> **mastermael said:**
> BUMP,

my Hulu stopped working, and other advice, i went through most of this stuff again.

Could you remember what you were doing just before you noticed it stopped working?

check the about: plugins again and post back with what file you are using.

There is a possibility that something may have been reinstalled after you ran the reinstall ubuntu-desktop command.

---

### Post by mastermael on 2009-10-05
Shockwave flash:

libflashplayer.so
shockwave flash10.0 r32
MIME                                      Type                    Description   Suffixes    Enabled 
application/x-shockwave-flash   Shockwave             Flash                swf         Yes 
application/futuresplash           FutureSplash          Player              spl          Yes


And i restarted my computer. then it wouldnt run.

---

### Post by tom.swartz07 on 2009-10-05
> **mastermael said:**
> Shockwave flash:

libflashplayer.so
shockwave flash10.0 r32
MIME Type Description Suffixes Enabled    application/x-shockwave-flash Shockwave Flash swf Yes   application/futuresplash FutureSplash Player spl Yes

Alrighty, flash is correctly installed. Check and make sure that your system is up to date by going to system/administration/update manager. It will ask for your password, enter it and make sure you install any updates listed there.
While that is going on, could you verify that your problem is not only limited to Hulu? Try youtube or some other sites you know of that use flash. Did you recently install some other software?

If it is only Hulu, then its a different problem, but if it is everything, then we could start in on the work to figure out what happened.

---

### Post by mastermael on 2009-10-05
It is not limited to hulu, it goes for all video viewing sites i went to, the updates are installing as we speak, no i didnt update anything, my computer was not running for 5 days because i moved.

Updated

---

### Post by tom.swartz07 on 2009-10-05
Next we have to determine your version of Ubuntu. Could you please go into applications/accessories/terminal and enter
```
uname -a
```
Then copy the result here? (The keyboard shortcut to copy in that program is ctrl+shift+c)
This will tell us if you are using the 32bit or 64bit version. 
32 bit is shown as:```
Linux 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 **x86 GNU/Linux**
```
and 64bit:
```
Linux 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 **x86_64 GNU/Linux**
```

There are different methods for the 2 systems.

If you have the 32bit, try uninstalling the flash plugin, and re-installing it. If you need help with this, we could help, but it is fairly well covered in several other forum posts.

If you have 64bit- you should upgrade to the 64bit version of flash. [Flash Player 10 for Ubuntu 64 bit]("http://labs.adobe.com/downloads/flashplayer10.html")
You download that, open it, and copy and replace it in the folder located in ~/.mozilla/plugins/. After it is copied, restart firefox, and make sure that it works by checking about:plugins again. It should be libflashplayer.so

If you need any help along the way, feel free to give us a holler!

Hope this helps! Cheers!

---

### Post by mastermael on 2009-10-05
2.6.24-24-generic #1 SMP Fri Sep 18 16:49:39 UTC 2009 i686 GNU/Linux

this is the reply i get

im guessing 32 bit?

---

### Post by QIII on 2009-10-06
Can you see flash content using Applications | Internet | Epiphany Web Browser?

I think Epiphany is installed by default.

---

### Post by tom.swartz07 on 2009-10-06
> **mastermael said:**
> 2.6.24-24-generic #1 SMP Fri Sep 18 16:49:39 UTC 2009 i686 GNU/Linux

this is the reply i get

im guessing 32 bit?

Yessir! You have one of the best of the best 32 bit processors, and the OS will take care of it!

Like I said, try uninstalling it. 
In the terminal type
```
sudo apt-get remove --purge flashplugin-installer
```
This will remove flash completely.
Next, type
```
cd ~/.mozilla/plugins/
```
and then type ls (lowercase L and S; it lists the files in the location)
Make sure that you do not have a libflashplayer.so file listed there. If you do, type ```
sudo rm libflashplayer.so
```

FINALLY- type this into the terminal:
```
sudo apt-get install flashplugin-installer
```
Enter your password and you should be all set!

---

### Post by lavinog on 2009-10-06
> **mastermael said:**
> 2.6.24-24-generic #1 SMP Fri Sep 18 16:49:39 UTC 2009 i686 GNU/Linux

this is the reply i get

im guessing 32 bit?

correct

---

### Post by mastermael on 2009-10-06
> **QIII said:**
> Can you see flash content using Applications | Internet | Epiphany Web Browser?

I think Epiphany is installed by default.

Yes i can see content through epiphany. although i would like to see it through firefox. i will see iif reinsttalling helps and if not i will use epiphany

---

### Post by QIII on 2009-10-06
Are you using AdBlock?  (Not AdBlock Plus)

The original AdBlock was problematic.

If you are using AdBlock Plus, you will need to disable it for Hulu.  Apparently, Hulu doesn't like to play if you don't want to watch the ads from their sponsors.

---

### Post by mastermael on 2009-10-06
how do i figure out if i am using adblock? and how do i disable it

---

### Post by QIII on 2009-10-06
You would probably know if you had installed it as an add-on to Firefox, so you probably aren't.  That would tend to kill that line of troubleshooting.

But just in case:  Is there a red "stop sign" near the upper right hand corner of the FF GUI?

---

### Post by mastermael on 2009-10-06
> **tom.swartz07 said:**
> Yessir! You have one of the best of the best 32 bit processors, and the OS will take care of it!

Like I said, try uninstalling it. 
In the terminal type
```
sudo apt-get remove --purge flashplugin-installer
```This will remove flash completely.
Next, type
```
cd ~/.mozilla/plugins/
```and then type ls (lowercase L and S; it lists the files in the location)
Make sure that you do not have a libflashplayer.so file listed there. If you do, type ```
sudo rm libflashplayer.so
```FINALLY- type this into the terminal:
```
sudo apt-get install flashplugin-installer
```Enter your password and you should be all set!


E: Couldn't find package flashplugin-installer 
error after first one.

---

### Post by tom.swartz07 on 2009-10-06
> **mastermael said:**
> E: Couldn't find package flashplugin-installer 
error after first one.

Just keep going then. Apparently, this was the cause- you didnt have the proper package installed.

Follow the instructions to remove the file from .mozilla.
BEFORE you use the command to install flash, (sudo apt-get install flashplugin-installer)

Type ```
locate libflashplayer.so
``` and post back the results. Ideally, there should be no entries returned, but if there are, we have to remove them manually.

If you see that there are other locations listed, they would most likely be located in ```
/usr/lib/mozilla/plugins/
```
To remove it, use ```
sudo rm /usr/lib/mozilla/plugins/libflashplayer.so
```
"sudo rm" indicates that you would like to remove the file (rm) and *do* it with *super* privileges (sudo)

After that, simply run the command from the previous post to install flashplugin-installer.
Also, lets do a little housekeeping. Q111 mentioned that the problem *might* also be caused by Adblock. In Firefox, click on tools/add-ons. Across the top of the window, there are a few tabs; click on the 'Extensions' tab. *IF* you have AdBlock installed, it will be listed here. If its not, there is no need to worry about that. If it is installed, however, you will have to go to this location and disable it whenever you go to Hulu. 

Everything should be fine after that!

---

### Post by mastermael on 2009-10-06
bash: cd: /home/ben/.mozilla/plugins/: No such file or directory

After I use :~$ cd ~/.mozilla/plugins/

---

### Post by mastermael on 2009-10-06
> **tom.swartz07 said:**
> Just keep going then. Apparently, this was the cause- you didnt have the proper package installed.

Follow the instructions to remove the file from .mozilla.
BEFORE you use the command to install flash, (sudo apt-get install flashplugin-installer)

Type ```
locate libflashplayer.so
``` and post back the results. Ideally, there should be no entries returned, but if there are, we have to remove them manually.

If you see that there are other locations listed, they would most likely be located in ```
/usr/lib/mozilla/plugins/
```To remove it, use ```
sudo rm /usr/lib/mozilla/plugins/libflashplayer.so
```"sudo rm" indicates that you would like to remove the file (rm) and *do* it with *super* privileges (sudo)

After that, simply run the command from the previous post to install flashplugin-installer.
Also, lets do a little housekeeping. Q111 mentioned that the problem *might* also be caused by Adblock. In Firefox, click on tools/add-ons. Across the top of the window, there are a few tabs; click on the 'Extensions' tab. *IF* you have AdBlock installed, it will be listed here. If its not, there is no need to worry about that. If it is installed, however, you will have to go to this location and disable it whenever you go to Hulu. 

Everything should be fine after that!

/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/xulrunner-addons/plugins/libflashplayer.so
these are the places after the first command line

ben@benxubu:~$ sudo apt-get install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-installer

---

### Post by achase79 on 2009-10-06
flash plugin version 10 is in the backports repository in Hardy.  It is not activated by default.  You can go to system -> administration -> software sources and add the backports repository. Then update in synaptic and install.

---

### Post by QIII on 2009-10-06
Since flash seems to be working in epiphany, I am disinclined to believe anything is installed incorrectly.

However, you may try this:

```
sudo apt-get install --reinstall flashplugin-nonfree
```That will accomplish the same thing as selecting it for reinstall from Synaptic.  It will also keep you from tracking down and removing a bunch of files.

You already had Flash 10 installed, so I don't think there is any need to go to the backports.

If you are running a 32 bit system, you'll get 32 bit Flash back anyway.

As I said, we can work on 64 bit a little later when you are more familiar...

EDIT:  Hmmm.  Another thought.  In FF, you might go to Tools | Add-ons and see if Iced Tea is enabled.  If it is, disable it.

---

### Post by Xeginy on 2009-10-06
I was having the same problems with Hulu that whoever started this thread said they were having (black screen), I followed the directions that QIII gave on the first page, and it worked great.  Just wanted to say thanks!

---

### Post by mastermael on 2009-10-06
> **Xeginy said:**
> I was having the same problems with Hulu that whoever started this thread said they were having (black screen), I followed the directions that QIII gave on the first page, and it worked great.  Just wanted to say thanks!

Great! im glad you found help

---

### Post by mastermael on 2009-10-06
> **QIII said:**
> Since flash seems to be working in epiphany, I am disinclined to believe anything is installed incorrectly.

However, you may try this:

```
sudo apt-get install --reinstall flashplugin-nonfree
```That will accomplish the same thing as selecting it for reinstall from Synaptic.  It will also keep you from tracking down and removing a bunch of files.

You already had Flash 10 installed, so I don't think there is any need to go to the backports.

If you are running a 32 bit system, you'll get 32 bit Flash back anyway.

As I said, we can work on 64 bit a little later when you are more familiar...

EDIT:  Hmmm.  Another thought.  In FF, you might go to Tools | Add-ons and see if Iced Tea is enabled.  If it is, disable it.

After running 
sudo apt-get install --reinstall flashplugin-nonfree i get
download failed
The Flash plugin is NOT installed.

yet if i try to reinstall from 
[http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb](http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb))
and run the install, i get :Error a later version is already installed

---

### Post by mastermael on 2009-10-06
BUMP, anyones help is appreicated, and thanks to all who tried to help =)

---

### Post by QIII on 2009-10-06
"download failed" would seem to indicate a simple failure to connect to the source and transfer the data.

It might be worth just giving it another try.

---

### Post by mastermael on 2009-10-07
> **QIII said:**
> "download failed" would seem to indicate a simple failure to connect to the source and transfer the data.

It might be worth just giving it another try.

I just upgraded to next level of ubuntu and its started working fine. thanks for alll the help tho.

---

