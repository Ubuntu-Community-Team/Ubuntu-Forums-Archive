---
title: "Totally newbie to Ubuntn"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by Joebhoy on 2010-09-22
Atfer majoe troublw with spyware I thought I'd try Ubuntu, must say it's nice just have a few questions.
 
I ran Dban to totally wipe my harddrive it took 10 hours while all this happened I went to bed. Came down the screen was black so I restarted and installed Ubuntu.
 
I have a file called lost+found there's no way that could be my files from windows 7? The file it says 248GB's free. I take it it's nearly 50GB's in there as my HD is 300GB or else the file is 248GB's.
 
What is in this file?
 
GA-MS5LI-S4
AMD X2 6000+
4GIG DDR2

---

### Post by migs73 on 2010-09-22
the lost+found folder has any broken files in it found during disk checks, assuming you Dban has not 100% wiped your drive but has left some remnants of files behind which have been picked up by the disk check. I assume you are asking what is in it as you cannot open it (you can only do so with root priviledges). If there is 50GB of stuff in there you might want to get rid of the files, I am sure there are a few how to's around on the subject

BTW to open the folder, right click on it and select open as administrator.

---

### Post by Joebhoy on 2010-09-22
Thanks for the reply. Yes I cant get into as it says unreadable there's also a file called root which I cant get into althought I'm sure that's part of the Ubuntu.
 
I only ran Dban because I wanted the HD everything deleted. I've had to install windows 3 times over this bloody thing.
 
If I was to delete I'm sure it would start spreading again and infect my whole system again.

---

### Post by migs73 on 2010-09-22
Nothing you delete will cause any 'infections'. The files detected are probably 'broken' not malicious. They will have been partially destroyed by your disk being flattened by Dban. As the disk check has picked up these files as being broken it has put them in a safe place for you to check. If you do not want these files anymore (you have just flattened your HDD so I am guessing 'no') just delete them. FYI Spyware and Viruses are not currently a problem on Linux (ubuntu) systems.

---

### Post by SlugSlug on 2010-09-22
in terminal

gksudo nautilus


and remove the lost-found folder

---

### Post by Diametric on 2010-09-22
Welcome to Ubuntu!  If you're new to Ubuntu/Linux, spend some time reading through this site - TONS of information.  Also, don't forget, at some point, begin learning the command line.  Very powerful and most people will reference it when you ask for help.

---

### Post by sanderd17 on 2010-09-22
@migs73: I don't think that you can open a directory as root by right-clicking in the normal ubuntu configuration.

@Joebhoy: To open the directory, press ALT+F2 and type
```

gksudo nautilus

```
navigate to the lost+found directory and delete everything.

FYI: gk stands for gnome, the graphical interface used in ubuntu, if you use kubuntu you should type kdesudo. The "sudo" stands for "superuser do". "Superuser" and "root" are synonims, it's the user which has all the rights over the system (can read and modify ALL files, install system wide programs ...). For your security, Ubuntu has deactivated the superuser account by default but you can become "superuser" for one action by using a "sudo" command like gksudo, kdesudo or just sudo if you use the terminal. You have to give your password to become superuser for a moment.

nautilus is the name of the file manager. So the command says you open the file manager with superuser rights.

---

### Post by migs73 on 2010-09-22
> **SlugSlug said:**
> in terminal

gksudo nautilus


and remove the lost-found folder

+1 to that. BE VERY CAREFUL the gksudo command gives you root priviledges, enabling you to do anything. While the key symbol is on your top panel you still have root priviledges, so make sure to shut down nautilus (your file browser) when you are finished. 
This will drop the root priviledge.

---

### Post by ghostborg on 2010-09-22
[http://perfectbuntu.category5.tv/]("http://perfectbuntu.category5.tv/")

Check out this script by Robbie Ferguson of Category5.tv

It will help you setup your Ubuntu desktop, like being able to play Encrypted DVD's , music codecs and other software.

---

### Post by migs73 on 2010-09-22
> **sanderd17 said:**
> @migs73: I don't think that you can open a directory as root in the normal ubuntu configuration.

@Joebhoy: To open the directory, press ALT+F2 and type
```

gksudo nautilus

```
navigate to the lost+found directory and delete everything.

FYI: gk stands for gnome, the graphical interface used in ubuntu, if you use kubuntu you should type ksudo. The "sudo" stands for "superuser do". "Superuser" and "root" are synonims, it's the user which has all the rights over the system (can read and modify ALL files, install system wide programs ...). For your security, Ubuntu has deactivated the superuser account by default but you can become "superuser" for one action by using a "sudo" command like gksudo, ksudo or just sudo if you use the terminal. You have to give your password to become superuser for a moment.

nautilus is the name of the file manager. So the command says you open the file manager with superuser rights.

Beat me to it. Yes, you can open the folder using the 'open as administrator', I just did it. I don't think you can alter the files in the folder, but can't check as my folder is empty!!

---

### Post by coffeecat on 2010-09-22
> **SlugSlug said:**
> in terminal

gksudo nautilus


and remove the lost-found folder

@joebhoy, **please don't so that**. The lost+found folder is normal.

Dban did not produce that folder. Dban would have left you with a totally scrambled HD data-wise. In fact you needn't have used Dban. The Ubuntu installer would simply have reformatted the whole drive for you if necessary. The lost+found folder is normal on all Linux filesystems. It's in your root partition filesystem and is needed. Leave it alone.

Oh - did I say not to delete the lost+found folder? :wink:

**Edit:**

> **Joebhoy said:**
> I have a file called lost+found there's no way  that could be my files from windows 7? The file it says 248GB's free. I  take it it's nearly 50GB's in there as my HD is 300GB or else the file  is 248GB's.

Your 300GB (gigabyte)  HD is, in fact, only 279GiB (gibibytes). That 248 is GiB, not GB. The remaining difference of 31 GiB can probably be accounted for by a separate swap partition and the journal of you ext4 root partition filesystem, which can take up a lot of space. Do have a look in lost+found, but don't delete the folder.

---

### Post by SlugSlug on 2010-09-22
lost+found gets recreated after every disk check

---

### Post by coffeecat on 2010-09-22
> **SlugSlug said:**
> lost+found gets recreated after every disk check

That's somewhat beside the point. Would it not be better to explain to a newbie what is going on rather than teaching them things that a newbie might accidentally use to do serious damage to their system? Shouldn't we  investigate whether or not there is something in lost+found before blindly deleting it?

Answers: yes - yes.

---

### Post by SlugSlug on 2010-09-22
> **coffeecat said:**
> That's somewhat beside the point. Would it not be better to explain to a newbie what is going on rather than teaching them things that a newbie might accidentally use to do serious damage to their system? Shouldn't we  investigate whether or not there is something in lost+found before blindly deleting it?

Answers: yes - yes.

was this a fresh install after the hard drive had been dbaned?

did the user wish to completely wipe everything form the old system the had in place?

did chkdsk pick up on lost files from dban and attempt to recover 50GB's?

answer: yes - yes - yes

---

### Post by Joebhoy on 2010-09-22
Dban was going fine when I went to bed didn't pick up any errors.
 
Just few more questions if ye dont mind. That lost folder even though I'm logged in as Admin I stall can't open it. I'm unable to get into network connections come up Unable to mount location.
 
Is it normal for 50 processes to be running after fresh install and all of then have sleeping beside them.

---

### Post by migs73 on 2010-09-22
> **Joebhoy said:**
> 
 
Is it normal for 50 processes to be running after fresh install and all of then have sleeping beside them.

Yes, I have over 100 but not on a fresh install.

I only wanted you to open the folder so you could see if there was anything worth recovering. Seeing as how you were flattening the disk any way, probably best to just delete it (using the gksudo nautilus method above) and as has been said the disk check will create a new one when required. 
Dban will not have shown any errors, it did what it should, disk check has just found some remnants of what Dban has left behind and decided they may be corrupted files you might like to keep, so has kept them for you.

---

### Post by nothingspecial on 2010-09-22
Stop worrying

Forget the lost and found "folder". Delete it or don`t, it doesn`t matter.

Don`t worry about the processes, this is normal.

Start enjoying the freedom of Ubuntu

---

### Post by migs73 on 2010-09-22
> **nothingspecial said:**
> Stop worrying

Forget the lost and found "folder". Delete it or don`t, it doesn`t matter.

Don`t worry about the processes, this is normal.

Start enjoying the freedom of Ubuntu

+1 but if it's using 50GB I'd delete it!

---

### Post by vegetarianshrimp on 2010-09-22
Welcome to Ubuntu! May I suggest this site?: [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

