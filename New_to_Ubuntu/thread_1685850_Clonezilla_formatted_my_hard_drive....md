---
title: "Clonezilla formatted my hard drive..."
date: 2011-02-11
forum: New to Ubuntu
---

### Post by throese on 2011-02-11
Simply put, accidentally saved the ISO or w/e Clonezilla uses to my hard drive and it formated it. Gotta re-install the OS and update ALL over again and DL all my programs. Getting really tired of all this. =/ I can't find a backup system that works for me. Remastersys says it's too big to save it as an ISO, using the tar setup sends me to the CLI, and Clonezilla won't save to anything but my hard drive and not a flash drive...please help.

---

### Post by Grenage on 2011-02-11
Ouch.

Where are you storing the archived files, on another local drive? Rsync is an excellent utility; yes, it's CLI, but once you've got it configured, you can schedule it in cron and forget about it.

I have heard good things about sbackup; that's GUI-based and in the main repository.

---

### Post by thefasterblueone on 2011-02-11
You can also try Déjà Dup located in Ubuntu Software Center. I use it to backup to an external harddrive.
You can choose where to backup to, so i'm preety sure it will backup to your flash drive like you are asking.

[http://www.makeuseof.com/tag/dj-dup-perfect-linux-backup-software/]("http://www.makeuseof.com/tag/dj-dup-perfect-linux-backup-software/")

---

### Post by kaldor on 2011-02-11
All I ever do is grab my 320 gb external and copy/paste the entire ~/ directory. I do this every few weeks and always leave the last two backups on it.

I just reinstall the programs as I need them.

---

### Post by Cpierce on 2011-02-11
CloneZilla works well for me. Just remember that the first time it asks you about drives, always select the USB/sdb drive. Doesn't matter if you are saving or restoring, always select the USB drive first. You will select your internal hard drive/sda last in the process.

If it helps, I did the same thing the first time I used Clonezilla and had to re-install everything. I learned my lesson the hard way. But from then on, it has worked wonderfully.

---

### Post by Linyx on 2011-02-11
Ok, So this is not about the Cloning Partition, But i Use it to save all my Packages Pre-installed and it is very Easy to install all the Packages already saved...

I use this Method when i do a fresh Install of my OS, so here it is...

```
$ sudo apt-get install dpkg-repack fakeroot
$ mkdir ~/dpkg-repack; cd ~/dpkg-repack
$ fakeroot -u dpkg-repack `dpkg --get-selections | grep install | cut -f1`
```> This will make a directory name = "dpkg-repack" in your home-directory,Which will Contain all packages which you have on your system.

To install these packages on another PC or Reinstall these packages after a fresh install, all you have to go to this directory and use:-

sudo dpkg -i *.debThats all,it will automatically install all the packages which you have already saved.... I think it better then Remaster-Sys-backup.....

---

### Post by jnguyen on 2011-02-11
> **Linyx said:**
> Ok, So this is not about the Cloning Partition, But i Use it to save all my Packages Pre-installed and it is very Easy to install all the Packages already saved...

I use this Method when i do a fresh Install of my OS, so here it is...

```
$ sudo apt-get install dpkg-repack fakeroot
$ mkdir ~/dpkg-repack; cd ~/dpkg-repack
$ fakeroot -u dpkg-repack `dpkg --get-selections | grep install | cut -f1`
```Thats all,it will automatically install all the packages which you have already saved.... I think it better then Remaster-Sys-backup.....

Thanks Linyx. This is a great help & save me a lot of time.

jvn

---

### Post by Rasa1111 on 2011-02-11
> **thefasterblueone said:**
> You can also try Déjà Dup located in Ubuntu Software Center. I use it to backup to an external harddrive.
You can choose where to backup to, so i'm preety sure it will backup to your flash drive like you are asking.

[http://www.makeuseof.com/tag/dj-dup-perfect-linux-backup-software/]("http://www.makeuseof.com/tag/dj-dup-perfect-linux-backup-software/")

+1.
 Deja Dup always works great for me. 

> Originally Posted by Linyx  
Ok, So this is not about the Cloning Partition, But i Use it to save all my Packages Pre-installed and it is very Easy to install all the Packages already saved...

I use this Method when i do a fresh Install of my OS, so here it is...

Code:
$ sudo apt-get install dpkg-repack fakeroot
$ mkdir ~/dpkg-repack; cd ~/dpkg-repack
$ fakeroot -u dpkg-repack `dpkg --get-selections | grep install | cut -f1`
Thats all,it will automatically install all the packages which you have already saved.... I think it better then Remaster-Sys-backup.....


wow niice! Thanks Linyx!

> Simply put, accidentally saved the ISO or w/e Clonezilla uses to my hard drive and it formated it. Gotta re-install the OS and update ALL over again and DL all my programs. Getting really tired of all this. =

So, Simply put..
 *you* made the accident and formatted the drive yourself. 
"*it*" didnt format it, *you* did though. Accident or not.

---

### Post by AndyM3 on 2011-02-11
Not sure if this is what you're looking for right now, but [here]("https://help.ubuntu.com/community/DataRecovery") is a nice guide on how to recover lost data from an HDD using Ubuntu.

---

### Post by uRock on 2011-02-11
I regularly burn files to disk and keep one happy script together that will install everything I need just in case I have to reinstall.

---

### Post by throese on 2011-02-11
Thanks everyone.

Ran1111: It wouldn't let me CHOOSE to save the file to my 14.9 GB flash drive. Whenever I tried, it'd give me this red error thing saying drive not found or something like that. So in a sense, yes it is my fault, but at the same time it's the program's fault too for not recognizing my flash drive even though it detected it and said it was there as an option to choose from.

---

