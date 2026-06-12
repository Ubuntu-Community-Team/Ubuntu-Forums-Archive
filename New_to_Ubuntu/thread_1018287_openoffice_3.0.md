---
title: "openoffice 3.0"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by Andrew79 on 2008-12-21
Okay, so I have been trying all sorts of different suggestions that I have searched the posts and got. I bought the magazine with the disk. Yet I still can not get OOo3.0 to load. I still have 2.4, what else can anybody suggest?

---

### Post by SunnyRabbiera on 2008-12-21
Personally I would stick to OO2 as right now OO3 is still fresh and doesnt really offer much over oo2, unless you want .docx support.

---

### Post by 73ckn797 on 2008-12-21
> **Andrew79 said:**
> Okay, so I have been trying all sorts of different suggestions that I have searched the posts and got. I bought the magazine with the disk. Yet I still can not get OOo3.0 to load. I still have 2.4, what else can anybody suggest?


Did you try  this:
```
I have installed OO 3.0 on my desk and laptops with Intrepid. Everything was effortless and is running great.

I completely removed all OO related installs through Synaptic.

Downloaded the file (OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz) from Openoffice.org

Created a directory in /home/name/whatever.

Extracted files using File Roller (default Gnome compression utility) to the created directory. 

Went to terminal and "cd" to new directory (example: /home/name/OO3/DEBS) then entered "sudo dpkg -i *.deb" The "DEBS" sub-directory is created when extracting. This installs the program.

Then changed to the other sub-directory created during extract (~/DEBS/desktop-integration) and repeated command "sudo dpkg -i *.deb". This creates the menu choices.

Started OO 3.0 and it works like a charm for me.

The desktop icon created using menu right click was read only but right click, properties allows changing that so I could rename the shortcut icon.
```

---

### Post by evilkastel on 2008-12-21
thats true. still i could not wait. so first go to synaptic and uninstall everything, everything thas is related to openoffice 2.4. the language packs and thesaurus can be left. download the debs from [www.openoffice.org](www.openoffice.org). run, then 
```
sudo dpkg -i /this/isthe/uncompressed/folder/withthe.deb && sudo apt-get install -f
```
EDIT: i believe that if you do not run apt-get in the commmand the package gets sort of half installed 
you have then to install the desktop integration deb inside a separate folder inside the OO debs folder.

---

### Post by woaiwojia on 2008-12-22
add the following to your sources.list

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main

then open the terminal

   sudo apt-get update && sudo apt-get upgrade

---

### Post by Andrew79 on 2008-12-22
I am not sure what your saying sources? I just downloaded from the website for 45 minutes, plus have a CD, why do I need to keep going other places? I have been to the launchpad site, and have no clue what I am supposed to even do there. Could some one very kindly in plain language explain this a little more?
Sorry for this, but I have been fighting with the dang thing for 3 days now, and all I have managed to do is unistall and the re-install 2.4 3 times.

---

### Post by jimrz on 2008-12-22
> **Andrew79 said:**
> I am not sure what your saying sources? I just downloaded from the website for 45 minutes, plus have a CD, why do I need to keep going other places? I have been to the launchpad site, and have no clue what I am supposed to even do there. Could some one very kindly in plain language explain this a little more?
Sorry for this, but I have been fighting with the dang thing for 3 days now, and all I have managed to do is unistall and the re-install 2.4 3 times.

try following [**_[COLOR="Sienna"]this how-to[/COLOR]_**]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml#") it is simple and worked for me with both hardy and intrepid (if you are running intrepid, just copy from the site as is but, if using hardy you will need to replace "intrepid" with "hardy" when you paste the instruction into your software sources.

---

### Post by anim on 2008-12-22
The reason that you need to download the Ubuntu version from the PPA is that Ubuntu requires a few hacks to oo.org 3.0 before it works. The package downloaded from the openoffice.org website did not work for me either but following the guide posted above by  jimrz did work.

---

### Post by Andrew79 on 2008-12-22
Thank You. I believe this helped, it looks like it is updating and installing right now. I will post this solved if it worked, with in the next few minutes

---

### Post by raymondvillain on 2008-12-25
Hello 73ckn797;

I am trying to install OO.org 3.0 and your comments on how to do this included the phrase "Extracted files using File Roller (default Gnome compression utility)..."

What exactly is File Roller?  I have Intrepid on a desktop.  When I use the bulit in gui file browser I can click on a file and extract it using the options that pop up with a right click.  Is that the same thing?  Or is File Roller a separate utility?

Many thanks, and happy holidays.

---

### Post by abn91c on 2008-12-25
before you go "hacking", installing/removing from random websites use this guide from Softpedia, it is the most reliable, I used it in 3 different computers and it installed fine
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

Only giltch will be if you use Kubuntu, hem you will have to remove this file openoffice.org-kde

---

### Post by raymondvillain on 2008-12-25
How do you start up OO3 after doing the install?  I followed your instructions to the letter, but I have no desktop icon.

---

### Post by abn91c on 2008-12-25
> **raymondvillain said:**
> How do you start up OO3 after doing the install?  I followed your instructions to the letter, but I have no desktop icon.
you have to add them from the office menu, by default OO3 does not put them in the desktop. In the applications>office menu right click on the icon then select add to desktop

---

### Post by 73ckn797 on 2008-12-25
> **raymondvillain said:**
> Hello 73ckn797;

I am trying to install OO.org 3.0 and your comments on how to do this included the phrase "Extracted files using File Roller (default Gnome compression utility)..."

What exactly is File Roller?  I have Intrepid on a desktop.  When I use the bulit in gui file browser I can click on a file and extract it using the options that pop up with a right click.  Is that the same thing?  Or is File Roller a separate utility?

Many thanks, and happy holidays.

File roller is the default compression utility in Ubuntu. When you double click on any compressed file, it is the program that allows you to view the compressed contents of the file. From there you can extract the files to either the default folder that the compressed file has been saved to do/create or designate your own folder. The extraction will still create the directories (DEBS and desktop-integration within a coded like folder name) I mention in my directions.

Does that help?

---

### Post by Norm24 on 2008-12-25
This will work for installing 3.0

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

Never mind.

Didn't see the previous post suggesting this.

---

### Post by 73ckn797 on 2008-12-25
> **raymondvillain said:**
> How do you start up OO3 after doing the install?  I followed your instructions to the letter, but I have no desktop icon.


If you have followed the instructions I provided, a desktop icon will be created during the second install command I list from within the "desktop-integration" sub-folder. 

EDIT: The desktop icon may not appear until going to Applications/Office/OpenOffice.org 3.0 Writer and right clicking to add to desktop or panel. Then my icon comments in the instructions would apply.

---

