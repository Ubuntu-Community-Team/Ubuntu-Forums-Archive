---
title: "Installing Login splash theme"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by D-Train on 2011-01-10
Hey guys,
I am a computer geek but new to Ubuntu, I love it so far!

OK, here is my 1st newbie question:

I am running Ubuntu 10.10 and am in fact typing this message on it.
If I go into system preferences/appearance/theme and click on "get more themes online" then click on "Login Screen" here: [http://art.gnome.org/themes/gdm_greeter](http://art.gnome.org/themes/gdm_greeter)
and download one of the login screens shown that I want to install, how do I install it? I downloaded the file, extracted it, (also tried installing it by leaving it as a .tar.gz file) so I guess my first question is where is the best location to extract these files to? Then once they are extracted what do I do with them then? I tried dragging the JPG into my themes window and now I can use the JPG as my desktop, but I want to use it as my login screen instead. I don't see a way to choose a new login screen?

A friend at work who is an Ubuntu geek said I need to use apt-get to install it but from what I can find out about apt-get (on the Ubuntu help pages) it requires a .DEB file to install, and the downloaded themes I've got are .TAR.GZ files which seems to be what I need if I click on "install" from my appearance preferences window, but that doesn't work either because what I am trying to install is not a whole new theme but just a new login screen and the installer says that it does not appear to be a valid theme I am trying to install.

Help!?!?

---

### Post by Eternal_Light on 2011-01-11
Well, if you have the .tar.gz file downloaded anywhere (lets say ~/Downloads) you just have to go to the system preferences appearence theme as u did but instead of get more themes you have to click on "Install a theme". Browse to ~/Downloads and select the .tar.gz. It will autoinstall and show in the list of themes. If you get an error it might mean that the theme could be for a different (older) version of gnome or gdm or whatever programs are used to launch the splash screen.
So if you have trouble installing a theme try getting a couple of others working to see if it is your problem or was it just the incompatibility of one theme.

---

### Post by JOHNNYG713 on 2011-01-11
Ubuntu 10.10 does not use GDM any more (GDM's apply to 8.10 and earlier) the Plymouth splash screen and log in screen are incorporated ! I suggest installing Python gdm2 to change the appearance of your login screen ! [http://launchpad.net/gdm2setup/0.2/0.5.0/+download/python-gdm2setup.deb](http://launchpad.net/gdm2setup/0.2/0.5.0/+download/python-gdm2setup.deb)

and to mange and install new plymouth themes I recommend Zorin splash screen manager !
[http://gnome-look.org/content/download.php?content=134231&id=1&tan=84589074](http://gnome-look.org/content/download.php?content=134231&id=1&tan=84589074)

---

### Post by D-Train on 2011-01-11
Thanks Eternal_Light, like I said in my original email:

*the downloaded themes I've got are .TAR.GZ files which seems to be what I  need if I click on "install" from my appearance preferences window, but  that doesn't work either because what I am trying to install is not a  whole new theme but just a new login screen and the installer says that  it does not appear to be a valid theme I am trying to install.*

One theme I downloaded has 3 files in it, a JPG, an XML file and a file with the extension .desktop (desktop configuration file) the installer doesn't like these files when I point to them in their .tar.gz form.

I even downloaded a program from the Ubuntu Software Center called Art Manager that is supposed to install art found on the art.gnome.org website. 

But when I select "login manager" the choices all have "install" disabled and I can only select "download only" on those, but once I download them I'm still stuck. 

If I understand JohnnyG correctly there is no way to edit this with Ubuntu 10.10 (actually it says I'm running Ubuntu 11.4, I guess I'm a time traveller that's come back from the future! :D

SO I guess I'll have to install Python GDM2 if I want to use a different login screen. :(

---

### Post by D-Train on 2011-01-11
Hey JohnnyG713,

I've installed Python GDM2 and the Zorin theme manager and actually figured out how to use them, sorta.

I downloaded some Plymouth themes from gnome-look.org and figured out how to install them, the archives are put into /lib/plymouth/themes/*whatever* and then I've clicked on "change default theme", navigated to this location, picked one of the themes I downloaded and it said my theme has been changed. Then I restarted Ubuntu and I still have the same initial ugly splash screen. 

So what am I doing wrong?

---

### Post by yojoe on 2011-01-11
If you install ubuntu tweak, it will let you change a lot of things all in one place, i changed my login screen background, and ubuntu logo. i did change my splash screen but its been so long, i dont remember how to do it, sorry. lol

---

### Post by lbarnes on 2011-01-12
> **D-Train said:**
> Hey JohnnyG713,

I've installed Python GDM2 and the Zorin theme manager and actually figured out how to use them, sorta.

I downloaded some Plymouth themes from gnome-look.org and figured out how to install them, the archives are put into /lib/plymouth/themes/*whatever* and then I've clicked on "change default theme", navigated to this location, picked one of the themes I downloaded and it said my theme has been changed. Then I restarted Ubuntu and I still have the same initial ugly splash screen. 

So what am I doing wrong?

[http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html]("http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html")

---

### Post by D-Train on 2011-01-12
OK, I feel like a total dumba$$ now. I just noticed in System>Administration there are a "Login Screen" and "Login Screen (GDM2Setup)" options. I only noticed the "Splash Screen Manager" option before.  D'ohhhh!

I tried clicking on these (tried the GDM2Script one first) and that let me navigate to the new wallpaper that I wanted to use, but when I clicked on the JPG and said OK, nothing happens (OK button doesn't go away). Does my wallpaper have to be some other format besides a JPG or JPEG? 

When I tried the other option (Login Screen, not GDM2Setup version) I am even less successful. I can navigate to my downloads folder where there's a couple of JPG's (the rest are still in .tar.gx format) and it doesn't even display the images when I click on their containing folders, I just get a blank gray window. So again, does this one only show files with a certain file extension, such as PNG, or something else? 

I'm bound and determined to figure this out. It shouldn't be rocket science. :confused:

OK here's one other really dumb question. Where does the splash screen show? Is that the plain screen that just says "Ubuntu" with the animated 5 dots below it that shows before the login window? I've set my splash screen to different things but always see the same thing as before. It's not my desktop wallpaper, and it's not the login screen wallpaper, so what exactly is the splash screen? (go ahead and laugh, but I'm not really as dumb as I sound, just confused by this new OS)

Thanks!

---

### Post by D-Train on 2011-01-12
Sorry, duplicate posting, was getting no response from forum, then it posted my reply 3x!

---

### Post by D-Train on 2011-01-12
Sorry, duplicate posting, was getting no response from forum, then it posted my reply 3x!

How do I delete this? The button at the bottom says "edit/delete" but I see no way to delete my dupes?

---

### Post by JOHNNYG713 on 2011-01-12
This may sound a bit odd But, go to synaptic package manager and search xsplash and install, Python gdm2 will place your background for your login screen, and pull from there, and the "login screen' option will now be  unused ! and yes the Plymouth splash screen is that wonderful purple background with the 5 dots !
Note: on Changing the login box via Python gdm2,  New themes you install via appearances, will only show up in the Python gdm2 menu if you open a teminal type gksudo nautilus enter your password when prompted, navigate system>home>yourname, Then press Cntl+h, This will open hidden folders, Copy the contents of .themes to file system>usr>share>themes, then go back to your home "unhidden folders" and delete the themes in .themes ( or you will have two instances show up in appearances menu of themes ), do the same for .icons, place the content of .icons in file from your unhidden home folers, To system>usr>share>icons then back to unhidden  home folder> .icons and delete the content in .icons folder.

And I am not sure why you get the "grayed out" folders thing ! Maybe show us a screenshot !

And the set "splash screen" **WAS** a small pic shown just before your desktop loaded but is now inop!
 Hope this helps ! :)

---

### Post by D-Train on 2011-01-12
Hi Johnny,
Thanks for the reply. Of course every time you tell me something to try I end up with even more questions than before. ROFL!

First off is "synaptic package manager" what runs when you install stuff from the Ubuntu Software Center? If so I went there and installed xsplash. Now what? :)

I also did like you said and after I typed gksudo nautilus I got the following error message in terminal:

(nautilus:5507): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
eedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '5507'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

I also followed your instructions and navigated to my user folder using Nautilus and opened .themes  but this folder was EMPTY !
Was that not expected? :(

As far as the grayed out folders, I think you misunderstood. What's interesting is if I select System>Administration>Login Screen (GDM2Setup) then select the Wallpaper tab, then click "select new image" I can see a bunch of new images in the /usr/share/images folder that it goes to automatically. But from this screen I cannot do anything. I click on a new image then click OK, nothing happens. I can't even click on "cancel" this screen seems locked up when OK and Cancel are both non-responsive. All I can do is close this window by clicking the X to close it. WTF?? :confused:

Thanks for your patience. I answer the phones all day and provide tech support for a major computer company and customers thank me all day for being patient with them. Now I know how they feel. heh heh

---

### Post by D-Train on 2011-01-13
> **yojoe said:**
> If you install ubuntu tweak, it will let you change a lot of things all in one place, i changed my login screen background, and ubuntu logo. i did change my splash screen but its been so long, i dont remember how to do it, sorry. lol

Hey Joe, (where you going with that gun in your hand?) :P

Ummm, I searched the Ubuntu Software Center for Ubuntu Tweak but came up empty. Where do I get it and how do I install it? 

Thanks!

---

### Post by Johnce on 2011-01-13
[http://ubuntu-tweak.com/downloads/](http://ubuntu-tweak.com/downloads/)

:)

---

### Post by D-Train on 2011-01-13
> **Johnce said:**
> [http://ubuntu-tweak.com/downloads/](http://ubuntu-tweak.com/downloads/)

:)

[FONT=Verdana][SIZE=2]Ummm, OK I followed the link, then used terminal to enter the following command:[/SIZE][/FONT]
[COLOR=Black]
[COLOR=#666666]sudo add-apt-repository ppa:tualatrix/ppa

It seems to have worked, I think? But now what? I don't see any new choices under System>Preferences or System>Administration, so how do I use tweak? Did I properly install it or did I just add something to my environment variables or something? What else do I need to do? 
**Sorry if I seem dense, but this is confusing the crap outta me. :confused:**

Thanks for the help guys!

[/COLOR][/COLOR]

---

### Post by JOHNNYG713 on 2011-01-15
sorry, double post !](*,)

---

### Post by JOHNNYG713 on 2011-01-15
Ubuntu Tweak ! [http://launchpad.net/ubuntu-tweak/0.5.x/0.5.9/+download/ubuntu-tweak_0.5.9-1~natty1_all.deb]("http://launchpad.net/ubuntu-tweak/0.5.x/0.5.9/+download/ubuntu-tweak_0.5.9-1%7Enatty1_all.deb")
Synaptic package manager; System>Administration Synaptic package manager
and also search (in synaptic ) gksudo and see if it is installed ! ;)
 P.S. Sorry for the late response as I have had to work a lot of OT !
Also Ubuntu tweak will be in Preferences>System tools
and try Ailurus [http://code.google.com/p/ailurus/downloads/detail?name=ailurus_10.10.1-0maverick1_all.deb](http://code.google.com/p/ailurus/downloads/detail?name=ailurus_10.10.1-0maverick1_all.deb)

---

### Post by D-Train on 2011-01-15
> **JOHNNYG713 said:**
> Ubuntu Tweak ! [http://launchpad.net/ubuntu-tweak/0.5.x/0.5.9/+download/ubuntu-tweak_0.5.9-1~natty1_all.deb]("http://launchpad.net/ubuntu-tweak/0.5.x/0.5.9/+download/ubuntu-tweak_0.5.9-1%7Enatty1_all.deb")
Synaptic package manager; System>Administration Synaptic package manager
and also search (in synaptic ) gksudo and see if it is installed ! ;)
 P.S. Sorry for the late response as I have had to work a lot of OT !
Also Ubuntu tweak will be in Preferences>System tools
and try Ailurus [http://code.google.com/p/ailurus/downloads/detail?name=ailurus_10.10.1-0maverick1_all.deb](http://code.google.com/p/ailurus/downloads/detail?name=ailurus_10.10.1-0maverick1_all.deb)

Hey Johnny, welcome back! \\:D/
Umm, OK, it doesn't appear that I have Ubuntu Tweak installed. I went into my Synaptic Package Manager (never noticed it before, thanks for pointing it out!) and I see ubuntu-tweak listed but not installed. I've now installed it. :redface:

I don't have gksudo installed, nor do I see it listed as something available for install in SPM or on the Ubuntu Software Center. Where do I get it and how do I install it? :-?

After installing ubuntu-tweak using Synaptic Package Manage I still don't see anything called System>Preferences>System Tools
Even after a restart it doesn't appear. :confused:

Anyway, after playing around with Login Screen (GDM2Setup) I now have a pretty cool login screen, but still no splash screen. 

Uhh, how do I install .DEB packages ? Aren't those the files I need to use apt-get to install? If so I don't know the syntax for using it. 

I'm bound and determined to learn this stuff. Thanks for the help!

---

### Post by JOHNNYG713 on 2011-01-16
Ok My bad ! System tools is in Applications, I suggest you go through each menu item and see what there is, don't be shy, and don't try to "over think" linux ! .deb packages are self installing just double click, contrary to popular belief. you don't have to run commands in terminal all the time! as for your splash screen, It is no longer a functioning option after karmic! If you haven't installed any "new" Themes, icons or pointers your .themes and .icons folder in your home folder will be emty. And do you get any errors in terminal when you type **sudo nautilus** ?

---

### Post by Sh1n1g4m1 on 2011-01-16
.Deb package can be install as an .exe just double click on it

---

### Post by Sh1n1g4m1 on 2011-01-16
Sorry double post

---

### Post by D-Train on 2011-01-16
> **JOHNNYG713 said:**
> Ok My bad ! System tools is in Applications, I suggest you go through each menu item and see what there is, don't be shy, and don't try to "over think" linux ! .deb packages are self installing just double click, contrary to popular belief. you don't have to run commands in terminal all the time! as for your splash screen, It is no longer a functioning option after karmic! If you haven't installed any "new" Themes, icons or pointers your .themes and .icons folder in your home folder will be emty. And do you get any errors in terminal when you type **sudo nautilus** ?

Hey Johnny,
Nope, no System Tools anywhere on my system, not in Applications (or any of it's sub-folders) nor in System>Preferences or System>Administration. 

Didn't know that about .deb files. I read somewhere when I was researching the apt-get command that it said you must be trying to install a .deb file, so I assumed....

As far as errors running sudo plymouth goes, see message 12 in this thread. That's what I get when I run gksudo plymouth. So the question is, what's the difference between sudo and gksudo ??

Thanks bud!
:cool:

---

### Post by JOHNNYG713 on 2011-01-17
Ok those error messages in terminal you can ignore for now as long as your root nautilus window opens! (I get the same errors on mine, has to do with file sharing or samba or something!) Sudo nautilus makes any file or folder you copy and past or create have "Root" ownership meaning it will be locked to you as user (Unless you change permissions!) gksudo nautilus gives you the user root permissions while maintaining user ownership !

You say you have Ubuntu tweak installed? where do you see it? under what menu heading?
Have you tried ailiurus ?
 And sudo plymouth and gksudo plymouth are not commands!

 I know that learning this can and will be frustrating at times ! but once you see how things run you will be amazed at how really simple it is ! You can no longer think in windows mode as little to none of it applies to linux ! You have to "Break the windows" habit ! :P
 also have you checked out Ultimate Edition ! as an O/S I am affiliated with Ultimate Edition and it is and will always be my main O/S ! [http://ultimateedition.info/](http://ultimateedition.info/)
Ultimate Edition has all the bells and whistles and then some, You should stop by and give it look ! :D

---

### Post by D-Train on 2011-01-17
Hey there Johnny,
Thanks for the responses. I just stumbled across Ubuntu Tweak, it was there the whole time in Applications, just like you said. ](*,)
And yes, it does appear to work. I now can change my login background at will. Haven't figure out how to change the look of the box where I type in my password though. It's still kinda ugly, like my ex-wife. :lol:

I haven't tried ailiurus, WTF is that? :-k  Never mind, I just installed it. Look pretty cool! Thanks for the suggestion! 

and is sudu and gksudo are not commands, then what are they? 

As far as Windows goes, I'm not trying to think like a Windows person. When I said I work in a call center answering computer tech support calls all day, you probably thought I was talking about Windows support. Nope, I do Mac support. Which is one reason why I thought learning Linux would be a good thing. Since in Mac OS X you can go into Terminal and use the same commands to fix things as in Linux (since Mac OS X is a flavor of Linux after all)

I want a better understanding of all these chmod and sudo and fsck commands I sometimes use to help customers fix their Macs. 

I also just ordered a good book on Linux. This version was just released in October 2010.
[http://www.amazon.com/Beginning-Ubuntu-Linux-Emilio-Raggi/dp/1430230398](http://www.amazon.com/Beginning-Ubuntu-Linux-Emilio-Raggi/dp/1430230398)

I hope this will help me with most of the basics that I keep bugging you about. I'm pretty computer savvy, been making my living with computers since 1989. I was a CNE for several years (Novell Netware) 
but never an MSCE, Windows networking still confuses the sh*t outta me all these years later. This machine I'm typing this from in fact dual boots to Windows 7, and if I can figure out how to install WINE on this thing so I can still run the few Windows Apps that I cant run on Ubuntu or my Mac I'll never use Windows again. :-P

I'll check out Ultimate Edition, but with the 100's of flavors of Linux out there, to be honest, I'll probably stick with Ubuntu since the support community for it is the biggest and I can buy books on it. I don't see any books on Ultimate Edition out there. 

Thanks again!

---

### Post by JOHNNYG713 on 2011-01-17
No problems here my friend ! your not "Bug'n " Me one bit ! Luv the"Ex wife" Comment ! :D AS I have one of those also !
 And no no sudo and gksudo ARE commands! Not "sudo plymouth" or "gksudo pllymouth" !

 Ohh Your a MAC guy ! Cool !! I love mac ! Thats what brought me to LINUX ! :D

And No there Are no Books on Ultimate Edition (Yet) You see Ultimate Edition is a Unrecognized "spin" on Ubuntu ! it has everything Ubuntu has and much much more! Just stop by the forum and check it out ! Good luck to you my friend I hope I have been of some help ! :D

---

### Post by D-Train on 2011-01-17
Hi Johnny,
Yes you've most certainly been a lot of help. When my book arrives I'll dig in a little deeper. Right now it's just fun playing with it and trying to customize it to my liking. I've install KMyMoney and so far I like it and it's saved me from spending $50-$60 for Quicken or iBank. 

Now if I can find a good DVD Duping program I'll be set. I use 1ClickDVDCopy on my Windows 7 install and it works great. I've tried Mac The Ripper for my Mac but can't figure out how to shrink the files to under 4.5GB with it. Maybe that's all I'll need to install WINE for, so I can run 1ClickDVDCopy. 

Take care buddy and thanks again for your help! ;)

---

