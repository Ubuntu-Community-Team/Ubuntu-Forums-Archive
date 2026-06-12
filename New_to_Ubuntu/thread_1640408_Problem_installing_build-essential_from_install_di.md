---
title: "Problem installing build-essential from install disc"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by dittohead4 on 2010-12-07
Hello, I am new to Ubuntu and have tried following the instructions on how to [install packages without an Internet connection]("https://help.ubuntu.com/8.04/add-applications/C/offline.html") and am still having trouble installing build-essential.

When Ubuntu is running, I insert the installation disc, and I do not receive a pop-up saying "This disc has packages on it, would you like to open Synaptic Package Manager?" or something along those lines...

So I open Synaptic Package Manager myself, and click on Settings > Repositories and in the section titled "Installable From CD-ROM" the disc shows up and I turn the check mark on.

Then I click the Reload button and I get a list of errors saying it's unable to fetch a bunch of things from the server.  (Sorry I can't list all of the errors and I am connected to the Internet from a different PC)

Then when I try to mark build-essential for installation, I end up getting errors saying that some packages could not be retrieved from the servers.

It's like even though I have the CD-ROM checked in the "Installable From CD-ROM" section, it's still trying to install them from the servers...What am I doing wrong?  Any help would be appreciated.  Thanks.

---

### Post by gordintoronto on 2010-12-07
The CD doesn't have all the packages which make up "build-essential".

If you go to packages.ubuntu.com you can download what you need. Pay a lot of attention to all the "depends," you need to download each of them. You will get a bunch of deb files, which you can put on a flash drive, for example, to move to your Ubuntu computer.

---

### Post by anewguy on 2010-12-07
It's easier, when installing from the install CD, to not go through the package manager.  Instead, cancel the notice that says a software disk is found, then open the disk via "places" and navigate the CD.  In your case, build-essential is in the /pool/main/b/build-essential folder.  Dependencies may not be met, but I've installed, and had others install, build-essential, b43-firmware-cutter, ndiswrapper common, ndiswrapper utilities and ndisgtk this way with no problems.

Dave ;)

---

