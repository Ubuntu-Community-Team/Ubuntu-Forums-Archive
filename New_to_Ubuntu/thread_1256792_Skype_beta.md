---
title: "Skype beta"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by expatCM on 2009-09-03
I have installed the new beta on a 64 bit machine ... no problems.

I have repeated this on a 32 bit machine and a second copy appears by magic.  This is annoying but I cannot work out why it appears and how to fix it.

When the machine starts a second skype window opens with a red error message to the effect of ....  Another instance of skype appears to be running ....

To install I first ran sudo apt-get remove skype and then simply clicked the .deb.  What can go wrong with that .... 

Since then I have uninstalled (and ensured that the system tray icon was first closed) and reinstalled but also removing the .Skype file from the user home directory.

I have also checked the user / group and permissions of the new .Skype file (which are read / write / execute for the user only).

But always the second copy of skype appears.

There are other instances of this found through google but the solutions I have already tried (which seem to be around the .Skype file)

Has anyone managed to fix this?

---

### Post by expatCM on 2009-09-03
bump

---

### Post by expatCM on 2009-09-05
ok ... so bump ..

---

### Post by Paqman on 2009-09-05
Check in System > Admin > Startup applications, make sure you haven't got two references to Skype in there.

---

### Post by expatCM on 2009-09-05
In System / Preferences / Startup Applications there is no instance of skype at all.

If skype is started from the command line only one instance loads.

If I run

ps ax | grep skype

only one instance of skype is listed.

---

### Post by swoody on 2009-09-05
Try opening up your home folder. Hit 'ctrl + H' to show hidden files. Then navigate into the ".config" folder, and then into the "autostart" folder. If there is more than one 'Skype' file in there, delete one of them, and restart your computer. Let us know if this works out for you, or if there was only one Skype file in there.

---

### Post by expatCM on 2009-09-05
There is no command for skype in the autostart directory.  It is still launching though .....  I do not know how.

There are four user accounts on this machine, could that have any bearing on the matter?  Just looked under the user with admin rights but no skype.

---

### Post by swoody on 2009-09-05
Can you restart the computer again, and login to a different account? Does it auto-start only to your account, or does it do it for all accounts on that computer?

Also, have you tried going into the Skype settings on one of the two instances that pop up, and disabling 'auto-start'? Try that, and see if it disables them both, or just one of them.

If that don't work, try disabling the option in Skype's menu so it doesn't start by itself at all. Then go into System>Preferences>Startup Applications and create a new entry with the command 'skype' and see how that works out for you. You said that starting Skype from the command line only gave you one instance, so this should do the trick.

Let us know if this works out for you :)

---

### Post by swoody on 2009-09-05
Another idea. Browse to your /usr/share/autostart folder. Are there any instances of Skype in there?

---

### Post by expatCM on 2009-09-06
Thanks for all the suggestions .....  

Skype appears to autostart only on the one account.

I could not find any setting to disable autostart in skype.  I did find a setting to start skype minimized (to the system tray) and I did disable this.  Trouble is that this seems to have no effect at all ... still get two copies loading.  When it is enabled it works as described but only with the first copy to load.

Do you happen to know where the setting to start skype automatically with Ubuntu is to be found (within the skype program) ....  I cannot spot it?  I feel that it should be there but I seem to be overlooking it.

/usr/share/autostart does not have any instance of skype.

I get the idea that this is some setting somewhere in the user account but it really is not obvious.

---

### Post by swoody on 2009-09-06
Ah, right. I can't seem to find anything either in Skype. It must have been under Windows where it had the option to auto-start at login.

Try running:
```
sudo find /home/user/ -iname *skype*
```
Where "user" is the user name of the account you're having this issue with. Then post the output here :)

---

### Post by expatCM on 2009-09-06
I ran the command and this is what was returned.....  

```

/home/user/Desktop/skype-ubuntu-intrepid_2.1.0.47-1_i386.deb
/home/user/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#skype.com
/home/user/.macromedia/Flash_Player/#SharedObjects/SNFWXAB8/skype.com

```

---

### Post by swoody on 2009-09-07
Well, that all looks normal. Unfortunatly, I'm just about out of ideas on how this is auto-starting on your system. With the version of Skype you were using previously, did you have Skype installed from the Medibuntu repository, or was that also a .deb that you downloaded from the Skype website? Also, if you were running the version from the repos, was there a reason you stopped using it? Did you have any issues, or did you just want the latest version out there?

Ok, so first, try deleting .Skype again from your home folder. You can just go to your home folder, press ctrl+H to show hidden files, and then delete the .Skype folder. This will delete all your current settings for Skype, so you'll have to go through the options again, to setup Skype to how you have it now. Then restart your computer, and see if you still have the same issue.

If that doesn't work, you may want to try installing Skype from the Medibuntu repository. If you haven't had any issues or specific reasons for needing the newer version directly from Skype, this should work out fine for you. In Synaptic Package Manager, *completely* remove anything that is installed that has to do with Skype. If you already have the Medibuntu repository added, you can skip this next part, and go down to install Skype. Otherwise, go to a terminal and run:
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

Then you can run:
```
sudo apt-get update && sudo apt-get install skype
```

This will install the Skype version from the Medibuntu repository, and allow you to keep up with updates automatically. Once again, restart your computer, and see if you still have the same auto-start issues.

Now, *hopefully* this will help you out, but let us know how it works out for you :)

---

### Post by expatCM on 2009-09-08
Many thanks for your efforts here …..  I appreciate that ideas are finite in this case, especially since for some reason there do not appear to be others afflicted with this event.

Yes, skype was originally on this machine, installed from the repositories.  The upgrade is needed since the new version of skype, even though is in beta, resolves a large number of fundamental issues which we need to address.  These issues include for us better operation in a low bandwidth environment, ease of configuration for the hardware devices and now the practical opportunity to use a webcam.  Even with a duplicate copy there is no question of going back to the version in the repositories the two versions are radically different.

I just reinstalled having first stopped skype from running, running apt-get remove and then deleting the hidden files.  I even rebooted before running the deb file again to install fresh.  But, guess what … still two copies installed.  I even declined the second license agreement but that also had no effect.

So I guess this will be one to live with until say Ubuntu 9.10 / 10.04 when perhaps skype will be updated in the repositories …..

---

### Post by swoody on 2009-09-08
Ok, well I have sought out advice on this, and got another suggestion you may want to give a shot. It seems that some people are having an issue where their auto-start cache isn't clearing completely, and this should hopefully take care of that.

First, close all running apps - Firefox, Skype, terminals, etc. Go into System>Preferences>Startup Applications and under the 'Options' tab select 'Automatically Remember Running Applications when Logging Out'. Then, making sure that there are NO running apps, restart your computer. When your computer restarts it should clear your auto-start cache, and Skype shouldn't start at all. Then you can go back into that menu, uncheck the option to "remember your apps on logout", and you're good to go :)

---

### Post by expatCM on 2009-09-08
Well I am VERY please to be able to report back and tell you that your last suggestion was 100% successful.  Brilliant, well done and thank you for all your efforts :)

---

### Post by swoody on 2009-09-09
Ah, well like I said, I got that suggestion from someone else, so I can't really take the credit for it. It's great to hear that everything's up and running smoothly now, though :)

---

