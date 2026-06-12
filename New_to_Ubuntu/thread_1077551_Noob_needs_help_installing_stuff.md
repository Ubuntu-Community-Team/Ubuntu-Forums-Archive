---
title: "Noob needs help installing stuff"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by Zapatas Dog on 2009-02-22
Hey, I'm new to Ubuntu and totally psyched, but there's some stuff I don't get.

I understand the concept of how most software is downloaded and updated, or am beginning to, but what about installing programs from other sources?

I know now that a .deb runs smoothly, like an install.exe- I installed NeroLinux with a .deb- but I have two others that I can' figure out.

One is Darwinia. It came in an .iso and I finally mounted it with MountManager, but inside I found an install.exe, and nothing happens when I try to click it- it's definitely supposed to be for Linux.

The other is Savage2 ([http://savage2.com/en/main.php)-](http://savage2.com/en/main.php)-) it came in a .bin and I can't seem to mount it, although MountManager claims to mount .bin.

Also I downloaded PowerISO from their website- it was a .tar.gz, a zip file I gather. I unzipped it to the desktop but can't open it- it just sits there mocking me. Under properties it claims to be an executable file.

I'm used to just mounting images and they pretty much run themselves, so any specific or general advice would be appreciated.

Thanks,
Zapata's Dog

PS- I am mucking through the recommended guides also, but there's a lot of info to cover.

---

### Post by Temposs on 2009-02-22
Well, the thing is that you should be trying to use things from the repositories, rather than going on websites and downloading random programs you find. The ideal way to install new software on Ubuntu is to open the "Add/Remove" program from the Applications menu. You should try to find a program on there that meets your functional needs first. Any program you install on there will be updated as necessary. If after searching for programs on there, there's absolutely nothing that meets your needs, then you should go looking on the web.

Programs downloaded as debs or from source will not be updated.

Here's basically how Ubuntu keeps programs you have installed updated. You have on your computer several lists of programs and their versions(also called "repositories lists"), and which ones you have installed. A few times per day, Ubuntu automatically downloads those lists again from the Ubuntu servers, to see if there have been any changes. On downloading the new list, Ubuntu compares the new list to the old list, and if it finds a different version in the new list for a program you have installed, then it knows that program has an update, and it will alert you to download and install it. This will happen for any program you download from Add/Remove programs or from Synaptic Package Manager.

Take a look at these guides:
[http://doc.ubuntu.com/ubuntu/switching/applications-installing.html](http://doc.ubuntu.com/ubuntu/switching/applications-installing.html)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Temposs on 2009-02-22
Regarding the particular programs you're trying to download, NeroLinux is really not that necessary because Ubuntu comes with a couple programs already for burning discs. In Applications->Sound & Video there is Brasero Disc Burning. Under the Places menu, there is CD/DVD Creator.

Darwinia comes as an iso, which is a file you should burn to a CD using Brasero Disc Burning. Just open that program and click "Burn Image" after putting in a CD.

PowerISO is completely unnecessary, as you can just use Brasero for burning ISO files to disc. fyi, if a program comes in a zip file of some sort, that means it probably needs to be compiled from source, which is a little more complicated process.

---

### Post by Zapatas Dog on 2009-02-22
Thanks, I do understand how Ubuntu is meant to work, it's just I've been doing it the other way for so long. I'm in the process of letting go.

I know what an .iso is for- in Windows I would mount it to a virtual drive rather than burning it to a physical medium- less wasteful. Anyway, looking back at the uploader's comments, I guess he made a mistake, so never mind about Dawinia.

Thanks, though.

---

### Post by steveneddy on 2009-02-22
Burn DVD's and CD's with k3b. It's a very nice tool.

```
sudo apt-get install k3b
```

Look at the links in my sig for more great advice.

Look for the application in synaptic before downloading from the internet, at least at first. You system will remain stable that way and everything updates automatically.

**System --> Administration --> Synaptic Package Manager**

---

### Post by bgates on 2009-02-22
> **Zapatas Dog said:**
> Thanks, I do understand how Ubuntu is meant to work, it's just I've been doing it the other way for so long. I'm in the process of letting go.

I know what you mean.  I tried to compile every program from source at first.  :)

---

