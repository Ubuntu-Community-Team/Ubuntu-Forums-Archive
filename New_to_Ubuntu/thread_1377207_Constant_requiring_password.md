---
title: "Constant requiring password"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by ThePinkWitch on 2010-01-10
I'm getting really annoyed with constantly having to type in my password or having permission denied to do stuff on Ubuntu. I installed Awn and Screenlets to try and I downloaded themes and applets and unpacked them in my Downloads folder. I'm trying to drop them in their respective folders in my files folder but I don't have permission. How do I put the downloaded files into the right folders? How do I disable the constant asking for my password? I'm the only person who uses this computer so I don't need so much security. Thanks for any help :)

---

### Post by Temposs on 2010-01-10
it should only be asking you for your password when you do administrative stuff. It is the security model of Linux. The password doesn't only protect from other people messing with your computer, but also malicious software. So, it doesn't matter if you're the only one using your computer.

What is the folder that you're trying to drop the themes into? You generally should have permission for this sort of thing.

---

### Post by cenzorrll on 2010-01-10
you can use "gksu nautilus" to give yourself a root file manager (like explorer in windows)

from here you can copy and paste what you need in each folder.

as far as other passwords go, try looking up policykit, which is what ubuntu uses to manage passwords.  you can change how some programs ask for passwords, but not all.

---

### Post by ThePinkWitch on 2010-01-10
Thankyou guys for answering. I downloaded an awn theme and unpacked it as I said into downloads then clicked on Places Home then file system  and tried to drag the theme into the Themes folder of the Avant window manager  and it says permission denied.
I downloaded a screenlet and dont know how to install that either. Do I need Awn with Screenlets do you think or just one of them? What is Nautilus? If its like Win Explorer that might work better for me. Its been a bit of a nightmare getting things set up in Ubuntu the last couple of weeks but hey I'm getting there. Thanks to all the help from everyone :D

---

### Post by lindsay7 on 2010-01-10
Nautilus is what you are using when you click on "Places" (at the top menu bar) and look at files and folders,etc. The sudo gksu command that you were told about lets you manipulate these files and folders as the root file manager and you have all the permission that you need to do just about anything.  Be very careful when you use this as you can screw up just about anything too. It is best to use this as little as possible and when you do use it, do what you need and get out as fast as you can. A missed key or slip up can change a lot of things very quickly and you may not be able to fix them.

Be careful!!

---

### Post by Temposs on 2010-01-10
> **ThePinkWitch said:**
> Thankyou guys for answering. I downloaded an awn theme and unpacked it as I said into downloads then clicked on Places Home then file system  and tried to drag the theme into the Themes folder of the Avant window manager  and it says permission denied.
I downloaded a screenlet and dont know how to install that either. Do I need Awn with Screenlets do you think or just one of them? What is Nautilus? If its like Win Explorer that might work better for me. Its been a bit of a nightmare getting things set up in Ubuntu the last couple of weeks but hey I'm getting there. Thanks to all the help from everyone :D

You should not be dragging an AWN theme into the filesystem root folder! And I don't recommend for you to use gksu nautilus because you are a beginner and you would probably mess up your system at this point. 

That is not where an AWN theme goes...you need to look up where AWN themes are supposed to go and put it there. In fact, generally never put anything in the filesystem root folder. Every folder you use should basically be within /home/yourusername. That is, you go to Places->Home Folder. Everything in there is accessible to you, and you should only drag stuff into there or subfolders within there.

---

### Post by Temposs on 2010-01-10
> **ThePinkWitch said:**
> Thankyou guys for answering. I downloaded an awn theme and unpacked it as I said into downloads then clicked on Places Home then file system  and tried to drag the theme into the Themes folder of the Avant window manager  and it says permission denied.
I downloaded a screenlet and dont know how to install that either. Do I need Awn with Screenlets do you think or just one of them? What is Nautilus? If its like Win Explorer that might work better for me. Its been a bit of a nightmare getting things set up in Ubuntu the last couple of weeks but hey I'm getting there. Thanks to all the help from everyone :D

Nautilus is the program that comes up when you click on something in the Places menu. It is the equivalent of Windows Explorer in Ubuntu. Do not try to use gksu nautilus though. It is too dangerous for a beginner. 

Almost every file that you want to put on your computer you should generally put into your Home Folder, which you can get to from the Places menu.

Your files for AWN that you downloaded are going to go into the awn configuration directory, which is a hidden folder. To see your hidden folders, go to Places->Home Folder and press Ctrl-H. Then you should see a number of files and folders that start with a dot. Look for a folder called .awn, or something similar. You'll find the appropriate folder to put your theme and screenlet files in there. After you're done, go back to your home folder and press Ctrl-H again to hide your hidden files again, so they don't bother you.

---

### Post by ThePinkWitch on 2010-01-11
Thankyou very much :)

---

### Post by ThePinkWitch on 2010-01-12
I still don't know how to install downloaded applets which are .tar files..I'm getting really frustrated trying to find this out. For a couple of days I have looked for this info. I downloaded tar files to my downloads folder. How do I install them?????? I tried right clicking and open with and it doesn't work. Getting very grumpy :( help please. I am hating tar and b whatever files.

---

### Post by ThePinkWitch on 2010-01-12
> **Temposs said:**
> Nautilus is the program that comes up when you click on something in the Places menu. It is the equivalent of Windows Explorer in Ubuntu. Do not try to use gksu nautilus though. It is too dangerous for a beginner. 

Almost every file that you want to put on your computer you should generally put into your Home Folder, which you can get to from the Places menu.

Your files for AWN that you downloaded are going to go into the awn configuration directory, which is a hidden folder. To see your hidden folders, go to Places->Home Folder and press Ctrl-H. Then you should see a number of files and folders that start with a dot. Look for a folder called .awn, or something similar. You'll find the appropriate folder to put your theme and screenlet files in there. After you're done, go back to your home folder and press Ctrl-H again to hide your hidden files again, so they don't bother you.

I did this but although I found .files.....no AWN :(

---

### Post by SirBismuth on 2010-01-12
> **ThePinkWitch said:**
> I still don't know how to install downloaded applets which are .tar files..I'm getting really frustrated trying to find this out. For a couple of days I have looked for this info. I downloaded tar files to my downloads folder. How do I install them?????? I tried right clicking and open with and it doesn't work. Getting very grumpy :( help please. I am hating tar and b whatever files.

Ok, thought I could help, as I have done this before, but I am not at home, and therefore don't have access to the file where I have saved all the solutions that I have found to various things in Ubuntu.

If I remember correctly, I found the solution to installing tar files on this forum (try using "install .tar.gz files" as a search term on this forum), otherwise try google.  I extracted them from the command line, but can't remember the exact command, so am not even going to try to guess, hopefully someone else can help you here.

HTH

---

### Post by wannabegeek on 2010-01-12
from one newbie to another, stick to installing software that is in the
repositories...I have been able to find everything I need there,and on this forum I find the code for the keys, the sources.list code, all that...

When you are thinking of getting some application, search here or post to find out what people use and what's in the repo.

It makes life with Ubuntu easy, because Linux really is hard, its for computer science people.

good luck !

wbg

---

### Post by ThePinkWitch on 2010-01-12
Thanks :) tried searching the forums and even psychocats and they recommend asking in the forums. I'm just going to delete the tar files and give up. Cheers :)

---

### Post by ThePinkWitch on 2010-01-12
I'm hearing ya :) Like I said..I'm deleting the tar files and not bothering with them. I just want an app that will tell me what speeds I'm getting from my internet and what I've downloaded. :)

---

### Post by mikewhatever on 2010-01-12
> **ThePinkWitch said:**
> I'm hearing ya :) Like I said..I'm deleting the tar files and not bothering with them. I just want an app that will tell me what speeds I'm getting from my internet and what I've downloaded. :)

[http://speedtest.net](http://speedtest.net)

As for the app to tell you what you've downloaded, I am confused. Don't you know what you download?

Oh, by the way, installing screenlets isn't rocket science either.
[http://www.google.com/search?btnG=1&pws=0&q=install+screenlets](http://www.google.com/search?btnG=1&pws=0&q=install+screenlets)

---

### Post by egalvan on 2010-01-12
> **ThePinkWitch said:**
> ...what I've downloaded. :)

If you are referring to files downloaded in Firefox,

Menu -> Tools -> Downloads

will open the download window...
on my FF3.0.x install, this shows all files downloaded.
You can remove files from the list, if you want to trim it down...
mine goes back to October-09...

As for files downloaded with Synaptic, or apt-get, there are files containing this info, but I don't remember them at the moment...
I'm sure some other guru will come up with the info...

---

### Post by HiImTye on 2010-01-12
if you want something similar to awn try cairo-dock
```
sudo apt-get install cairo-dock
```
there's also a multitude of others, but cairo-dock grabs all the themes and such for you, so there's no hassle

I recommend you bookmark this site, to help you:
[How to install ANYTHING in Ubuntu!]("http://amitech.50webs.com/installing/index.php.html")
if possible, always install from .deb files so you can easily remove them later
to see all the programs you can/have install(ed) use synaptic
```
Administration>Synaptic Package Manager
```
just remember that _only_ .deb files will show up here. anything else you're kind of on your own

---

### Post by ThePinkWitch on 2010-01-12
> **mikewhatever said:**
> [http://speedtest.net](http://speedtest.net)

As for the app to tell you what you've downloaded, I am confused. Don't you know what you download?

Oh, by the way, installing screenlets isn't rocket science either.
[http://www.google.com/search?btnG=1&pws=0&q=install+screenlets](http://www.google.com/search?btnG=1&pws=0&q=install+screenlets)

I want a Net Monitor with my upload and downloads So I can keep an eye on them because my IP gives me a 12G download limit. I like to know whats going out also as it gives me a hint If I have anything intruding on my machine. I also wanted to check what speed I'm getting because my internet has been painfully slow. And no screenlets isn't rocket science but working out how to use Tar files is for a beginner. I'm good with Windoze but am a total newb on Ubuntu.

---

### Post by ThePinkWitch on 2010-01-12
> **HiImTye said:**
> if you want something similar to awn try cairo-dock
```
sudo apt-get install cairo-dock
```
there's also a multitude of others, but cairo-dock grabs all the themes and such for you, so there's no hassle

I recommend you bookmark this site, to help you:
[How to install ANYTHING in Ubuntu!]("http://amitech.50webs.com/installing/index.php.html")
if possible, always install from .deb files so you can easily remove them later
to see all the programs you can/have install(ed) use synaptic
```
Administration>Synaptic Package Manager
```
just remember that _only_ .deb files will show up here. anything else you're kind of on your own

Thankyou :) That URL was actually very helpful

---

### Post by mikewhatever on 2010-01-13
> **ThePinkWitch said:**
> I want a Net Monitor with my upload and downloads So I can keep an eye on them because my IP gives me a 12G download limit. I like to know whats going out also as it gives me a hint If I have anything intruding on my machine. I also wanted to check what speed I'm getting because my internet has been painfully slow. And no screenlets isn't rocket science but working out how to use Tar files is for a beginner. I'm good with Windoze but am a total newb on Ubuntu.

Well, what you are experiences is a learning curve, which is only natural when learning something new. I suspect, judging by the frequency of the fact being mentioned, that many people think their know how with Windows somehow applies universally, that's not the case. Using linux is similar to learning a new language, with different words, meanings and concepts.

Anyway, you want to monitor your bandwidth usage in Ubuntu. Check out the link below.
[http://lmgtfy.com/?q=ubuntu+bandwidth+monitor](http://lmgtfy.com/?q=ubuntu+bandwidth+monitor)

---

### Post by audiomick on 2010-01-13
Hallo PinkWitch.

---

### Post by 3rdalbum on 2010-01-13
> **ThePinkWitch said:**
> I want a Net Monitor with my upload and downloads So I can keep an eye on them because my IP gives me a 12G download limit. I like to know whats going out also as it gives me a hint If I have anything intruding on my machine. I also wanted to check what speed I'm getting because my internet has been painfully slow.

I basically can't check on quota usage using a program on my computer, because I have several computers and other devices on my network and their use can't be counted at my end. My ISP, however, has a section on its website called Account Toolbox, where I can see how much download and upload quota has been used for that month.

I also keep a System Monitor applet on my panel so I can see whether any programs are thrashing my CPU, filling my RAM or sending data to the network (and whether this data is 'local' and stays on the network, or if it's remote and goes to the internet). It's handy.

---

### Post by doublewitt on 2010-01-13
I was wondering...

A couple of days ago, I stumbled on this software called UBUNTU TWEAK. I'm still relatively new with Ubuntu and so I wonder how the following setting can be of help in regards to the initial question about "root" priveleges. Inside Ubuntu Tweak there is an option, NAUTILUS SETTINGS:NAUTILUS WITH ROOT PRIVELEGES. Would this help to resolve the issue? I kinda like this software and find it to be rather useful thus far. 

Here is the website:
[http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

I guess it's best to avoid playing with "root" priveleges unless you really know what you are doing. Any commentaries about this setting in Ubuntu Tweak?

---

### Post by audiomick on 2010-01-14
> **doublewitt said:**
> I was wondering...
Inside Ubuntu Tweak there is an option, NAUTILUS SETTINGS:NAUTILUS WITH ROOT PRIVELEGES. Would this help to resolve the issue? 

Only as far as file manipulation operations go, but not for installing things or changing system settings.

The argunment for not choosing this setting is that when you are using Nautilus as root, there is nothing stopping you erasing or editing system files. If you are _**always**_ absolutely aware of what you are doing and never do anything absentmindedly, this might be ok. Personally, I like the reminder via the password request that I am messing around with things that I need to think carefully about.

> I kinda like this software and find it to be rather useful thus far. 

Yes, I have heard good reports about it. It is on my list of things to look at.

> I guess it's best to avoid playing with "root" priveleges unless you really know what you are doing.
Yes indeed. That is why Ubuntu is set up the way it is, with root disabled and the password request for operations requiring root privileges.

---

### Post by MoarningSun on 2010-01-14
I don't use AWN myself, but according to the internets applying a theme to AWN shouldn't be too difficult. The option should be somewhere in the AWN-manager: 
> How do I access the preferences for AWN?

Right-click either end of the bar and choose "Preferences", check the "Settings" or "Preferences" menu in your desktop's application menu for "Awn manager", or run the following at the command prompt:
```
awn-manager &
```[http://wiki.awn-project.org/FAQ#How_do_I_access_the_preferences_for_AWN.3F](http://wiki.awn-project.org/FAQ#How_do_I_access_the_preferences_for_AWN.3F)

---

### Post by ThePinkWitch on 2010-01-15
> **audiomick said:**
> hallo pinkwitch.

hello :)

---

### Post by ThePinkWitch on 2010-01-15
> **MoarningSun said:**
> I don't use AWN myself, but according to the internets applying a theme to AWN shouldn't be too difficult. The option should be somewhere in the AWN-manager: 
[http://wiki.awn-project.org/FAQ#How_do_I_access_the_preferences_for_AWN.3F](http://wiki.awn-project.org/FAQ#How_do_I_access_the_preferences_for_AWN.3F)

Thankyou :)

---

### Post by ThePinkWitch on 2010-01-15
> **3rdalbum said:**
> I basically can't check on quota usage using a program on my computer, because I have several computers and other devices on my network and their use can't be counted at my end. My ISP, however, has a section on its website called Account Toolbox, where I can see how much download and upload quota has been used for that month.

I also keep a System Monitor applet on my panel so I can see whether any programs are thrashing my CPU, filling my RAM or sending data to the network (and whether this data is 'local' and stays on the network, or if it's remote and goes to the internet). It's handy.

Thanks I found an info panel for screenlets so I'm happy now. It has all the system info I want :)

---

