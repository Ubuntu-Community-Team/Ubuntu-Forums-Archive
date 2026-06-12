---
title: "File installation help needed"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by dkolars on 2010-04-02
This is driving me nuts...  Been using Ubuntu since last Oct.   MOST things are not a problem.. I'm a retired IT guy (Win NT4.0), but retired in '01 so lots has changed...

I'm on Facebook, and want to upload some pictures... well, it's been a while since I did that, so I get the message:

"The latest version of Facebook Plug-In was not found. Please make sure you have successfully installed it.Sorry, something went wrong. Please try downloading our standalone installer.Sorry, something went wrong while trying to self-update. Please download and run the installer below to update the Facebook Plug-In.You need to download and install the latest version of the Facebook Plug-In to continue.Windows 2000/XP/VistaMac OS X 10.4 or higherLinux x86
[Download Facebook Plug-In]("http://www.facebook.com/fbplugin/linux-x86/install/FacebookPlugIn-1.0.3.tar.gz")
Once you have installed the Plug-In, click "Done Installing" to continue."


I download the plug-in, and then File Roller wants me to Open or Extract the file:


FacebookPlugIn-1.0.3.tar.gz


Where the **** do you extract this to?  If it's an update, isn't there an older file somewhere?  Why can't Linux find the file that it's supposed to be updating and install into that directory?


So, I end up saving it in my "downloads" directory under my user name...  in hopes that someday I'll know where to put things...  I have a few files there, waiting for direction!



This is my main complaint about Linux...  With Windoze, one could manage where things went, and control updates/settings/etc. much easier...


I've perused several help sites, but this subject doesn't seem to come up enough to merit much discussion...


thanks in advance!!  dk

---

### Post by warfacegod on 2010-04-02
Open Synaptic and search for facebook. Its possible there is a package there that will do what you need it to.

---

### Post by 2hot6ft2 on 2010-04-02
Go into your Downloads folder and extract it like you said it wanted you to do.
Change to that folder that it creates and right click on the FacebookPlugIn_Install.sh file.
Select Properties.
Check the box for Allow executing file as program.
Close the properties box and double click on the file and select Run
Restart firefox if it was open.
That should be it.
Enjoy.

It's a .sh file, if facebook wanted it to be user friendly then they would have made it a .deb like they make .exe files for windows. So it's facebooks fault they made it that way.
> **dkolars said:**
> 
Where the **** do you extract this to?  If it's an update, isn't there an older file somewhere?  Why can't Linux find the file that it's supposed to be updating and install into that directory?

It will automatically extract it to the folder it's in. If firefox asks (and you choose extract) then it will extract it in your Home Folder.

P.S. There are about 10 firefox plugins for facebook. In firefox just click on Tools > Add-ons > Get Add-ons and in the search type in facebook and hit Enter then scroll down and click on the Show all results to see them all.

---

### Post by 3rdalbum on 2010-04-02
You don't need a plugin to upload photos to Facebook. The web interface works fine.

---

