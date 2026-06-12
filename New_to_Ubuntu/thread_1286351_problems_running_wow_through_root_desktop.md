---
title: "problems running wow through root desktop"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by theoak on 2009-10-08
so im running world of warcraft through a root desktop i get there by typing this into a terminal      "gksudo nautilus" 

and i cant find the wow folder that contains everything in it. i have the wow.exe file on the /root/desktop but cant find the file folder for it. 

now the problem. i am trying to download wowmatrix for the wow addons and i need to find the folder containing the world of warcraft files. if anyone can help me find these files or how i can switch wow from the root into a different folder. 

i've tried all the walk throughs to install wow in wine and had major problems and couldnt get the thing to download due to perrmisions on the new cd dvd installer discs. 

Thank You for your time in reading and hopefully posting to this thread!

---

### Post by ugriffin on 2009-10-08
Firstly, NEVER run Wine as root. Running Wine as root means that your windows apps have access to your system folders, but the viruses get root access too. There's NO need to run Wine as root, as all the new installations go straight to your home folder, where non-root wine has full privileges.


Now, regarding your WoW issue... I recommend a few workarounds. Since there's no way I can know your HD is set up, I can just recommend a few tips:

Search for "Wow.exe" from the root folder. If you've got all of your NTFS drives mounted, it should find it allright.

or...

Get the latest Wine by following the instructions [here]("http://www.winehq.org/download/deb"). The development Wine is ALWAYS better than the stable, in my opinion.

Grab your WoW CD's. If you got this legally, then you should have these. Open the CD, and then run "setup.exe", or "install.exe", etc.

WoW still needs some tweaks to work. The WoWWiki describes these perfectly, you can see that [here.]("http://www.wowwiki.com/Wine")


That's all you need. Create a desktop icon, if you want, and enjoy.

---

### Post by Vunutus on 2009-10-08
Seconding the "never run Wine as root" statement. Bad bad things can happen.

---

### Post by theoak on 2009-10-09
ok so i dont know what im doing wrong... it tells me to type this into a terminal,and do the following (replace /media/cdrom0 with wherever you mount your cds): 
[FONT=monospace]
[/FONT]wine /media/WoWDisc1/Installer.exe

as far as i know my mounted cds location is /media/cdrom0 thats what the windows says in location part when i put the cd in and the files come up.

now this is what i typed in the terminal i tried different ways.

theo@theo-laptop-ak:~$ wine /media/WoWDisc1/Installer.exe
wine: cannot find '/media/WoWDisc1/Installer.exe'

and i tried typing

theo@theo-laptop-ak:~$ wine /media/cdrom0/WoWDisc1/Installer.exe
wine: cannot find '/media/cdrom0/WoWDisc1/Installer.exe'

and i tried typing

theo@theo-laptop-ak:~$ wine /media/cdrom0/WOW3.1.0/Installer.exe
wine: cannot find '/media/cdrom0/WOW3.1.0/Installer.exe'

and i tried

theo@theo-laptop-ak:~$ wine /media/WOW3.1.0/Installer.exe
wine: cannot find '/media/WOW3.1.0/Installer.exe'

the reason why i switched WoWDisc1 to WOW3.1.0 is because the name of the cd that comes up in folder is WOW3.1.0.

but all in all it cannot find the file... i have wine, im pretty sure i've configured it right... any ideas on what i do now cause i tried the other method of copying and pasting the installer.exe file to a folder on my desktop and i got a permissions denied. now these are newer wow installer discs i just bought them a month or so ago. 

plz help! and Thank you.

---

### Post by Soulcage on 2009-10-09
The wow cds have problems w/ some of the files being missing so you can paste "sudo mount -o remount,unhide /dev/cdrom" into a terminal. Two of the things missing will be the icon which should now show as well as install.exe.

---

### Post by theoak on 2009-10-09
ok ive tried that and tried all four commands again and same cannot find the file...

---

### Post by 3rdalbum on 2009-10-09
**Tip:** If you drag a file onto the terminal, its filepath will be filled in for you.

So, in your terminal, type **wine** as normal, hit the space bar, and then drag the Installer.exe file from your file browser window onto the terminal.

---

### Post by theoak on 2009-10-09
ok so ive reinstalled wine and when i type in wine '/media/cdrom0/Installer.exe' I get this in the terminal

theo@theo-laptop-ak:~$ wine '/media/cdrom0/Installer.exe' 
wine: could not load L"D:\\Installer.exe": Module not found

i have the file to open with wine... and it cannot find the module, dont know what that is and dont know how to make it work. plz help all i want to do is install this game properly.

---

