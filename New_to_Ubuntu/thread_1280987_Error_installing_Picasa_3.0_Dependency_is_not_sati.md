---
title: "Error installing Picasa 3.0: Dependency is not satisfiable"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by hazypictures on 2009-10-02
I just installed my first dual boot Ubuntu/Vista OS. Finally! 

I want to primarily use Ubuntu. I have 9.04 64 bit running on a new HP G60 Notebook Pentium R Dual Core T4200, 2.0 GHz, 4 GB RAM, 64 bit OS.

I have been using Picasa 3 for a long time and really like and would like to continue using it.

When I downloaded the [SIZE=-1][Debian/Ubuntu amd64]("http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_amd64.deb") [/SIZE][SIZE=-1]but when I tried to install it, I rec'd the following error:

[/SIZE]```
Error: Dependency is not satisfiable: libc6-i386 (>=2.2)
```

Did I choose the wrong version?

Do I need to install WINE? (I don't know what that is.)

This is my first attempt to install Linux/Ubuntu software. Help will be greatly appreciated.

---

### Post by sandyd on 2009-10-02
you know what?

picasa 3.5 is out. and its runnable in WINE.
i know that google says that it dropped support for picassa 3.5 
but it still works. copy and paste....

```

cd /usr/bin/
wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)
sudo chmod 777 winetricks
sudo apt-get install cabextract wine wine-gecko //not sure if the version of wine in repos works correctly, im using the WINE ppa. See below if the picassa installer doesn't run.
winetricks allfonts fontsmooth-rgb gecko allfonts

```Then download picasa for windows
([http://dl.google.com/picasa/picasa35-setup.exe](http://dl.google.com/picasa/picasa35-setup.exe))
run it, and the installer should start.

If that doesn't work,
run one of these (accoring to your ubuntu version) 
**For Ubuntu Jaunty (9.04):**```

*sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list -O /etc/apt/sources.list.d/winehq.list*
``` **For Ubuntu Intrepid (8.10):**```

*sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/winehq.list*
``` **For Ubuntu Hardy (8.04):**```

*sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list*

```then run
```

*wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -*
sudo apt-get update
sudo apt-get install wine

```then try again...

---

### Post by hazypictures on 2009-10-04
Thank you for these code bits. I'm only days into Ubuntu so I have some noob Qs. Do I type those commands into the Terminal? I tried that but it said that "-0 was an invalid command".

I tried to copy and paste the code but it doesn't work. Therefore I keyed it all in and may have made a typo? Is there a way to make copy & paste work in terminal? Should I not be using terminal?

---

### Post by hazypictures on 2009-10-04
I tried this:
> **carlee said:**
> 

```

cd /usr/bin/
wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)
sudo chmod 777 winetricks
sudo apt-get install cabextract wine wine-gecko //not sure if the version of wine in repos works correctly, im using the WINE ppa. See below if the picassa installer doesn't run.
winetricks allfonts fontsmooth-rgb gecko allfonts

```.

and after the 2nd line I got this:

```
Resolving winezeug.googlecode.com... 66.249.90.82
Connecting to winezeug.googlecode.com|66.249.90.82|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 105294 (103K) [text/plain]
winetricks: Permission denied
```

Any suggestions?

---

### Post by hazypictures on 2009-10-05
Thanks for the code Carlee! It worked!

> **hazypictures said:**
> Do I type those commands into the Terminal? I tried that but it said that "-0 was an invalid command".

I tried to copy and paste the code but it doesn't work. Therefore I keyed it all in and may have made a typo? Is there a way to make copy & paste work in terminal? Should I not be using terminal?

I discovered that I can't copy & paste into Terminal using Ctrl+C and Ctrl+P, but I can by right clicking and selecting Copy or Paste. Hooray!

I copied the first code block into Terminal and it executed. Then I downloaded Picasa from the link and it worked! Thank you.

My only Q now is: How do I get Picasa to import the albums that I had on my old computer?

Thanks!!

---

### Post by MrWES on 2009-10-05
FYI, you can actually hightlite and drag the text on to the terminal too.

---

### Post by hazypictures on 2009-10-05
> **MrWES said:**
> FYI, you can actually hightlite and drag the text on to the terminal too.

Wow. Thanks for this tip!

---

### Post by abhishek.malhotra35 on 2009-10-05
Picasa deb package can be downloaded from below link:
[http://picasa.google.co.in/intl/en/linux/download.html#picasa30](http://picasa.google.co.in/intl/en/linux/download.html#picasa30)

If you are getting lib6 dependancy error that means your libc version is outdated. You can install a new version using below command.

apt-get install libc6.

---

### Post by MrWES on 2009-10-05
> **abhishek.malhotra35 said:**
> Picasa deb package can be downloaded from below link:
[http://picasa.google.co.in/intl/en/linux/download.html#picasa30](http://picasa.google.co.in/intl/en/linux/download.html#picasa30)

If you are getting lib6 dependancy error that means your libc version is outdated. You can install a new version using below command.

apt-get install libc6.

```
sudo apt-get install libc6
```

You'll need the sudo command, and sans the period.

~Bill

P.S. Hrmm...post number 777 -- lucky 7's!

---

### Post by hazypictures on 2009-10-23
Carlee (and others):

> **carlee said:**
> you know what?

picasa 3.5 is out. and its runnable in WINE.
i know that google says that it dropped support for picassa 3.5 
but it still works. copy and paste....



I installed 3.5 and loved it. The face recognition was working thru my large collection. Then I clicked on Places and it is frozen on 'loading maps'. I can't even shut it down. So, I un-installed it and tried to reinstall. I downloaded the wine updates (that were from an unknown source.) I downloaded the picasa 3.5 again and it will not launch.

Help!

I am running 64 bit Juanty. Is it not compatible?

I see that many people have freezing on the map. Did anybody find a solution?

---

### Post by skompier on 2009-10-23
> **hazypictures said:**
> 
I discovered that I can't copy & paste into Terminal using Ctrl+C and Ctrl+P, but I can by right clicking and selecting Copy or Paste. Hooray!


You can ctrl+shft+v to paste into the terminal also..;)

---

### Post by OldGoat58 on 2009-12-09
But will ANY of these options work in Ubuntu 9.10 Karmic Koala?  I tried getting Picasa to work prior to changing to the 32 bit build of Karmic and I had error after error.  I started playing with GIMP because it came with Ubuntu but I like the ease of use that Picasa offers.

I'll gladly report any success or failure.

Thanks!
Mike
Fairless Hills, PA:)

---

### Post by OldGoat58 on 2009-12-09
I had started a thread on the "General Information" board regarding this exact Google Picasa error.  One of the FANTASTIC UBUNTU FORUM MEMBERS posted this as a solution for Google Picasa for Ubuntu 9.10 Karmic Koala i386.  John NewBuntu is to be credited for the fix.

Thanks!
Mike
Fairless Hills, PA

 					Originally Posted by **john newbuntu** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8432428#post8432428") 				
 				[I]Ok Mike. Finally I got around trying to doing it myself. Since I love and have used Picasa several times before, I decided to try it myself for the first time on Linux. On installation, I had the exact same problem that you had. So here's what I did:
1. Completely uninstall picasa from Synaptic Package Manager.
2. In synaptic, go to settings->repositories-other software.
3. Uncheck the checkbox of deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
4. Click on Add and add this under the apt line:[FONT=monospace]
[/FONT]5. Now go to edit->reload package information
6. Type Picasa in quick search, mark for installation and apply.
After the installation completes, I have a working Picasa just like how it was in Windows.:grin:

This is a beta version of Picasa for Linux.  Anyway, as long as the bleeding edge works I am happy.[/I]

---

### Post by hazypictures on 2009-12-09
I couldn't get Picasa 3 to work. I've been using Picasa 2 with Wine, but I'm interested in finding an open source alternative. I should try GIMP.

---

### Post by OldGoat58 on 2009-12-10
> **hazypictures said:**
> I couldn't get Picasa 3 to work. I've been using Picasa 2 with Wine, but I'm interested in finding an open source alternative. I should try GIMP.

I played with GIMP and it is an extremely useful tool for hardcore photo shopping.  It is nice in the fact that it opens just about anything, has a lot of editing options, and seems to be fairly stable.  

If you try it I would suggest trying to find the "HELP" documentation to download with it.  My distro didn't come with the active help and that made it a trial and error thing.  I do not have patience to diddle that much with photos but I'm not like most people!  (thank god huh?)

---

### Post by Dooglus on 2010-11-30
> **hazypictures said:**
> Carlee (and others):
Then I clicked on Places and it is frozen on 'loading maps'. I can't even shut it down. [...] Did anybody find a solution?

I did:

rm ~/.google/picasa/3.0/*.reg

That fixes the problem by wiping out all the registry files for picasa.  I don't know what else is in them, but I've not missed anything.  The albums and stuff are stored elsewhere.

If I cared, I could find out which bit of which .reg file is causing the trouble, but I don't so I didn't.  You could though if you want to.

Chris.

---

