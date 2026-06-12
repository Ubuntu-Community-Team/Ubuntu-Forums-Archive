---
title: "Cant intall ANY repositories or ANY program at all."
date: 2009-04-16
forum: New to Ubuntu
---

### Post by Novnia on 2009-04-16
[http://img21.imageshack.us/my.php?image=screenshotsynaptic.png](http://img21.imageshack.us/my.php?image=screenshotsynaptic.png)

IT gives me that error whenever i try to install anything at all. It does not matter what.

---

### Post by rucadulu on 2009-04-16
It is looking for the Feisty Fawn repo's. I think Support has ended for feisty and the repo's are no longer available. You should probable download the latest release or the latest LTS (long term support release) and upgrade your system.

---

### Post by presence1960 on 2009-04-16
> **Novnia said:**
> [http://img21.imageshack.us/my.php?image=screenshotsynaptic.png](http://img21.imageshack.us/my.php?image=screenshotsynaptic.png)

IT gives me that error whenever i try to install anything at all. It does not matter what.

what version of ubuntu are you running? your repository sources are for feisty which I believe is no longer supported or is a few days away from being no longer supported. If you have installed Feisty i would suggest you download the .iso image for Hardy 8.04 or Intrepid 8.10 and burn that to a CD and install a current version of Ubuntu. I recommend Hardy because that is a LTS (long term support version) It will still be supported when support for Intrepid is done.

---

### Post by Novnia on 2009-04-16
where would i download an iso of a newer version?
do i HAVE to uninstall feisty or can i run an update tool?
once i have an iso of something better how do i burn it to cd? i cant install anything.

this is so frusterating. thanks for helping though. dont mean to sound ungratful

---

### Post by glennric on 2009-04-16
You do not have to uninstall feisty, but you will have to upgrade to gutsy first, and then to hardy.  Feisty is no longer supported, and support for gutsy is about to end also.

---

### Post by glennric on 2009-04-16
By the way you can download these releases of Ubuntu at [http://releases.ubuntu.com/]("http://releases.ubuntu.com/")

---

### Post by presence1960 on 2009-04-16
> **Novnia said:**
> where would i download an iso of a newer version?
do i HAVE to uninstall feisty or can i run an update tool?
once i have an iso of something better how do i burn it to cd? i cant install anything.

this is so frusterating. thanks for helping though. dont mean to sound ungratful

you can download the .iso here: [http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)

There are a number of programs you can use to burn the .iso image to a CD. I used Nero on my Windows when I did it. There are a few other programs you can download, but I am not familiar with them. Maybe someone else can suggest one for you. This is of course assuming you didn't wipe your windows when you installed feisty. Or you can download the .iso from feisty if you can get online and use brasero to burn it to CD.

My preference would be to do a clean install. That is boot off the Ubuntu Live CD you burn and install from there.

P.S. burn the CD at the lowest possible speed you can select.

---

### Post by Novnia on 2009-04-16
the problem with doing a clean install is i need to burn a cd

to burn a cd i need to install a burning program

i can install nothing because im on feisty.

catch-22


ps

I wiped my windows when i installed because windows wouldnt boot. BSOD + bad bios checksum. i popped the battery off my mobo to reset the bios and the first thing i did was demolish C: and load it with linux. i got a 250 and a 320 HDs for storage, C is a 80 for just the OS + OS apps.

---

### Post by presence1960 on 2009-04-16
> **Novnia said:**
> the problem with doing a clean install is i need to burn a cd

to burn a cd i need to install a burning program

i can install nothing because im on feisty.

catch-22

I never used feisty, check and see if brasero is included with the default install, it is on hardy.

you can open a terminal or Alt + F2 and type brasero. If it is installed it will open that is the burning software.

Or you can go the upgrade route, but that wouldn't be my preference. Either method will get you hardy 8.04

---

### Post by glennric on 2009-04-16
Try typing
```
gksu "update-manager -c"
```
in a terminal and upgrading that way.
Support for Gutsy ends on Saturday, April 18.  So you should still have time to upgrade to that and then upgrade to Hardy.

---

### Post by Novnia on 2009-04-16
nope. cant find it.


went to [http://www.howtogeek.com/howto/linux/upgra...eisty-to-gutsy/](http://www.howtogeek.com/howto/linux/upgra...eisty-to-gutsy/) to try to do the non clean updateing method,

went to the site, followed the directions, ran

gksu "update-manager -c "

and it opened a window, tried to download 68 files, got the 404 error. it said 7.10 update is avalible on a button, i click it, it tries to download 2 files, does NOT give an error, and then it just sits there.

now what do i do? i had a copy of windows round here, but i cant find it. so im stuck using linux, which ill enjoy once i get it working. arghh

---

### Post by presence1960 on 2009-04-16
> **Novnia said:**
> nope. cant find it.


went to [http://www.howtogeek.com/howto/linux/upgra...eisty-to-gutsy/](http://www.howtogeek.com/howto/linux/upgra...eisty-to-gutsy/) to try to do the non clean updateing method,

went to the site, followed the directions, ran

gksu "update-manager -c "

and it opened a window, tried to download 68 files, got the 404 error. it said 7.10 update is avalible on a button, i click it, it tries to download 2 files, does NOT give an error, and then it just sits there.

now what do i do? i had a copy of windows round here, but i cant find it. so im stuck using linux, which ill enjoy once i get it working. arghh
 Ok no need to panic. If you don't have brasero on your feisty and you can't run an upgrade then you need to get a CD. Is there another computer such as a friend's you can use to burn the Ubuntu CD?

P.S. I am not familiar with Feisty, but I am confident it has a CD burning program by default with it. Maybe someone who used Feisty can help you here.

---

### Post by Novnia on 2009-04-16
id have to wait till sunday or monday to use my friends pc, i could ask my dad, but best case that still leaves me screwed till sat-sun. it dont seem like there is a burning program in feisty that i can find, and i cant install one unless it came default it seems.

---

### Post by rucadulu on 2009-04-16
[B]Feisty Fawn I think came with the nautilus-cd-burner by default.

I am booting the Feisty live cd right now to see what is on it. I will let you know.
[/B]

---

### Post by lavinog on 2009-04-16
feisty came with a cd burner by default most likely nautilus as mentioned above. I know though it was able to burn iso files without needing to install anything.
Download the iso file and see what happens when you double click on it.

---

### Post by Novnia on 2009-04-16
its dloading. 25k a sec, eta 6hrs. 8%. wish it would go quicker.

---

### Post by presence1960 on 2009-04-16
Novnia, rucadulu and lavinog will get you squared away. Now that someone familiar with feisty is on the scene I will go to bed. Have to go to work in the morning. hang in there you will get this running!

---

### Post by garyed on 2009-04-16
I had a similar problem about a week ago & got some help here & it worked for me on Feisty. I'm a little late but if you still want to try it 
you should only need to do two things to be able to install programs on
Feisty:

1 - Edit your /etc/apt/sources.list 
     First make a backup copy of the sources.list file. Then 
   comment out all of the http: lines & insert these lines. 
```
deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse

```
 
2 - Then do: ```
 sudo apt-get update
```

Then you should be able to install programs again.

---

### Post by rucadulu on 2009-04-16
Under Places you have something that says CD/DVD creator this is the drag and drop burner. It is pretty straight forward to use. If you need help let me know.

---

### Post by Novnia on 2009-04-16
> **garyed said:**
> I had a similar problem about a week ago & got some help here & it worked for me on Feisty. I'm a little late but if you still want to try it 
you should only need to do two things to be able to install programs on
Feisty:

1 - Edit your /etc/apt/sources.list 
     First make a backup copy of the sources.list file. Then 
   comment out all of the http: lines & insert these lines. 
```
deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse

```
 
2 - Then do: ```
 sudo apt-get update
```

Then you should be able to install programs again.

whats the syntax for commenting out? 

edit: im blind. its ## aint it. its all over the file when u open as txt
edit2: How do i open the file for editng? if i open as txt it wont let me save, i went to terminal and did su and then my pass to log in as root, then tried again. same thing. says i cant overwrite it

---

### Post by Novnia on 2009-04-17
> **rucadulu said:**
> Under Places you have something that says CD/DVD creator this is the drag and drop burner. It is pretty straight forward to use. If you need help let me know.

/ashamed

one menu over. i feel like a child. lol. cool, once this gets done downloading ill just get rid of feisty and burn a cd.

anyone know of a download that will go quicker than 25k a sec? and ty all for being really helpful. ill ressurect the thread if i have a problem with burning or the same problem on 8.10, btw what is its name?

---

### Post by presence1960 on 2009-04-17
Intrepid Ibex is 8.10.

BTW you are making the right decision by installing a current version.

---

### Post by 3rdalbum on 2009-04-17
You don't use the CD/DVD Creator to burn an ISO to disc - you'll end off with a CD with just one .iso file on it.

You right-click the ISO and choose "Write to Disc" from the contextual menu.

---

### Post by garyed on 2009-04-17
> **Novnia said:**
> ...
How do i open the file for editng? if i open as txt it wont let me save, i went to terminal and did su and then my pass to log in as root, then tried again. same thing. says i cant overwrite it

For future reference in the terminal if you want to open gedit with root priviliges:
```
 gksudo gedit filename 
```
or if you want to use nano:
 ```
 sudo nano filename 
```

---

### Post by Novnia on 2009-04-17
update: My internet sucks and hiccups every few hours, i cant download a new linux unless its via a resumeable download. ive tried 7 times now to get it and it ALWAYS crashes and invalidates the files

any ideas?

---

### Post by Novnia on 2009-04-17
update: My internet sucks and hiccups every few hours, i cant download a new linux unless its via a resumeable download. ive tried 7 times now to get it and it ALWAYS crashes and invalidates the files

any ideas?

---

### Post by presence1960 on 2009-04-17
> **Novnia said:**
> update: My internet sucks and hiccups every few hours, i cant download a new linux unless its via a resumeable download. ive tried 7 times now to get it and it ALWAYS crashes and invalidates the files

any ideas?

It looks like you better use someone else's machine to download the .iso file. Then burn it to disc.

Unfortunately your internet connection will pose a slight problem. If it is that bad how are you going to grab updates after you install Ubuntu? You should get on your ISP and get that straightened out. No matter what OS you use you need a good internet connection to download updates, software etc.

---

### Post by lavinog on 2009-04-18
> **Novnia said:**
> update: My internet sucks and hiccups every few hours, i cant download a new linux unless its via a resumeable download. ive tried 7 times now to get it and it ALWAYS crashes and invalidates the files

any ideas?

You can order a free cd: [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)
or use wget
if the download stops for any reason, wget will resume where it left off
```
wget -c http://mirrors.xmission.com/ubuntu-cd/intrepid/ubuntu-8.10-desktop-i386.iso
```
the '-c' tells wget that if the destination file exists, continue where it ends.
make sure you check the md5sum of the file when it is complete
```
md5sum ubuntu-8.10-desktop-i386.iso
```
it should be 24ea1163ea6c9f5dae77de8c49ee7c03

---

### Post by lavinog on 2009-04-18
What internet connection are you using?

---

