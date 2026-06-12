---
title: "Trying to get Music file on Windows to be read by default on ubuntu"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by theadictspunk on 2010-01-08
I am trying to get my 4gig music folder on my windows desktop to be played by default by ubuntu. I use the music player that came with it. I can load the IBMPreload that i have as my windows drive and play the music. However, everytime that I restart my computer I have to re-import the folder into my music player.
 
I am guessing that this is because it needs my password (probably for root access?) to load music from another drive. But i would really like it to be indexed once and thats it. I know taht i can just copy the folder onto my ubuntu drive but i got ubuntu to try to make things easier and that would just take up another 4gigs of space.
 
help??

---

### Post by theadictspunk on 2010-01-08
Oh yeah, i am using rythmbox. Amarok wouldnt even mount the music on my IBMPRELOAD drive :/ let alone keep it on there after i reboot

---

### Post by Methuselah on 2010-01-08
What is this IBMPreload?
Is that a stupid question...lol?
I don't know if it is something important to the problem you're trying to solve or just a peripheral detail.

Would automounting the drive at boot solve your problem?
If so, you need to create a mountpoint for it:
eg.
**mkdir /media/mymusic**

Then edit /etc/fstab with the information on which partition you want to automount.
Here is a resource on fstab:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by michy99 on 2010-01-08
If it were me, I would create a NTFS partition for all files that I wanted to share between Ubuntu and Windows and have it automatically mount at boot.

---

### Post by theadictspunk on 2010-01-08
IBMPRELOAD is just what the linux system named my windows drive haha.
 
If i create another partition wouldnt it be the same thing? I would have to still load that folder onto my music player everytime i reboot my computer because it is on another drive?
 
If I automount the drive I wont have to input my password when i login to get on it?

---

### Post by Sef on 2010-01-08
>  If I automount the drive I wont have to input my password when i login to get on it?

That's automatic log-in.  System >  Administration > Log in Screen (for karmic)

---

### Post by michy99 on 2010-01-08
Automounting should take care of that. Check out this page:

[http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14](http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14)

---

### Post by oldsoundguy on 2010-01-08
try setting up your networking .. make the files available on the network ON the Windows machine.

Works for me (and I use Amarok.)

---

### Post by theadictspunk on 2010-01-09
I made a network and made the folder with my music (which was on my desktop) available to that network. It still did the same thing because I had to first lunch my windows drive to get to that shared folder. 

Unless you meant that i should share my whole c drive...

I am going to try seeing if letting it auto mount will work...

thanks guys!

---

### Post by theadictspunk on 2010-01-09
Awesome. Automounting solved the trick. thank you! 

Should I change the thread to [solve] or somehting somehow?

---

### Post by theadictspunk on 2010-01-09
Amarok will not recognize my IBMPRELOAD file AT ALL!

everytime i start amarok it asks me to inpout the kde wallet password. it always says "the name org.kde.kwalletd was not provided by any .service files"

---

### Post by theozzlives on 2010-01-09
Is the mount point named IBMPRELOAD, and did you mount it in your fstab as mentioned above?

---

### Post by theadictspunk on 2010-01-09
it is called IBM_PRELOAD

I didnt do the fstab thing. I only did the automount below it... should i also do the fstab to the same drive?

---

### Post by AlexandreP on 2010-01-09
> **theadictspunk said:**
> I didnt do the fstab thing. I only did the automount below it... should i also do the fstab to the same drive?
You should put a mounting instruction in *fstab*. I guess that would be the easiest solution to solve your problem. Your Windows partition will be mounted automatically every time you boot Ubuntu, and you won't need to provide your password in order for the partition to be mounted.

First, find the peripheral identifier attributed to your Windows partition, if you don't already know it. Use *ls -l /dev/disk/by-label/* to find it. For example :
```
administrator@mycomputer:~$ ls -l /dev/disk/by-label/
total 0
lrwxrwxrwx 1 root root  10 2010-01-09 16:34 SysWindows -> ../../sda2
lrwxrwxrwx 1 root root  10 2010-01-09 16:34 Ubuntu -> ../../sda5
```
In this example, I know the Windows partition is called *SysWindows*, and this command tells me its identifier is */dev/sda2*.

Then, create a new mountpoint for your partition (i.e */media/WindowsDrive*), as */media/IBM_PRELOAD* is probably dynamically created when using Nautilus to access your partition.
```
administrator@mycomputer:~$ sudo mkdir /media/WindowsDrive
```

Edit */etc/fstab* as an administrator :
```
administrator@mycomputer:~$ gksudo gedit /etc/fstab
     or
administrator@mycomputer:~$ sudo kate /etc/fstab
```
At the end of this file, add this new instruction:
```
/dev/sda2     /media/WindowsDrive     ntfs     auto,umask=000     0     0
```
Of course, change the partition identifier and the mountpoint with yours. Save the file, and restart your computer in order the check if this worked correctly (i.e. you can access your Windows drive from */media/WindowsDrive/* just after Ubuntu is loaded).

---

### Post by theadictspunk on 2010-01-12
> **AlexandreP said:**
> You should put a mounting instruction in *fstab*. I guess that would be the easiest solution to solve your problem. Your Windows partition will be mounted automatically every time you boot Ubuntu, and you won't need to provide your password in order for the partition to be mounted.
 

 
sorry if i'm not understanding something... when i did the other automount... that seemed to solve that problem. Now when i log in, my c: drive loads and is displayed on my desktop automatically with no password request. 
 
Are you saying that I should still do the fstab thing? or is it a problem with my amarok??

---

