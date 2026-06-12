---
title: "Install .tar.gz    Help"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by azzaw on 2009-08-22
Hi.  I have been trying to install the program audio converter from here:

[COLOR=DeepSkyBlue]http://linux.softpedia.com/progDownload/Audio-Convert-Download-3104.html[/COLOR]

I have downloaded and extracted the "Source Mirror 1 .tar.gz"

I am having heaps of trouble installing from here.  I green as at Linux and I think i have read a bunch of "Installing .tar.gz." posts and links but I havnt really got anywhere.  Just wondering if anyone out there may be able to point me in the right direction?  I would like to learn how to install .tar.gz files.  I have tried ths link:
[COLOR=DeepSkyBlue]http://amitech.50webs.com/installing/index.php.html#installing_a_package_manually
[/COLOR]

---

### Post by zvacet on 2009-08-22
I think you will get same result if you do [this #5.]("http://ubuntuforums.org/showthread.php?t=54821&highlight=audio-convert")After installing nautilus-script-audio-convert find it synaptic and right click on it.It will show what else you can install to get it work.Install all of them and that is it.

---

### Post by SoftwareExplorer on 2009-08-22
> to install it as a nautilus script, copy 'audio-convert' in /usr/bin, then run 'audio-convert-install'. or, follow the instructions on this link: [http://g-scripts.sourceforge.net/faq.php](http://g-scripts.sourceforge.net/faq.php).
So, extract audio-convert and audio-convert-install. Run ```
gksudo nautilus
``` and go to where you saved the file. Copy audio-covert to the folder /usr/bin. Then go to Applications->Accessories-> terminal. run ```
pwd
``` to find out where you are in the terminal. use ```
cd 'foldername'
``` open a folder. Use ```
cd ..
``` to go up a folder. Use those commands to get to where you extracted the two files and run ```
./audio-convert-install
```.

Hope that helps--tell me if you need more details.

---

### Post by SoftwareExplorer on 2009-08-22
Well, I see zvacet beat me to it and with an easier way. I should lean to type faster. :)

---

### Post by steveneddy on 2009-08-22
[This]("http://ubuntuguide.org/wiki/Ubuntu:Jaunty#FFMPEG_video_.2F_audio_conversion") is my recommendation.

---

### Post by perce on 2009-08-22
These programs are in the repository (i.e. no need to compile): 
nautilus-script-audio-convert, soundconverter

have you checked if they do what you need?

---

### Post by azzaw on 2009-08-22
Sorry I am still green to Linux but I try to copy any file to /usr/bin I have no Rights,  ie. canot copy, i think maybe that is part of my problem, maybe,

---

### Post by azzaw on 2009-08-22
Dont fully understand what your saying "Software Explorer" But really Really want to.  I am really new to Linux perhaps simpler step by step.

---

### Post by SoftwareExplorer on 2009-08-22
You have to copy it as root--the user that can administer the system and make system wide changes that effect the whole system. To run the file browser as root you should press Alt+F2 and type in ```
gksudo nautilus
```. It will ask for your password and the file window that comes up has root permissions and should be able to copy it without you getting a permission denied. If you need help finding your way around the file system, then I can try to explain it.

---

### Post by Hendrixski on 2009-08-22
Yeah, security...


The average user does not have a lot of rights on the system, and this is a good thing. So don't worry, you're not supposed to do these things as a regular user, that's not part of "the problem", everything seems OK so far.

There's a user called "root" which is on every Unix system, which has unlimited rights.  Let's just say it's not safe to run the system as the super user. Ubuntu let's some users access this temporarily through a command called sudo (or in the case of the instructions above with gksudo, which is the graphical version, but essentially the same thing). That's much safer, so the way they're describing above will give you the permissions to do these things.

hope that helps

---

### Post by steveneddy on 2009-08-22
> **perce said:**
> These programs are in the repository (i.e. no need to compile): 
nautilus-script-audio-convert, soundconverter

have you checked if they do what you need?

to the OP - you saw this post - right?

Why do you want to compile software that does something as simple as file format conversion when there are perfectly good tool ready for you to use in the repos.

You really need to look at the links in my sig and start reading from the top to the bottom.

You may need a better feel of the environment you are in and stop feeling as if everything ectra needs to be downloaded.

Not to say that downloading software is a bad thing, but most of what the average user is going to need is available in the repos.

Open up Synaptic Package Manager and look at all of the software there.

System --> Administration --> Synaptic Package Manager

---

### Post by azzaw on 2009-08-22
Thanks for that "steveneddy".  I am just going through the motions so as I can learn.  Throwing myself in the deep so to speak.  

I have copied the file "Audio-convert" into File-System/usr/bin .  But I cannot navigate to there in the Terminal:

wazza@wazza-desktop:~$ cd File System/usr/bin
bash: cd: File: No such file or directory
wazza@wazza-desktop:~$ cd File System
bash: cd: File: No such file or directory
wazza@wazza-desktop:~$ 


Also when I push alt-f2 what do  [I]use this window for?

[/I]I have another thread that has been solved how do I mark this as Solved[I]?
[/I]

---

### Post by oldos2er on 2009-08-22
There is no directory named "File System," you'd want to simply run **cd /usr/bin**.

---

### Post by SoftwareExplorer on 2009-08-23
The alt F2 window lets you run a command. In this case ```
gksudo nautilus
```, a command that will run your file browser as the root user.

As far as the filesystem thing, it's real name is /. The file browser in its effort to be friendly had to think up a name for it so it refers to what is really / as File System. Sorry, I should have made that more clear.

To mark a thread as solved, scroll to the bottom of the page. Click edit tags and add solved. Go to the first post and edit it. Add solved to the start of the title.

---

### Post by azzaw on 2009-08-23
OK, so I ran this:

wazza@wazza-desktop:~$ cd /usr/bin/audio-convert-0.3.1.1/
wazza@wazza-desktop:/usr/bin/audio-convert-0.3.1.1$ ./audio-convert-install
wazza@wazza-desktop:/usr/bin/audio-convert-0.3.1.1$ 

And straight away the last line came up and nothing else happened.

---

### Post by oldos2er on 2009-08-23
Reading back through this thread, I have to wonder why you are not installing this software using Synaptic or Add/Remove...? Far easier to use a package manager.

---

### Post by SoftwareExplorer on 2009-08-23
> **azzaw said:**
> OK, so I ran this:

wazza@wazza-desktop:~$ cd /usr/bin/audio-convert-0.3.1.1/
wazza@wazza-desktop:/usr/bin/audio-convert-0.3.1.1$ ./audio-convert-install
wazza@wazza-desktop:/usr/bin/audio-convert-0.3.1.1$ 

And straight away the last line came up and nothing else happened.
It probably worked then. Go ahead and try to use the program and see if it works. If it doesn't, I would recommend using synaptic to install nautilus-script-audio-convert or soundconverter if they are what you need.

---

### Post by azzaw on 2009-08-23
Thanks everyone for your help.  I still couldnt get it to work.  I will try "oldos2er" suggestion and try the package installer next time.  Thanks

---

