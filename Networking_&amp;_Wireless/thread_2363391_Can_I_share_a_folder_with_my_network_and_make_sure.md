---
title: "Can I share a folder with my network and make sure it can't be altered?"
date: 2017-06-09
forum: Networking &amp; Wireless
---

### Post by Megadoomer on 2017-06-09
Hi everyone,

I'm currently trying to figure out a way to get my music collection from my desktop system (100 GB+ of FLAC files) to my laptop in a way that will allow me to sync the folders on both devices so that I don't have to copy everything again when I get a new CD.

The solution I came up with was to share my desktop's music folder with my home network, so that I can access it like a normal folder on my laptop in my home WiFi and use a software to mirror the folder once in a while (e.g. FreeFileSync).

The only issue that I have with this scenario is that I don't want anyone to alter my desktop's music folder, just because they are on my network. Even the laptop's system doesn't have to alter any files, it just needs to read and copy them.

Is there a way to make sure that a shared folder can under no circumstances be altered in any way when sharing it on the network (and how would I even do that the easiest way with one folder in particular)? :D


Kind regards! :)

---

### Post by siben17 on 2017-06-11
If you have SSH on booth you can do something like this from your laptop :
rsync -e ssh -a -z --delete --stats user@yourdesktopIP:/path/to/files/directory /path/to/destination

---

### Post by Bucky Ball on 2017-06-11
I'd probably use Luckybackup for this, but because I know it. Simple GUI. It is in the repositories (look in whatever package manager you are using or install from terminal).

[Bit more info here]("http://luckybackup.sourceforge.net/features.html") and features down the page. 

The first backup will take ages (probably), but syncing after that will take seconds. I've used it for years and very stable and reliable. You might need to experiment with some dummy data before you go for the real thing, though. 

Make sure you have the correct target/source and have the sync set up correctly. Basically, make sure you understand what it does, what it is doing and what you are telling it to do before going beyond the 'point of no return'. 

It may even be an idea to drag and drop the data first time so you KNOW you have two copies, then sync them using a profile in Luckybackup.

Good luck(ybackup!). ;)

---

### Post by Megadoomer on 2017-06-16
Thank you both for your suggestions!

> **siben17 said:**
> If you have SSH on booth you can do something like this from your laptop :
rsync -e ssh -a -z --delete --stats user@yourdesktopIP:/path/to/files/directory /path/to/destination

I think SSH is installed on every Ubuntu Desktop derivative by default, right? Is there anything else that needs to be installed or configured? Do I have to give special permissions to the folder or any other settings?


> **Bucky Ball said:**
> I'd probably use Luckybackup for this, but because I know it. Simple GUI. It is in the repositories (look in whatever package manager you are using or install from terminal).

[Bit more info here]("http://luckybackup.sourceforge.net/features.html") and features down the page. 

I'm definitely gonna look into that for my regular backups as well, but I saw that it apparently uses rsync, too. ;)

I've also found this guide on how to share folders with Nautilus/Samba: [http://ubuntuhandbook.org/index.php/2015/02/share-a-folder-in-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2015/02/share-a-folder-in-ubuntu-14-04/) Which I tried, but I can't see my shared folder or my desktop computer, for that matter, in the Network-Directory of the file manager. I haven't tried using rsync yet, but it would be nice to try an alternative as well. Do you have an idea on what could be the issue with this?

---

### Post by Bucky Ball on 2017-06-16
An alternative would be Filezilla. That is also in the repositories. Helps if you have static IP address on the machines. The things I'm suggesting are really frontends for things you could do on the command line, but I prefer GUI, so throwing it out there. ;)

Sorry, can't help with Samba. Haven't used it since had Win boxes talking to each other and that was over a decade ago.

---

