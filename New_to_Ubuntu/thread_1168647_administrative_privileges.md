---
title: "administrative privileges"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by augie2051 on 2009-05-24
I'm trying to run KDE Partition manger and it says i dont have administrative privileges.  How to i get such privileges.  Im on my own computer and the only user>

---

### Post by Didius Falco on 2009-05-24
Did you run it using ```
sudo appname
```?

---

### Post by augie2051 on 2009-05-24
no i just opened it using my applications tab and then systems tool.  Do i need to run it from the terminal?

---

### Post by Didius Falco on 2009-05-24
> **augie2051 said:**
> no i just opened it using my applications tab and then systems tool.  Do i need to run it from the terminal?

Not necessarily, but it should ask for your password when you open it - at least Gparted does when I open it in Ubuntu.

Open a Konsole and type ```
groups
``` and see if you are in the "admin" group.

If you are, you should have administration rights. 

What's the name of the partitioner you are using?

Regards,

Didius

---

### Post by Kareeser on 2009-05-24
Please be advised, for graphical application, you run the command in terminal with "gksudo"

---

### Post by Didius Falco on 2009-05-24
> **Kareeser said:**
> Please be advised, for graphical application, you run the command in terminal with "gksudo"

+1 to that - right now I'm just trying to figure out where/how he tried to start it, and why it didn't ask for a password.

Gparted won't run w/o one...

Regards,

Didius

---

### Post by augie2051 on 2009-05-24
augie adm dialout cdrom plugdev lpadmin admin sambashare

This is the ouput from "groups"  I am augie soo i assume i am.

---

### Post by augie2051 on 2009-05-24
KDE partition manager

---

### Post by Didius Falco on 2009-05-24
Hmmm, It should ask you for a password when you start it - I'm not really familiar with Kubuntu - let me take a look around and see what I can find out.

Meanwhile, maybe someone that uses Kubuntu will come in and answer this...

Regards,

Didius

---

### Post by augie2051 on 2009-05-24
I think that may be the problem im nut using kubuntu!  Im using ubuntu.  I just downloaded the only application i saw for creating partitions which should i be using?

---

### Post by augie2051 on 2009-05-24
I want to partition my hard drive and format the partition in NFTS

---

### Post by Didius Falco on 2009-05-24
I just found a post from the author in which he said:

> It does ask for your password via kdesudo when using a KDE desktop. If you're trying to run this from a GNOME application menu, that might not work, because GNOME probably doesn't honor the setting to ask for authentication.[http://ubuntuforums.org/showthread.php?t=1150020](http://ubuntuforums.org/showthread.php?t=1150020)

Personally, I'd recommend gparted - it's in the repository or you can install it from a Terminal with the command ```
sudo apt-get install gparted
```
After it installs, you'll find it at **System/Administration/Partition Editor**

Regards,

Didius

PS If you are just creating a new partition out of free space, it'll work just fine, but it won't work on a mounted partition, and if you are going to do anything to your / (Ubuntu) partition, you should boot into the Live CD to do it.

---

### Post by augie2051 on 2009-05-24
Didus,
thanks for your help ii will try that.

---

### Post by augie2051 on 2009-05-24
I've installed this partition manger but the option for "new" under the partition tab is not highlighted.  are there man pages or instructions somewhere i can access for a tutorial?

---

### Post by augie2051 on 2009-05-24
> **Didius Falco said:**
> I just found a post from the author in which he said:

[http://ubuntuforums.org/showthread.php?t=1150020](http://ubuntuforums.org/showthread.php?t=1150020)

Personally, I'd recommend gparted - it's in the repository or you can install it from a Terminal with the command ```
sudo apt-get install gparted
```
After it installs, you'll find it at **System/Administration/Partition Editor**

Regards,

Didius

PS If you are just creating a new partition out of free space, it'll work just fine, but it won't work on a mounted partition, and if you are going to do anything to your / (Ubuntu) partition, you should boot into the Live CD to do it.

by the way i just want to partition free space maybe 20 g

---

### Post by Didius Falco on 2009-05-24
My pleasure!

Regards,

Didius

---

### Post by augie2051 on 2009-05-24
it seems i  dont have access to any option "resize" "shrink" "new" "delete"  how can i get access to these options?

---

### Post by GOfree on 2009-05-24
It sound like your hard drive is full and all your partitions are mounted.

You won't be able to resize partitions that you are currently using.

If you get the GParted Live cd, then you can run the partition editor without mounting your partitions, and will then be able to resize them.

You can download the cd at: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) .

---

### Post by michy99 on 2009-05-24
Can you show us a screenshot of gparted?

---

### Post by Didius Falco on 2009-05-24
A screenshot would be nice. You don't have to download the Gparted Live CD if you have a Ubuntu Live CD - the Ubuntu one will already have Gparted on it.

Don't get me wrong, the Gparted CD is nice to have around - I have a copy myself - but it's not a neccessity if you have a Ubuntu CD.

Regards,

Didius

---

### Post by GOfree on 2009-05-24
Ok, good point!

Use either a GParted Live or Ubuntu Live cd.

There are lots of screenshots on Google Images. :)

---

### Post by Roger Browne on 2009-11-28
[COLOR=Blue]> **Didius Falco said:**
> I just found a post from the author in which he said:

[http://ubuntuforums.org/showthread.php?t=1150020](http://ubuntuforums.org/showthread.php?t=1150020)

Personally, I'd recommend gparted - it's in the repository or you can install it from a Terminal with the command ```
sudo apt-get install gparted
```After it installs, you'll find it at **System/Administration/Partition Editor**

Regards,

Didius

PS If you are just creating a new partition out of free space, it'll work just fine, but it won't work on a mounted partition, and if you are going to do anything to your / (Ubuntu) partition, you should boot into the Live CD to do it.[/COLOR]      

[SIZE=2]I have had the same problem.   I found that the gparted program looks like it will work just fine.   Thanks to you both - for asking the right question and giving the right  answer[/SIZE].

---

