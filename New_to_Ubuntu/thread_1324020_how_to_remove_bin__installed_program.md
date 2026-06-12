---
title: "how to remove bin  installed program"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by urdrwho on 2009-11-12
Ok, I am "Trying" to use Ubuntu at work and didn't think I would need to become a command guru to use it.  

Yesterday I installed Adobe Reader from a bin file but now I want to remove it.  I have tried several uninstall command lines but none seem to want to work.

/home/MY NAME/Desktop/adobe/Adobe/Reader9/Reader

The above is the folder hierarchy.

I must now get back to working and hopefully someone can give me the command line that will remove the program.

---

### Post by wojox on 2009-11-12
Most .bin files have some type of --uninstall command line option.

---

### Post by urdrwho on 2009-11-12
> **wojox said:**
> Most .bin files have some type of --uninstall command line option.

Thanks for your response.

In the Adobe folder there is a file titled uninstall, it is a shell script (application/x-shellscript).

They also have a reader file in help that says:

To uninstall Adobe Reader 9.1 using the command line

1. Open a terminal window.

2.(a) In case of RPM installer:

Run the following command as an administrator or root:
rpm -e AdobeReader_enu

2.(b) In case of DEB installer:

Run the following command as an administrator or root:
dpkg -r adobereader-enu
2.(a) In case of PKG installer:

Run the following command as an administrator or root:
pkgrm ADBEreadr-enu

2.(d) In case of tarball or bin installer:

Run the following command:
<reader_install_dir>/bin/UNINSTALL 


At first I ran the RPM, that didn't work and now I have RPM installed.  There was a line about using Alien instead.  Alien?

Then I tried 2(d).  Probably / possibly I am not writing the command correctly.  I don't understand which parts of this line are needed <reader_install_dir>/bin/UNINSTALL 

Do I need the under line marks, the brackets, must I write it to point to the Adobe Reader 9 configuration that reside on the desktop or the main adobe folder?

Sure 20 years ago I knew my DOS commands like the back of my hand but haven't use commands in a long - long - time.  I just sit here shaking my head thinking, "can you imagine someone that has never ever used command lines trying to use this OS."  It would be a joke.  To me, it is the Achilles heal of a Nix type open OS.  

Now what command line must I use?

---

### Post by wheatpenny on 2009-11-12
Try dragging the uninstall file to the terminaland it will enter the correct path for it.

---

### Post by Paddy Landau on 2009-11-12
Take note of the following points:


[LIST]
[*]In Ubuntu, a thing called a Package Manager handles all your installs and uninstalls. You should *never* have to install from a [FONT=Courier New].bin[/FONT] file.
[*]To install Adobe, you go to your package manager and ask it to install. You do *not* need to download the file from the Internet; your package manager will do that for you.
[*]To install Adobe, you would go to menu System > Administration > Synaptic Package Manager. Scroll down to *acroread* (or use the search bar to find it), right-click and select *Mark for Installation*. Do the same with *adobe-flashplugin*. Press *Apply*. It's really that easy. (Don't do it yet, though. First you need to uninstall your present package.)
[*]In rare cases where the Package Manager doesn't know about a package, you download a [FONT=Courier New].deb[/FONT] file from the Internet, and then let the Package Manager install it for you.
[/LIST]

Now, before you try to install Adobe, let's see if you can uninstall your [FONT=Courier New].bin[/FONT] installation:


[LIST=1]
[*]Go to your Package Manager: System > Administration > Synaptic Package Manager.
[*]Use the search bar to find all instances of adobe.
[*]Look to find if Adobe is installed (it will have a green box).
[*]If found, right-click and select *Mark for Complete Removal* and select *Apply*.
[/LIST]

Let us know whether that helps; if not, we can help you manually uninstall. (It's nowhere near as complicated as on Windows.)

---

### Post by urdrwho on 2009-11-12
Well this is for sure that last time I do a bin install.  When I went to 
Adobe download it only gave:

Download the latest version of Adobe Reader
Adobe Reader
Adobe Reader 9.2
Linux (.bin), English
Different language or operating system?
43.3 MB

So I had to install from the bin and by doing so there is nothing in the SPM.  Maybe there could have been other steps to use to get it in the manager but I didn't know how.

So maybe I can learn something.  How could I install the bin file using the SPM if it isn't already in the Manager?  I did first search the SMP but Adobe reader was not in it.

And then....back to my try to uninstall Adobe 9. 


> **Paddy Landau said:**
> Take note of the following points:


[LIST]
[*]In Ubuntu, a thing called a Package Manager handles all your installs and uninstalls. You should *never* have to install from a [FONT=Courier New].bin[/FONT] file.
[*]To install Adobe, you go to your package manager and ask it to install. You do *not* need to download the file from the Internet; your package manager will do that for you.
[*]To install Adobe, you would go to menu System > Administration > Synaptic Package Manager. Scroll down to *acroread* (or use the search bar to find it), right-click and select *Mark for Installation*. Do the same with *adobe-flashplugin*. Press *Apply*. It's really that easy. (Don't do it yet, though. First you need to uninstall your present package.)
[*]In rare cases where the Package Manager doesn't know about a package, you download a [FONT=Courier New].deb[/FONT] file from the Internet, and then let the Package Manager install it for you.
[/LIST]

Now, before you try to install Adobe, let's see if you can uninstall your [FONT=Courier New].bin[/FONT] installation:


[LIST=1]
[*]Go to your Package Manager: System > Administration > Synaptic Package Manager.
[*]Use the search bar to find all instances of adobe.
[*]Look to find if Adobe is installed (it will have a green box).
[*]If found, right-click and select *Mark for Complete Removal* and select *Apply*.
[/LIST]

Let us know whether that helps; if not, we can help you manually uninstall. (It's nowhere near as complicated as on Windows.)

---

### Post by urdrwho on 2009-11-12
> **wheatpenny said:**
> Try dragging the uninstall file to the terminaland it will enter the correct path for it.

I did and it gave me the full path to the uninstall file.  Now what do I do with it.  It is not an executable file.  

This is the path '/home/myname/Desktop/adobe/Adobe/Reader9/bin/UNINSTALL' 

myname@ubuntu:~$ cd Desktop
myname@ubuntu:~/Desktop$ cd adobe
myname@ubuntu:~/Desktop/adobe$ cd Adobe
myname@ubuntu:~/Desktop/adobe/Adobe$ cd Reader9
myname@ubuntu:~/Desktop/adobe/Adobe/Reader9$ cd bin
myname@ubuntu:~/Desktop/adobe/Adobe/Reader9/bin$ chmod +x UNINSTALL
myname@ubuntu:~/Desktop/adobe/Adobe/Reader9/bin$ ./UNINSTALL

mynamee@ubuntu:~/Desktop/adobe/Adobe/Reader9/bin$

Nothing happens when I run the above.

---

### Post by Paddy Landau on 2009-11-12
OK, first things first. We'll deal with Synaptic Package Manager later. Synaptic does have Adobe; if you can't see it, it's just a matter of adding a repository. We'll do that later.

First, let's uninstall your current version of Adobe.

It's real easy; you just delete all the files in question. (There's no 'registry' as there is in Windows.)

Going by what you've already told us, delete the folder adobe that is in your Desktop. You can do that from the terminal, from the Desktop itself, or from Nautilus (Places > Desktop), whichever you prefer.

If you hit errors doing this, tell us.

In a few minutes, I'll create another post to help you install Adobe.

---

### Post by urdrwho on 2009-11-12
Gotta stop for a while.  I am really PO'd at such a system for adding/removing programs.  Get a GD GUI to do the install - remove and maybe more people will start using an alternative OS.  



> **urdrwho said:**
> I did and it gave me the full path to the uninstall file.  Now what do I do with it.  It is not an executable file.  

This is the path '/home/myname/Desktop/adobe/Adobe/Reader9/bin/UNINSTALL' 

myname@ubuntu:~$ cd Desktop
myname@ubuntu:~/Desktop$ cd adobe
myname@ubuntu:~/Desktop/adobe$ cd Adobe
myname@ubuntu:~/Desktop/adobe/Adobe$ cd Reader9
myname@ubuntu:~/Desktop/adobe/Adobe/Reader9$ cd bin
myname@ubuntu:~/Desktop/adobe/Adobe/Reader9/bin$ chmod +x UNINSTALL
myname@ubuntu:~/Desktop/adobe/Adobe/Reader9/bin$ ./UNINSTALL

mynamee@ubuntu:~/Desktop/adobe/Adobe/Reader9/bin$

Nothing happens when I run the above.

---

### Post by Paddy Landau on 2009-11-12
To install Adobe, you need to go to System > Administration > Synaptic Package Manager.

This first step is to make sure that you have the repositories set:


[LIST]
[*]Select Settings > Repositories > Ubuntu Software.
[*]Check the first four boxes (Canonical supported, Community maintained, Proprietary devices, and Software restricted) if not already selected. Close.
[*]Press *Reload* (this reloads any changes you might have made in the previous step).
[*] Press *Mark All Upgrades* (this marks any packages that need to be upgraded, similar to Windows Update).
[*]Press *Apply* if it's not greyed out.
[/LIST]

The next step is how you install Adobe, and how you'd normally install a package on Ubuntu:


[LIST]
[*]Find *acroread* in the main window. (If you don't see it, then tell us.) Right-click and select *Mark for Installation*.
[*]Do the same with *adobe-flashplugin*.
[*]Press *Apply*.
[*]Close Synaptic.
[/LIST]

Now you should find Adobe under your menu: Applications > Office > Adobe Reader 9.

---

### Post by Paddy Landau on 2009-11-12
> **urdrwho said:**
> Gotta stop for a while.  I am really PO'd at such a system for adding/removing programs.  Get a GD GUI to do the install - remove and maybe more people will start using an alternative OS.
There **is** a GUI to do it. Synaptic Package Manager. You're having problems because you did it the wrong way and we need you to undo it.

Follow my **easy** instructions in [post 8]("http://ubuntuforums.org/showthread.php?p=8301895#post8301895") and [post 10]("http://ubuntuforums.org/showthread.php?p=8301971#post8301971").

---

### Post by oldos2er on 2009-11-12
> **urdrwho said:**
> Gotta stop for a while.  I am really PO'd at such a system for adding/removing programs.  Get a GD GUI to do the install - remove and maybe more people will start using an alternative OS.

[https://help.ubuntu.com/9.10/add-applications/C/index.html](https://help.ubuntu.com/9.10/add-applications/C/index.html)

[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

---

### Post by mrboojive on 2009-11-12
> **urdrwho said:**
> Gotta stop for a while.  I am really PO'd at such a system for adding/removing programs.  Get a GD GUI to do the install - remove and maybe more people will start using an alternative OS.

I totally understand your frustration. Trying to uninstall something this way is a pain. But please don't get angry at Ubuntu, get angry at Adobe for suggesting that you download a ".bin" file! Once you start using the package manager, I suspect you'll come to think that installing and uninstalling programs on Linux is way easier than Windows or Mac.

> **Paddy Landau said:**
> To install Adobe, you need to go to System > Administration > Synaptic Package Manager.

This first step is to make sure that you have the repositories set:


[LIST]
[*]Select Settings > Repositories > Ubuntu Software.
[*]Check the first four boxes (Canonical supported, Community maintained, Proprietary devices, and Software restricted) if not already selected. Close.
[*]Press *Reload* (this reloads any changes you might have made in the previous step).
[*] Press *Mark All Upgrades* (this marks any packages that need to be upgraded, similar to Windows Update).
[*]Press *Apply* if it's not greyed out.
[/LIST]

The acroread package is actually in Canonical's Partner repository, so we need to add one step to these instructions. After checking the other boxes in the Software Sources application, you will also need to click the tab at the top for "Other Software," then check the line that has "http://archive.canoncial.com/ubuntu ... partner".

---

### Post by Paddy Landau on 2009-11-12
> **mrboojive said:**
> The acroread package is actually in Canonical's Partner repository...
Thanks!

---

### Post by urdrwho on 2009-11-13
I preformed all the above steps.  So to remove a piece of software is just a matter of deleting?  Kind of like the old DOS days.

I don't have acoread.  The first thing I did before installing the bin was checked the SPM.


> **Paddy Landau said:**
> To install Adobe, you need to go to System > Administration > Synaptic Package Manager.

This first step is to make sure that you have the repositories set:


[LIST]
[*]Select Settings > Repositories > Ubuntu Software.
[*]Check the first four boxes (Canonical supported, Community maintained, Proprietary devices, and Software restricted) if not already selected. Close.
[*]Press *Reload* (this reloads any changes you might have made in the previous step).
[*] Press *Mark All Upgrades* (this marks any packages that need to be upgraded, similar to Windows Update).
[*]Press *Apply* if it's not greyed out.
[/LIST]

The next step is how you install Adobe, and how you'd normally install a package on Ubuntu:


[LIST]
[*]Find *acroread* in the main window. (If you don't see it, then tell us.) Right-click and select *Mark for Installation*.
[*]Do the same with *adobe-flashplugin*.
[*]Press *Apply*.
[*]Close Synaptic.
[/LIST]

Now you should find Adobe under your menu: Applications > Office > Adobe Reader 9.

---

### Post by urdrwho on 2009-11-13
Thank you all for your help.  Acoread is now in my repository and I had to click on the partners tab in other software to get it.

If I knew that all that was needed was to delete, I would not have lost a few hairs over the frustration.

Thanks to all!

---

### Post by urdrwho on 2009-11-13
I hit delete and deleted the folders.  There is a remaining instance of Adobe.  When I click on a PDF, a pop-up window still has the Adobe reference.  I must now manually choose view with and choose the Ubuntu installed viewer.

If this were Windows I would know how to make a certain extension open with a certain application.  

How do I make a certain app always open a certain extension
How to I remove the instance of Adobe reader in the pop-up

---

### Post by Paddy Landau on 2009-11-13
> **urdrwho said:**
> So to remove a piece of software is just a matter of deleting?
No, that was just to undo the [FONT=Courier New].bin[/FONT] thing. In future, use Synaptic Package Manager to uninstall. It handles all dependencies, menu entries, and so forth for you.

> **urdrwho said:**
> How do I make a certain app always open a certain extension
How to I remove the instance of Adobe reader in the pop-up

[LIST]
[*]Find any PDF file, either on your desktop or in nautilus (Places > Home Folder > wherever).
[*]Right-click the file and select Properties.
[*]Go to the tab Open With.
[*]If Evince (Document Viewer) is listed there, press its button. Close.
[*]Otherwise:
[LIST]
[*]Press Add
[*]If Document Viewer is listed, select it and press Add. Close.
[*]Otherwise:
[LIST]
[*]Use a custom command
[*]/usr/bin/evince
[*]Add. Close.
[/LIST]
 
[/LIST]
 
[/LIST]
HTH

---

### Post by Paqman on 2009-11-13
> **Paddy Landau said:**
> Evince (Document Viewer)

It's worth pointing out that this app is included in the default install, and(IMO) does a perfectly good job of reading PDFs.

---

### Post by Paddy Landau on 2009-11-13
> **Paqman said:**
> It's worth pointing out that this app is included in the default install, and(IMO) does a perfectly good job of reading PDFs.
Agreed. However, it doesn't have the flexible printing options that Abode has, especially "Shrink to Printable Area", which I frequently need.

---

### Post by urdrwho on 2009-11-13
Thank ya very much.

I find that the fonts in the default viewer are not as clear as Adobe.  Not an Adobe fan and if PDF Xchange had a unix app...I'd be there.  I use it in Windows.

> **Paddy Landau said:**
> No, that was just to undo the [FONT=Courier New].bin[/FONT] thing. In future, use Synaptic Package Manager to uninstall. It handles all dependencies, menu entries, and so forth for you.



[LIST]
[*]Find any PDF file, either on your desktop or in nautilus (Places > Home Folder > wherever).
[*]Right-click the file and select Properties.
[*]Go to the tab Open With.
[*]If Evince (Document Viewer) is listed there, press its button. Close.
[*]Otherwise:
[LIST]
[*]Press Add
[*]If Document Viewer is listed, select it and press Add. Close.
[*]Otherwise:
[LIST]
[*]Use a custom command
[*]/usr/bin/evince
[*]Add. Close.
[/LIST]
 
[/LIST]
 
[/LIST]
HTH

---

### Post by A_M_S on 2009-11-13
If you need to install an app not present in the repos, consider using Checkinstall. It'll create an deb package for you and then you can use the Synaptic Package Manager to remove it.

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by cmcanulty on 2009-11-13
evince freezes our printer at the library.There are lots of bug posts about that issue. I wish they would fix it.

---

