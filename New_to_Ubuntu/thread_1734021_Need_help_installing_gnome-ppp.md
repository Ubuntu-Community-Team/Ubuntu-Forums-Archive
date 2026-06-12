---
title: "Need help installing gnome-ppp"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by TCMGO on 2011-04-19
After reading numerous instructions, I am still unable to install gnome-ppp. I downloaded the zip file to my usb stick, copied it to my home file and extracted it. There are now a whole bunch files under a new directory named gnome-ppp 0.3.23. From here I am lost. I opened a readme file called install instructions, which did't work and got rather complicated quickly. I could use some real basic, step-by step instructions. Thank you

---

### Post by Miljet on 2011-04-19
Why don't you just install it using Synaptic Package Manager?

---

### Post by TCMGO on 2011-04-19
I have tried the synaptic package manager (SPM), but do not know how get it to look at (let alone install) the gnome-ppp package that I downloaded to my usb stick.  How do I get this package on the SPM radar screen so that I can install it.  I am totally lost.

---

### Post by Blasphemist on 2011-04-19
In Synaptic, Settings-Repositories, other software tab-add, web address of package.

Or 
Adding a PPA to your Ubuntu system
In Ubuntu 9.10 (Karmic) and subsequent versions
If you're using the most recent version of Ubuntu, or any that has been released since Ubuntu 9.10, adding a PPA is really simple.

Step 1: Visit the PPA's overview page in Launchpad and look for the heading that reads Adding this PPA to your system. Make a note of the PPA's location, which looks like:


ppa:gwibber-daily/ppa
Step 2: Open a terminal and enter:


sudo add-apt-repository ppa:user/ppa-name

Adding the repository
Replace ppa:user/ppa-name with the PPA's location that you noted above.

Your system will now fetch the PPA's key. This enables your Ubuntu system to verify that the packages in the PPA have not been interfered with since they were built.


Ubuntu adding the repository and its key
Important: This is not an endorsement of any of the software in PPAs. You must make sure you trust the PPA owner before installing their software.

Step 3: Now, as a one-off, you should tell your system to pull down the latest list of software from each archive it knows about, including the PPA you just added:


sudo apt-get update
Now you're ready to start installing software from the PPA! If you already have the software installed and you're adding the PPA to get a more recent/different version, you may just need to run:


sudo apt-get dist-upgrade

---

### Post by TCMGO on 2011-04-19
It was suggested that I use the Synaptic Package Manager (SPM) to install a package that I downloaded to my usb stick. The package is gnome-ppp, which I need to connect my serial hardware modem to the Internet. As it is I cannot update my installation nor download packages with the SPM until I get connected, which is somewhat like a Catch-22. Can someone give me instructions on how to install the package that is on my usb stick using the SPM? Here is where it stands:
 
I have the zipped file on my usb stick .
It has also been copied to my home folder
It was also extracted to my home folder.
 
I do not know how to get SPM to see it.

---

### Post by oldos2er on 2011-04-19
Open a terminal and run ```
sudo dpkg -i gnome-ppp*deb
``` But, I see gnome-ppp has many dependencies, so the above command won't work.

Depends: libatk1.0-0 (>= 1.29.3), libc6 (>= 2.7), libcairo2 (>= 1.2.4),
         libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.2.1),
         libgdk-pixbuf2.0-0 (>= 2.21.6), libglade2-0 (>= 1:2.6.1),
         libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.8.0), libpango1.0-0 (>=
         1.14.0), libpng12-0 (>= 1.2.13-4), libx11-6, libxml2 (>= 2.6.27),
         wvdial

Edit: You might want to look at this software for installing packages without an internet connection: [http://keryxproject.org/](http://keryxproject.org/)

---

### Post by mörgæs on 2011-04-19
Try to avoid downloading stuff from here and there on the web. The Ubuntu repositories are the way to go.

There is no need for using a personal package archive in this case. Just search in Synaptic for gnome-ppp and mark for installation.

---

### Post by ashickur.noor on 2011-04-19
> **TCMGO said:**
> After reading numerous instructions, I am still unable to install gnome-ppp. I downloaded the zip file to my usb stick, copied it to my home file and extracted it. There are now a whole bunch files under a new directory named gnome-ppp 0.3.23. From here I am lost. I opened a readme file called install instructions, which did't work and got rather complicated quickly. I could use some real basic, step-by step instructions. Thank you
You may have download the source code. If you want to install it then you have to use
```

./configure 
make
sudo make install

```
in terminal.

If you have *.deb file in the extracted folder then goto synaptic=>File=>Add Download Packages.

---

