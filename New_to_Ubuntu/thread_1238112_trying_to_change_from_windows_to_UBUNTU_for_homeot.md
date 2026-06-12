---
title: "trying to change from windows to UBUNTU for home/other usage"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by takke on 2009-08-12
Dear Sir/Madam/Computer-person

The computer is being used in a general family environment and consists of general usage (eg. reading, typing, emails and occasionally some videos (you-tube)).


I have tried reading the other forums, but unfortunately cannot understand it as i have loss all technical computer jargon a few years back.


I am experiencing the following problems for the transition to be convenient for users at home:
[U]I cannot successfully install the following

Adobe Reader:[/U]  
1. On the desktop, the icon *"AdbeRdr9.1.2-1_i486linux_enu.bin"* and says when opening *"The file is of an unknown type"*
2. This icon type reflects *"unknown (application/octet-stream)"*
2. The above-mentioned icon was downloaded from Adobe's website[U]

A media player [/U]
1. What may i use to view download videos from you-tube and for other general video usage.
2. The one (flvplayerv2.0.exe) that was used on windows cannot be used. Could this be why??? as its type is *"DOS/Windows executable (application/x-ms-dos-executable)"* [U]

A program that allows you to write in Arabic
[/U]1. The previous type was *"program (application/octet-stream)"* 
2. I think that it also used this program*- **shamela.exe** *its type *"DOS/Windows executable (application/x-ms-dos-executable"*


I hope you will find the above details clear and available, if you need any further


Kind Regards

The Layman

---

### Post by Paqman on 2009-08-12
> **takke said:**
> 
[U]I cannot successfully install the following

Adobe Reader:[/U]  
1. On the desktop, the icon *"AdbeRdr9.1.2-1_i486linux_enu.bin"* and says when opening *"The file is of an unknown type"*
2. This icon type reflects *"unknown (application/octet-stream)"*
2. The above-mentioned icon was downloaded from Adobe's website


Ubuntu comes with the ability to open PDF files already. Just click on the PDF file and it'll open, no install needed.

> 
A media player
1. What may i use to view download videos from you-tube and for other general video usage.
2. The one (flvplayerv2.0.exe) that was used on windows cannot be used. Could this be why??? as its type is *"DOS/Windows executable (application/x-ms-dos-executable)"*


When you view a Flash video online, it's temporarily saved into the /tmp folder. You can copy it from that folder and open it with any media player, including the default one that's preinstalled.

> 
A program that allows you to write in Arabic
1. The previous type was *"program (application/octet-stream)"* 
2. I think that it also used this program*- **shamela.exe** *its type *"DOS/Windows executable (application/x-ms-dos-executable"*

Can you not just set Arabic as your language? You should then be able to type in Arabic in any application.

---

### Post by 3rdalbum on 2009-08-12
Welcome to Ubuntu.

1. There is already a program installed on Ubuntu that can read Adobe Acrobat (.pdf) files. When you double-click on a PDF, it will open.

If you really want the official Adobe Reader software, you can add it easily on Ubuntu, but to do this we'll have to explain about software installation.

On Linux, you generally use a program called a "package manager" to download and install software, rather than surfing the web and downloading programs using your web browser. It's more efficient, and easier to do.

Adobe Reader is available in the Ubuntu package manager, and it is very simple to install, but it requires one extra step.

Go to System > Administration > Software Sources. Make sure that the top 4 checkboxes are ticked; if they aren't, then click them to tick them. This enables almost all the repositories you will need in Ubuntu. Click on the "Third Party Software" tab at the top of the window, and you should see two extra repositories there starting with "http://archive.canonical.com". Make sure these are ticked as well.

Click the "Close" button at the bottom-right of the window, and then click "Reload" when you are asked to reload the package list.

Now go to System > Administration > Synaptic Package Manager. In the "Quick Search Box", type "acroread" (without the quote marks). You will see the Acroread package displayed. Right-click it and choose Mark For Installation. It will tell you that it will install some other packages, click OK. Now click Apply and Ok and the package will be downloaded and installed for you.

When it has finished installing, close the package manager and Acrobat Reader will be available in the Applications menu.

2. Flash Video (.flv) is also usable on Ubuntu. The best program for playing flv files is VLC Media Player. You can use the package manager to install VLC.

Windows programs generally cannot be used on Linux. You might hear of some software called Wine, which is an attempt to make a way for Windows programs to run, but in the end you will be happier using Linux software.

As for downloading Youtube videos, once you have Flash Player installed (you can install it from the package manager, it's called "flashplugin-nonfree") you just go to the video you want to download, wait until it has fully loaded into the window, and then go to Places > Computer, double-click on Filesystem and double-click on "tmp". Your Flash video will be in there, ready to copy to your home directory.

3. I'm sorry I can't help you with this; I don't write in Arabic and I haven't heard of the necessary software. Ubuntu and Linux are used in many parts of the world, and I know that Ubuntu has Arabic language support, but I don't personally know how to write in Arabic on Ubuntu.

---

### Post by oldfred on 2009-08-12
Under System/Preferences/Keyboard - the second tab - layouts, allows you to add other keyboards. Many countries are shown, the first is Afghanistan (scroll down for all other countries) and you then can also choose dialect.

---

### Post by Terl on 2009-08-12
> **takke said:**
> Dear Sir/Madam/Computer-person

The computer is being used in a general family environment and consists of general usage (eg. reading, typing, emails and occasionally some videos (you-tube)).


I have tried reading the other forums, but unfortunately cannot understand it as i have loss all technical computer jargon a few years back.


I am experiencing the following problems for the transition to be convenient for users at home:
[U]I cannot successfully install the following

Adobe Reader:[/U]  
1. On the desktop, the icon *"AdbeRdr9.1.2-1_i486linux_enu.bin"* and says when opening *"The file is of an unknown type"*
2. This icon type reflects *"unknown (application/octet-stream)"*
2. The above-mentioned icon was downloaded from Adobe's website[U]

A media player [/U]
1. What may i use to view download videos from you-tube and for other general video usage.
2. The one (flvplayerv2.0.exe) that was used on windows cannot be used. Could this be why??? as its type is *"DOS/Windows executable (application/x-ms-dos-executable)"* [U]

A program that allows you to write in Arabic
[/U]1. The previous type was *"program (application/octet-stream)"* 
2. I think that it also used this program*- **shamela.exe** *its type *"DOS/Windows executable (application/x-ms-dos-executable"*


I hope you will find the above details clear and available, if you need any further


Kind Regards

The Layman

To install adobe from what you downloaded you need to do a few things from command line.  It is very simple.  Open a terminal (under accessories)

When you first open it you will be in your home directory.  You need to move to your desktop which is in your home.  To do this type : ```
cd Desktop
```  You can actually type the cd then De and hit the tab key and it should finish it up for you.

The next step will change the file into an executable for you. ```
chmod a+x Ad (then hit tab and it will finish the filename for you)
```  Now we can get started :)  Once you have that done type ```
./Ad (and hit tab again to finish the file name)
```  It will extract a bit and then ask where you want it to go.  I installed mine in my home folder.  If you want to do the same you would enter /home/(your username home).  If you want to install it to the default location you should start the installation with ```
sudo ./Ad (hit tab to complete filename)
``` then enter the password and when prompted for where to install you can accept the default.

As for flash, type the following in the terminal: ```
sudo apt-get install ubuntu-restricted-extras
```  This will install flash, other multimedia codecs, Java runtime, and Microsoft TTF fonts.

Like the others I can't really help you with the Arabic support.  You may wish to google for that.

---

