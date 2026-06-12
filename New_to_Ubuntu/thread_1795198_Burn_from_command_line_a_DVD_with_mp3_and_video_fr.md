---
title: "Burn from command line a DVD with mp3 and video from several places?"
date: 2011-07-02
forum: New to Ubuntu
---

### Post by honeybear on 2011-07-02
I have this file: 

/tmp/filestoburn.txt

```

/home/xeratox/partitionspianos/*.mp3
/home/xeratox/piano/*.mid
/home/xeratox/concerto/*.avi
/home/xeratox/spectacles/July_Zenit_Arena.avi

```

the command: 
```
 growisofs -dvd-compat -speed=2 -Z /dev/sr0 < /tmp/filestoburn.txt
```

is not working ... :( 

Any help would be appreciated

edit: I would like a regular data DVD of data format.

---

### Post by Gryllida on 2011-07-02
- Create .iso image using *mkisofs*
- Write the .iso image to the CD using *cdrecord*

More details: 
- [http://sharkysoft.com/tutorials/linuxtips/cdcommands/](http://sharkysoft.com/tutorials/linuxtips/cdcommands/)
- [http://linuxcommand.org/man_pages/dvdrecord1.html](http://linuxcommand.org/man_pages/dvdrecord1.html)

---

### Post by honeybear on 2011-07-02
> **Gryllida said:**
> - Create .iso image using *mkisofs*
- Write the .iso image to the CD using *cdrecord*

More details: 
- [http://sharkysoft.com/tutorials/linuxtips/cdcommands/](http://sharkysoft.com/tutorials/linuxtips/cdcommands/)
- [http://linuxcommand.org/man_pages/dvdrecord1.html](http://linuxcommand.org/man_pages/dvdrecord1.html)

and this without a temp *.ISO. I would like to burn directly...

---

### Post by dcsoldschool53 on 2011-07-02
> **honeybear said:**
> and this without a temp *.ISO. I would like to burn directly...
  I have a question, in the command```
growisofs -dvd-compat -speed=2 -Z /dev/sr0 < /tmp/filestoburn.txt
``` what does this mean,```
 < /tmp/filestoburn.txt
``` because I did not see it in the man page. Maybe I did and just over looked it. I am talking about the < sign before the file location.

[http://manpages.ubuntu.com/manpages/natty/man1/growisofs.1.html](http://manpages.ubuntu.com/manpages/natty/man1/growisofs.1.html)

---

### Post by honeybear on 2011-07-02
> **dcsoldschool53 said:**
> I have a question, in the command```
growisofs -dvd-compat -speed=2 -Z /dev/sr0 < /tmp/filestoburn.txt
``` what does this mean,```
 < /tmp/filestoburn.txt
``` because I did not see it in the man page. Maybe I did and just over looked it. I am talking about the < sign before the file location.

[http://manpages.ubuntu.com/manpages/natty/man1/growisofs.1.html](http://manpages.ubuntu.com/manpages/natty/man1/growisofs.1.html)

I found that in a forum, and tried to change the switches. would mean to use the file. 

Otherwise something like this would be nice but it does not work, but states well like man says...
```
growisofs -dvd-compat -speed=2 -Z /dev/cdrom -R -J -pad  /tmp/filestoburn.txt
```

---

### Post by honeybear on 2011-07-02
is that a better method? 

```
/usr/bin/growisofs -Z /dev/hdd -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=dao -dvd-compat -speed=6 -gui -graft-points -volid K3b data project -volset -appid K3B THE CD KREATOR VERSION 0.11.14 (C) 2003 SEBASTIAN TRUEG AND THE K3B TEAM -publisher -preparer K3b - Version 0.11.14 -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-satimis/k3bH0ARVb.tmp -rational-rock -hide-list /tmp/kde-satimis/k3bLUAwFb.tmp -full-iso9660-filenames -max-iso9660-filenames -iso-level 2 -path-list /tmp/kde-satimis/k3bWcPrqc.tmp 
```

---

### Post by dcsoldschool53 on 2011-07-04
After thinking about this for a couple days, I know that this will work to copy that file to DVD. I had tried this, and it burned this file```
growisofs -Z /dev/dvd /home/user-name/Gnome-Panel/Gnome_Panel.xml
```The only problem I had, was that it had burned the file using only 8 characters```
Gnome-Pa.xml
```I know that -dvd-compat is for videos so we don't want to use it in this case. I am not sure about use the force luke.

---

### Post by dcsoldschool53 on 2011-07-04
> **Gryllida said:**
> - Create .iso image using *mkisofs*
- Write the .iso image to the CD using *cdrecord*

More details: 
- [http://sharkysoft.com/tutorials/linuxtips/cdcommands/](http://sharkysoft.com/tutorials/linuxtips/cdcommands/)
- [http://linuxcommand.org/man_pages/dvdrecord1.html](http://linuxcommand.org/man_pages/dvdrecord1.html)
  
I like this better, because I can create an iso file first.  Then burn it to a disk. Growisofs just lets me burn it straight to a disk.

With mkisofs, I can add files to the iso any time I want.

1.) Mount the .iso file.
2.) Copy the contents to a new directory.
3.) Add any additional files, or directory.
4.) Create a new .iso file.
5.) Burn it to a disk whenever I want to burn it.

 I don't burn videos; therefore, growisofs is not something I would use. This had created a nice iso in my home directory.```
mkisofs -o bashrc.iso /home/user-name/.bashrc
```

---

### Post by honeybear on 2011-07-04
> **dcsoldschool53 said:**
> After thinking about this for a couple days, I know that this will work to copy that file to DVD. I had tried this, and it burned this file```
growisofs -Z /dev/dvd /home/user-namel/Gnome-Panel/Gnome_Panel.xml
```The only problem I had, was that it had burned the file using only 8 characters```
Gnome-Pa.xml
```I know that -dvd-compat is for videos so we don't want to use it in this case. I am not sure about use the force luke.

there are -path
 -path-list
and -J ... but what is difference. It is obscur based on manpage.

UTF-8 could be also improatn

---

### Post by honeybear on 2011-07-04
> **dcsoldschool53 said:**
> I like this better, because I can create an iso file first.  Then burn it to a disk. Growisofs just lets me burn it straight to a disk.

With mkisofs, I can add files to the iso any time I want.

1.) Mount the .iso file.
2.) Copy the contents to a new directory.
3.) Add any additional files, or directory.
4.) Create a new .iso file.
5.) Burn it to a disk whenever I want to burn it.

 I don't burn videos; therefore, growisofs is not something I would use. This had created a nice iso in my home directory.```
mkisofs -o bashrc.iso /home/user-name/.bashrc
```

it will make an ISO with only the .bashrc (1 file only) and not the content of files that may be contained into the cat .bashrc... 

```
mkisofs -o myiso.iso < `cat mylistoffiles.txt`
```  does not work
/home/user-name/.bashrc

---

### Post by dcsoldschool53 on 2011-07-04
The user-name is the name of your home directory on your computer. For instance, my name is dcsoldschool53, and my home dicectory would look like this```
/home/dcsoldschool53/.bashrc
```You would have to use your home user-name to make it work.
```
ls -l /home
```You will see your user-name. I, on the other hand, have two user-names on this pc, and five on one of the other computers.

---

### Post by dcsoldschool53 on 2011-07-04
-R -J are the Joliet and Rock-Ridge  extensions on a DVD, you will use them to burn multi-session to the disk. So that other computer can see what is on the disk besides a Computer with Ubuntu on it. I think I said that right. Now the way I used it, I was doing it for Ubuntu only...on my computer

[quote=honeybear]there are -path
 -path-list[/quote]
What do you mean? Never mind, I had found the info under genisoimage manpage

---

### Post by dcsoldschool53 on 2011-07-04
So, this did not work for you honeybear```
mkisofs -o bashrc.iso /home/xeratox/.bashrc
```That is strange. Is xeratox your user-name in your home folder?

---

### Post by honeybear on 2011-07-05
> **dcsoldschool53 said:**
> So, this did not work for you honeybear```
mkisofs -o bashrc.iso /home/xeratox/.bashrc
```That is strange. Is xeratox your user-name in your home folder?

Yes but I would have liked to burn a list of file, and not the .bashrc file only... 

there are two user on this machine xeratorx and rantalox.

I hope the discussion goes in the same direction... 

Best regards

---

### Post by dcsoldschool53 on 2011-07-06
This puts the .iso file in my downloads folder.```
mkisofs -o /home/dcsoldschool53/Downloads/Misu.iso /home/dcsoldschool53l/Icons /home/dcsoldschool53/*.txt /home/dcsoldschool53/HTML
```It copies the contents of my Icons, and HTML folder. It also copies every text file that I have in my home directory. IT DOES NOT PUT THE NAME OF THE ICONS, OR HTML FOLDER IN THE ISO, JUST THE CONTENTS.
you also can do it this way. ```
mkisofs -o ~/Downloads/Misu.iso ~/Icons ~/*.txt ~/HTML
```it all  works in the same way.```
mkisofs -o Misu.iso ~/Icons/Download/default.png ~/Documents/*.txt ~/Music/*.ogg
```however you want to do it.

---

### Post by dcsoldschool53 on 2011-07-06
I am in the administrator account, and I am copying stuff from my account and the user's account too. By using the chmod command.```
mkisofs -o ~/ISO/Misu.iso ~/bin ~/Pictures /home/DC44/PDF
```I have given the administrator privileges to copy the user's PDF file.

As with mkisofs, in growisofs, you should be able to do the same things too.

---

### Post by Perkins on 2011-07-06
If you don't want to create a temporary iso file, then create a directory to use as your DVD root directory and link the files you want into it with ln.  Then burn the directory with growisofs.

---

