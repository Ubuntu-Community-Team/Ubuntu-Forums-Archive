---
title: "How do I COMPLETELY remova all traces of Broken Wine instalation ??"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by scrypt on 2010-08-03
Hello

I have made a complete mess of My Wine Installation on Ubuntu 10.04 Lucid.

I cannot Run Runes of Magic. So I decided to try to COMPLETELY remove Wine and then reinstall it again once I fully installed Wine.

The problem is That I cannot seem to fully uninstal Wine no matter what I try

I have uninstalled everything wine related from Synaptics.
and also tried these commands:

rm -rf $HOME/.wine
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm

But I cannot fully uninstall Runes of Magic or Wine

I know wine is NOT fully removed because if I run this command 

sudo aptitude install -f

I get this message ::

mark@mark-laptop:~$ sudo aptitude install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
The following NEW packages will be installed:
  wine wine1.2 wine1.2-gecko winetricks 
0 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/18.5MB of archives. After unpacking 95.6MB will be used.
Do you want to continue? [Y/n/?] 


Can somebody help me to COMPLETELY remove wine and runes of magic from Ubuntu. So I can try to install Wine and runes of magic cleanly again

---

### Post by justin43384 on 2010-08-03
I have the same problem here...

---

### Post by scrypt on 2010-08-03
I also removed my .Wine directory

and ran these commands with No joy either 

 sudo apt-get remove wine
sudo apt-get purge wine
rm -rf ~/.wine

Still not removing Wine fully

Help needed please

---

### Post by sydbat on 2010-08-03
This thread might help - [http://ubuntuforums.org/showthread.php?t=635356](http://ubuntuforums.org/showthread.php?t=635356)

This one might be better (post #2) - [http://ubuntuforums.org/showthread.php?t=1532789](http://ubuntuforums.org/showthread.php?t=1532789)

And there's this one - [http://ubuntuforums.org/showthread.php?t=1081883](http://ubuntuforums.org/showthread.php?t=1081883)

---

### Post by giddyup306 on 2010-08-03
I feel your pain.  I've had a couple programs that just don't want to delete regardless of what I did.  I don't know about Wine specifically, but one thing you can try is if you have Ubuntu Tweak, there is an option to delete obsolete packages.  For some reason Ubuntu likes to leave garbage packages when you "delete" a program.

---

### Post by scrypt on 2010-08-03
Thanks for the replies sydbat and giddyup

Sydbat I have actually tried all the suggestions on the web sites you suggested and still no luck

Giddyup306... Is Ubuntu Tweak A Package  that can be instaled through synaptics ??

---

### Post by k3lt01 on 2010-08-03
> **giddyup306 said:**
> I feel your pain.  I've had a couple programs that just don't want to delete regardless of what I did.  I don't know about Wine specifically, but one thing you can try is if you have Ubuntu Tweak, there is an option to delete obsolete packages.  For some reason Ubuntu likes to leave garbage packages when you "delete" a program.Not entirely accurate. You can clean orphaned packages with Synaptic and that is the only other thing UT does. Ubuntu doesn't do it by default because you can break your system if you don't understand what you are doing.

[Check this thread]("http://ubuntuforums.org/showthread.php?t=140920") out for how to clean your system without having to install yet another program that isn't even in the repositories.

As for deleting WINE, you may need to open Nautilus as root
```
 gksudo nautilus
```
navigate your way and find .wine and the other folders etc and delete them manually. Then make sure you empty your rubbish bin.

---

### Post by scrypt on 2010-08-04
Thank-you for your reply.

I am relative beginner when it comes to Ubuntu. So I will try to quickly explain my problem.
I Installed runes of Magic Using Wine.
Runes of Magic will NOT start at all. I assume I have corrupted my Wine somehow.
I Have removed Wine from synaptics. I also removed all Residual config files in Synaptics.
I have also deleted my .Wine directory from my Home folder.

 want to completely remove all traces of Wine and Runes of Magic so I can cleanly install Both from fresh again following different methods. To try to get Runes of magic working

I Know there are still traces of Wine and Runes of magic left behind because when I run this command

sudo aptitude install -f

i get this output:

Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initialising package states... Done
The following NEW packages will be installed:
  libmpg123-0 wine1.2 wine1.2-gecko winetricks
0 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/18.6MB of archives. After unpacking 95.9MB will be used.
Do you want to continue? [Y/n/?]

As I say im newcomer to Ubuntu. I would Like to know how to remove all traces of Wine and Runes of Magic to make clean instalation of the two

---

### Post by bumanie on 2010-08-04
Go [here]("http://wiki.winehq.org/FAQ") and follow all the commands one by one which are under point 5.1

---

### Post by scrypt on 2010-08-04
Hello Bumanie I have tried all the options from the wine site you suggested and i still have no luck.

There is something fundamental I am not understanding here. I am a relative newcomer to Ubuntu so I am still learning.

I am relative beginner when it comes to Ubuntu. So I will try to quickly explain my problem.
I Installed runes of Magic Using Wine.
Runes of Magic will NOT start at all. I assume I have corrupted my Wine somehow.
I Have removed Wine from synaptics. I also removed all Residual config files in Synaptics.
I have also deleted my .Wine directory from my Home folder.

 want to completely remove all traces of Wine and Runes of Magic so I can cleanly install Both from fresh again following different methods. To try to get Runes of magic working

I Know there are still traces of Wine and Runes of magic left behind because when I run this command

sudo aptitude install -f

i get this output:

Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initialising package states... Done
The following NEW packages will be installed:
  libmpg123-0 wine1.2 wine1.2-gecko winetricks
0 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/18.6MB of archives. After unpacking 95.9MB will be used.
Do you want to continue? [Y/n/?]

As I say im newcomer to Ubuntu. I would Like to know how to remove all traces of Wine and Runes of Magic to make clean instalation of the two

can somebody help me understand where im going wrong of how i can fix this

---

### Post by scrypt on 2010-08-04
Is it becuase I still have Runes of Magic Instalation File Named :
/home/home/Downloads/FOGDownloader-RoM_3_0_1_2153.exe

In my Downloads Folder that, Even though I have uninstalled all traces of Wine including the .wine directory. that When I run this command:

sudo aptitude install -f

I get this output :

laptop:~$ sudo aptitude install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
The following NEW packages will be installed:
  wine1.2 wine1.2-gecko winetricks 
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/18.4MB of archives. After unpacking 95.5MB will be used.
Do you want to continue? [Y/n/?] 

Is this what is causing me to think that Wine and Runes Of magic are NOT fully uninstalled ??

---

### Post by bumanie on 2010-08-04
Did you try those commands with sudo in front? Long time since I did them, but admin rights are probably needed. Try the commands with sudo in front of each one - I have removed wine completely with those commands in the past.

---

### Post by k3lt01 on 2010-08-04
It is probably trying to install a new version of Wine etc because you probably have it marked in Synaptic as still installed. It may be an idea to double check Synaptic to make sure you removed it with "Complete Removal".

---

### Post by scrypt on 2010-08-05
Thank-you all for your help informative replies.

My issue is now fixed using the link k3lt01 Posted.

found here :

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

Thanks again k3lt01 you helped fix my issue

---

