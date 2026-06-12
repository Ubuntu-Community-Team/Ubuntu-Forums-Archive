---
title: "errors running programs in wine"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by theoak on 2009-09-16
hi so ive been trying to install world of warcraft from the cd dvd discs and i get an access denied. i know that due to the installer.exe file is hidden. and when i tryed to follow the howto forums and typing the commands in the terminal it doesnt work. so then i tryed downloading wow from the internet... got it and now when it trys to patch i get a error window that says "the program installer.exe has encountered a serious problem and needs to close. we are sorry for the inconvenience." and that also happens to my other programs under wine like windows media player wont open or install as well as explore. ive been trying for weeks to get wow to run ive had a friend try and help me over the phone, im so frustrated if anyone can help plz... im so close to just going back to windows.

---

### Post by AlexenderReez on 2009-09-16
first of all relax  and take a deep breath :D

we will walk down through each problem ...world of warcraft should not be problem ,as logn as you have graphic configure corectly .

please refer here --> 
[http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine](http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine)

when you enter command and it doesn't work...dont make your own assumption , please ask... you might get fooled by your own assumption ,when post on forum..please give error log, people able to help you then.

for other applications , please find replacement , what is meaning of using linux then if you still expect all applications depends on wine (windows application)??

good video player is Mplayer , VLC and music player i still prefer rythmbox or amarok .

neverless , [www.google.com](www.google.com) is our best friend :D

---

### Post by theoak on 2009-09-16
ok so ive tried following the installer howto link you gave me. when it asked me to type this command in with the location of my cd rom drive which i did and it told me it was unable to find the location, i may have the wrong location. here is tyhe command it gave me.
wine /media/WoWDisc1/Installer.exe

I may have the wrong location what i switch the media with was this location.
/media/cdrom0

then i tried the next option of installation, which was to copy the files into a directory and i was unable to do that because it told me i do not have permission to do so.

im not sure if im typing the commands wrong or have the wrong cd rom location.
plz help. im going to try the download from blizzard, but if i can do it from the cds i would rather do that.

thnx for helping.

---

### Post by 3rdalbum on 2009-09-16
> **theoak said:**
> then i tried the next option of installation, which was to copy the files into a directory and i was unable to do that because it told me i do not have permission to do so.

If you want to delete, modify or add files outside your home directory, you need to become root.

You can either do this by putting "sudo" before the terminal command you want to run, or by pressing Alt-F2 and typing:

```
gksudo nautilus
```

which opens up a file browser as root.

---

### Post by theoak on 2009-09-16
ahahahahhaha awesome ok now that im copying these files over im going to try and finish following that installer howto and will keep posted on how its working.
                                    
                               THANK YOU!

---

### Post by AlexenderReez on 2009-09-16
when you open the mounted cd in folder , just click a button beside name of the directory (beside like (media)(namemightproblem)(WoWDisc1)) ..so it wil change to words instead of button , copy those words (/media'namemightproblem/WoWDisc1/) and open terminal 


[HTML]cd <paste those copy words>
wine Installer.exe
[/HTML]
remember ..it is case sensitive

---

### Post by AlexenderReez on 2009-09-16
> **3rdalbum said:**
> if you want to delete, modify or add files outside your home directory, you need to become root.

You can either do this by putting "sudo" before the terminal command you want to run, or by pressing alt-f2 and typing:

```
gksudo nautilus
```

which opens up a file browser as root.

**please don't ever use [color="red"]sudo[/color] , unless the guide state to do so, it might corrupt your software and system as well**

---

### Post by theoak on 2009-09-16
ok so now the installer opened and installed and as it was patching i got an error windowed that said the program ran into a serious problem and had to quit. any answers on why it ran into an error?

---

### Post by theozzlives on 2009-09-16
As far as games, wine works fine. Media Player??? Give me a break! Wine is NOT Windows and neither is Linux. If you learn the open source apps made for Linux, you'll have less headaches and relax knowing you have a secure OS free from all the crap people use to bring down Windows.

---

### Post by theoak on 2009-09-16
and when i run this command into my terminal 

cd /root/wow installer1
wine Installer.exe

it tells me 

theo@theo-laptop-ak:~$ cd /root/wow installer1
bash: cd: /root/wow: Permission denied
theo@theo-laptop-ak:~$ wine Installer.exe
wine: could not load L"c:\\windows\\system32\\Installer.exe": Module not found
theo@theo-laptop-ak:~$

what do i do now.

+ now when i try to just run the installer it opens to the games beginning install menu, and when i hit install nothing opens and the the menu disapears.

any answers to what i should do now?

---

### Post by AlexenderReez on 2009-09-17
> **theoak said:**
> and when i run this command into my terminal 

cd /root/wow installer1
wine Installer.exe

it tells me 

theo@theo-laptop-ak:~$ cd /root/wow installer1
bash: cd: /root/wow: Permission denied


+ now when i try to just run the installer it opens to the games beginning install menu, and when i hit install nothing opens and the the menu disapears.

any answers to what i should do now?


i believe that is not folder directory ...please make sure about it...
please type in terminal

> sudo apt-get install nautilus-open-terminal

log out and log in back

go to Installer.exe directory in CD directory ,using mouse right click, open terminal
then just
> wine Installer.exe

**_[COLOR="Red"]OR[/COLOR]_**


```
cd root

ls

cd media

cd <cd name>

wine Installer.exe
```
 



nothing appears mean error/s....and each might differ for each system.. i don't know how you expect people to help if you failed to  give the detail about error..

---

