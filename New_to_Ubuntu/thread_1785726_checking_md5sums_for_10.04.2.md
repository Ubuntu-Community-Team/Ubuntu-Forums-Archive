---
title: "checking md5sums for 10.04.2"
date: 2011-06-18
forum: New to Ubuntu
---

### Post by RavenBrimstone on 2011-06-18
[SIZE=2]I am trying to check the md5sums on the recent download of 10.04.2 desktop-i386. I was following the guidelines listed as such :[/SIZE]
[SIZE=2][COLOR=black]
[/COLOR][/SIZE]
 _[SIZE=2][COLOR=black]MD5SUM on Linux[/COLOR][/SIZE]_
[SIZE=2]
[/SIZE]
 [SIZE=2]Most Linux distributions come with the md5sum utility so installation  is usually unnecessary. We are going to use the Ubuntu 8.10 LiveCD for  the following example:[/SIZE]
[SIZE=2]
[/SIZE]
 [SIZE=2]Check the iso file[/SIZE]
[SIZE=2]
[/SIZE]
 _[SIZE=2]Manual method[/SIZE]_
[SIZE=2]
[/SIZE]
 [SIZE=2]First open a terminal and go to the correct directory to check a downloaded iso file:[/SIZE]
 [SIZE=2]      cd download_directory[/SIZE]
[SIZE=2]
[/SIZE]
 [SIZE=2]Then run the following command from within the download directory.[/SIZE]
 [SIZE=2]     md5sum ubuntu-[/SIZE][SIZE=2]8.10-desktop-[/SIZE][SIZE=2]i386.iso[/SIZE]
[SIZE=2]
[/SIZE]
 [SIZE=2]md5sum should then print out a single line after calculating the hash:[/SIZE]
 [SIZE=2]      24ea1163e[/SIZE][SIZE=2]a6c9f5dae77de8c[/SIZE][SIZE=2]49ee7c03 ubuntu-[/SIZE][SIZE=2]8.10-desktop-[/SIZE][SIZE=2]i386.iso[/SIZE]
[SIZE=2]
[/SIZE]
 [SIZE=2]Compare the hash (the alphanumeric string on left) that your machine  calculated with the corresponding hash on the UbuntuHashes page.[/SIZE]
[SIZE=2]
[/SIZE]
 [SIZE=2]I cannot seem to find the directory. I find the file in down loads, click properties, and it says /home/nicole/[/SIZE][SIZE=2]downloads. I tried to enter in the command line and it doesn't work. any suggestions. 
[/SIZE]

---

### Post by inameiname on 2011-06-18
Personally I use a handy script called Hash Checker to check all that I want:

[http://gnome-look.org/content/show.php/Hash+Checker?content=129309](http://gnome-look.org/content/show.php/Hash+Checker?content=129309)

It autoinstalls into your ~/.gnome2/nautilus-scripts folder and then its a matter of you right-clicking a file and running it.

So just find the actual file you want scanned to check md5sums for, and you're good. Not sure on the specifics of why you are having trouble finding the file.

---

### Post by Rex Bouwense on 2011-06-18
Remember that there is a difference between Downloads and downloads.  In my case the directory is in Downloads.  Check yours.

---

### Post by inameiname on 2011-06-18
Good point, Rex. For me, I use 'Temp' instead of Downloads. Probably a carryover from using Windows way back when.

---

### Post by RavenBrimstone on 2011-06-18
[SIZE=3]If I were to type in the terminal, how do i specify which directory. The File I want is in Downloads.  The location according to properties states thus:


/home/nicole/Downloads
[/SIZE]

---

### Post by akand074 on 2011-06-18
```
cd ~/Downloads
md5sum ubuntu-10.04.2-desktop-i386.iso
```

you can also just cut/paste it to your home folder, in which case you'll only need to run the second command (assuming that's the proper name of the file, you could always type "md5sum ubuntu-" and press tab and it will complete it.

---

### Post by RavenBrimstone on 2011-06-18
> **inameiname said:**
> Personally I use a handy script called Hash Checker to check all that I want:

[http://gnome-look.org/content/show.php/Hash+Checker?content=129309](http://gnome-look.org/content/show.php/Hash+Checker?content=129309)

It autoinstalls into your ~/.gnome2/nautilus-scripts folder and then its a matter of you right-clicking a file and running it.

So just find the actual file you want scanned to check md5sums for, and you're good. Not sure on the specifics of why you are having trouble finding the file.


I am not sure how to unpack this file. HashCheck-4.0.0.tar.gz

---

### Post by inameiname on 2011-06-18
For Nautilus, a handy little help to 'cd' into a folder is by adding this extensions, by:

sudo apt-get install nautilus-open-terminal

It adds an open-in-terminal option in the right-click context menu so you can simply right click inside the folder where the file is housed, click it, and you will be automatically 'cd'-ed into it. 

Again, just another little shortcut.

---

### Post by inameiname on 2011-06-18
If using Ubuntu, there is already a simple GUI installed to extract it by right-clicking the tar.gz file and choosing extract here. Then you open the folder it creates and click the Setup file inside. Rest is easy. And once installed, again, just right click an item, choose Scripts, and then find the CheckHash one.

If you want to untar it through a terminal command:

cd /home/nicole/Downloads
[FONT=verdana][SIZE=2][COLOR=#000000] tar -xzvf [/COLOR][/SIZE][/FONT]HashCheck-4.0.0.tar.gz

---

### Post by RavenBrimstone on 2011-06-18
Thanx very much to all. I am loyal user of Ubuntu. I started with 9.10 which I still have on my laptop, which is why I need the md5 sum. I have 10.04.2 on The girlfriends desktop. We dated for about a year and her dekstop sat useless in the corner, Window problems. She had ordered re-installation disks from the computer company to no avail. Still window problems. I finally convinced her to let me switch the OS to the almighty Ubuntu. I told her what have you got to lose, the thing doesn't work anyways. 
   
   She agreed, I downloaded,I installed ( although I don't remember having so many issues with the md5 sum). and within 30 - 45 minutes, VOILA ! a pristine working desktop computer instead of a $1500 electronic paper weight. 

    Thanks again everyone for your help. I have started me a notebook so I can hopefully easily answer my own questions. Have a great day all and a good weekend.

---

### Post by inameiname on 2011-06-18
No problem. Good luck bringing her on the Ubuntu side. ;) Definitely a better way than Windows. hehe

A random curiosity, you've upgraded Ubuntu all the way from 9.10 on? Wow.... I'm just used to redoing it all after each Ubuntu version gets released.

---

### Post by dFlyer on 2011-06-18
If you feel your problems are resolved please mark title as SOLVED.

---

