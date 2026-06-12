---
title: "ubuntu to ubuntu filesharing"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by dbowlin17 on 2010-11-11
is there any way i can share files from my ubuntu desktop to my laptop over wireless conection?

---

### Post by spcwingo on 2010-11-11
You could install samba.  With samba you will also be able to share with others who are running other operating systems (samba is cross platform).  To install it just issue this command in a terminal.

```
sudo apt-get install samba smbfs
```

---

### Post by sandyd on 2010-11-11
> **dbowlin17 said:**
> is there any way i can share files from my ubuntu desktop to my laptop over wireless conection?

yes. that would require ad-hoc which is built into ubuntu.

right click on the network manager icon and look for "create network" or something close to it. I know its there, but I havent used gnome in a long time...

---

### Post by dbowlin17 on 2010-11-11
hey so both the computers have samba installed. when i go to click on "tim-desktop" (computer i wanna get files from) it says it is opening it, but never does and eventually says it couldn't retrieve lists from server or something like that...

---

### Post by Easy Limits on 2010-11-11
You could use Giver.  It's in the Software Center.

---

### Post by A_M_S on 2010-11-11
To configure samba try this:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by kroq-gar78 on 2010-11-11
you can also use openssh
```
sudo apt-get install openssh-server
```

---

### Post by mastablasta on 2010-11-12
wow so many complications.... 
 
why not just go to your desktop (or whereever you want to share files from) open the nautilus (file manager), right-click folder you want to share, select propperties and enable sharing for the folder. then go to your netbook and go to places->network and select your desktop computer from the list.
 
it will ask for password and username and after some time it will be opening the computer (might take a while) and then the shared folder from desktop will pop on your netbook. simple. and preety much just like you would do it in Windows. if anything needs to be installed (such as samba) it will be.

---

### Post by dbowlin17 on 2010-11-12
> **mastablasta said:**
> wow so many complications.... 
 
why not just go to your desktop (or whereever you want to share files from) open the nautilus (file manager), right-click folder you want to share, select propperties and enable sharing for the folder. then go to your netbook and go to places->network and select your desktop computer from the list.
 
it will ask for password and username and after some time it will be opening the computer (might take a while) and then the shared folder from desktop will pop on your netbook. simple. and preety much just like you would do it in Windows. if anything needs to be installed (such as samba) it will be.

thats what i have tried. and it wont pull up the list of folders that are being shared...

---

### Post by dbowlin17 on 2010-11-12
I have been able to, with both of the computers i am trying to use, been able to share files and folders without problems to a windows computer I also have. However, when i try to share between ubuntu computers, it says "unable to mount location. unable to get share list from server." whats up? i tried using giver, but it only worked when transferring files. this is bad considering i have 1700 music files i want on my laptop. anyone have any advice???

---

### Post by dbowlin17 on 2010-11-12
update- when i go to share the folder, it lets me click share. then when i go back to it, it does not say its shared. but when i go into my computer via the network area, it pulls up some shared folders... how do i fix this? same thing happens on the laptop too......

---

### Post by tahitiwibble on 2010-11-12
> **kroq-gar78 said:**
> you can also use openssh
```
sudo apt-get install openssh-server
```

ssh has always worked beautifully for me, I keep going back to [this link]("http://ubuntuforums.org/showpost.php?p=4956300&postcount=2") all the time when needed :)

---

### Post by onaridge on 2010-11-12
I had the same problem until I did this:

type: gksudo nautilus and then navigate to your music folder. Apply the permissions and sharing there. This gives you root priveleges.

---

### Post by rcayea on 2010-11-12
I took the advice from a post somewhere on these forums and went to Go-->Location in Nautilus and then just typed in smb://serveripaddress/share

That worked then I bookmarked it and it is always there.

---

### Post by dbowlin17 on 2010-11-12
ALRIGHT! i have been successful using SSH! thank you!!!!!!!!

---

### Post by rcayea on 2010-11-14
Please mark this as solved as I know I was looking for a solution to this question a while ago and it would have helped to find SOLVED threads to help with the issue. I'm glad you found a solution.

---

