---
title: "How do I find my 'Downloads', please?"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by L Campbell on 2009-03-25
When I downloads files such as .wmv,  .iso,  etc. how do I relocate these files?

What search criteria do I use?

TIA.

---

### Post by drs305 on 2009-03-25
Normally the files are downloaded to your Desktop, /home/yourusername/Desktop (or shortened to ~/Desktop ).

You can use the *find* command to locate a file anywhere on your system with the following:
```
sudo find / -type f -iname enter.filename.here
```
.
There is also a search feature in the main menu, Places, Search for Files

---

### Post by JohnLM_the_Ghost on 2009-03-25
More specific?

Well as far as I know programs tend to download files by default either on desktop ("~/Desktop/") or home folder ("~/").

EDIT:
> **drs305 said:**
> 
You can use the *find* command to locate a file anywhere on your system with the following:
```
sudo find / -type f -iname enter.filename.here
```

I think searching home folder is wiser, cause I doubt those files go anywhere else...
```
find ~/ -type f -iname enter.filename.here
```
like this

---

### Post by mcduck on 2009-03-25
...or, assuming you are talking about files you have downloaded with Firefox, just check from Firefox's settings where it's saving the files. ;)

---

### Post by kpkeerthi on 2009-03-25
I believe GNOME has Find option somewhere in the Places menu.

---

### Post by L Campbell on 2009-03-25
> **drs305 said:**
> Normally the files are downloaded to your Desktop, /home/yourusername/Desktop (or shortened to ~/Desktop ).

You can use the *find* command to locate a file anywhere on your system with the following:
```
sudo find / -type f -iname enter.filename.here
```
.
There is also a search feature in the main menu, Places, Search for Files

Thanks, I tried this but I must have done something wrong.

qwer@qwer-desktop:~$ sudo find / -type f -iname enter.RespectTheSenior.wmv
[sudo] password for qwer: 
find: /home/qwer/.gvfs: Permission denied

---

### Post by gaming_guy on 2009-03-25
> **L Campbell said:**
> Thanks, I tried this but I must have done something wrong.

qwer@qwer-desktop:~$ sudo find / -type f -iname enter.RespectTheSenior.wmv
[sudo] password for qwer: 
find: /home/qwer/.gvfs: Permission denied

i'm new to ubuntu myself, but i think you have got the command slightly wrong:

sudo find / -type f -iname RespectTheSenior.wmv

then when it asks for a password, enter the same password for the account you used to log on to the machine with and press enter

hope this helps

---

### Post by L Campbell on 2009-03-25
> **gaming_guy said:**
> i'm new to ubuntu myself, but i think you have got the command slightly wrong:

sudo find / -type f -iname RespectTheSenior.wmv

then when it asks for a password, enter the same password for the account you used to log on to the machine with and press enter

hope this helps

Thanks for your interest.

What happens with Ubuntu is that, when you enter your password, it doesn't 'show'.  This is a security measure.

Kind regards.

---

### Post by gaming_guy on 2009-03-25
i'm pretty sure its a security measure as it does the same on my linux based firewall (and i think fedora does it as well)

---

### Post by Vere nicolson on 2010-04-23
[FONT=DejaVu Sans, sans-serif]I am an absolute beginner determined to get the hang of this. [/FONT] 
 [FONT=DejaVu Sans, sans-serif]Where has Ubuntu put my downloads and what do I do to run it, and preferably put an object on the desktop to launch it when I chose[/FONT]
 

 

 [FONT=DejaVu Sans, sans-serif]Using Ubuntu 9.10[/FONT]
 [FONT=DejaVu Sans, sans-serif]I found the PPA I was after on Launchpad “ppa:arduino-ubuntu-team/ppa ”[/FONT]
 

 [FONT=DejaVu Sans, sans-serif]Then in terminal ran;[/FONT]
 [FONT=DejaVu Sans, sans-serif] [/FONT]
 sudo add-apt-repository ppa:arduino-ubuntu-team/ppa 
  
 Then2;
 sudo apt-get update 
 

  Then3;
 sudo apt-get dist-upgrade 
  I think that should have got me the download but I also followed instructions on  ( [http://linuxers.org/howto/how-install-any-software-ubuntu-ppa](http://linuxers.org/howto/how-install-any-software-ubuntu-ppa)    ) for earlier distributions
 

 

   Then4;
 sudo gedit /etc/apt/sources.list 
  
 Added the PPA to the end of the source list and saved it, then added the PGP key
  Then5;
 sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 97A63961
 (where 97A63961 is the second part of the signing key.)
 I did it all over using the GUI “Software sources”
 47 files were downloaded but I can find them.


I used "locate arduino and found a bunch in the "trash" files but when I pasted the path into "Places, Find Files" it said "nautilus could not handle this type of location
Where do I find trash files if nautilus cant go to "home/vere/.local/share/Trash/files/arduino-0017"


Thanks in antisipation. I don't mind starting over, I just want to eliminate the mistakes this time.


Cheers

---

### Post by kanikilu on 2010-04-23
You probably should have started a new thread, but anyways, by adding the PPA repo, all you did is tell Ubuntu where to look for software, you didn't actually install the package you were looking for. Rather than "dist-upgrade" in step 3, I think all you needed was: ```
sudo apt-get install arduino
```

---

### Post by Vere nicolson on 2010-04-24
Thanks Kanikilu,
Tried that and still no files anywhere I can get to.
Started a new thread this time.

Cheers
Vere

---

### Post by ed-koala on 2010-04-24
Try this ... Empty your trash. Then open up Synaptic and search for arduino.  If the box is filled, click it and select mark for complete removal.  Hit apply.  Then try reinstalling.

If it wasn't filled, install it.

---

