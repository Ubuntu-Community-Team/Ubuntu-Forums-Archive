---
title: "How do I turn a ZIP file into an ISO file?"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by brawnypandora0 on 2011-03-03
I've never "burned" (or do computer scientists call it "copied?") a CD before in my life until yesterday. I'm currently using Windows and want to install lubuntu, because my computer does not meet the hardware requirements for Ubuntu. I went to the lubuntu website and clicked on the download link which resulted in a single ZIP file. I unzipped all the files and then dragged the icons onto the blank CD icon. But then I read around online and saw that I actually have to have an ISO image. What does that mean?

Also, after the files were successfully engraved onto the CD, I ejected the CD and inserted it in again. Autoplay did not run, so I didn't know what to do next. There was this icon called Wubi that offered to install Xubuntu or Ubuntu, but strangely lubuntu was not an option. What's going on here?

---

### Post by Hedgehog1 on 2011-03-03
We call it 'Burning'.

The file you downloaded should have ended with: '.iso'

An ISO file is a whole CD squeezed into the smallest file we possibly can.

You need to burn a CD again, using the ISO file as downloaded, but this time select the 'Burn ISO to CD' option in your burning software.

There are free CD burning software packages for Windows if you don't already have one.

To re-download the lbuntu ISO: [http://people.ubuntu.com/~gilir/lubuntu-10.10.iso]("http://people.ubuntu.com/~gilir/lubuntu-10.10.iso") (in case you need a clean one).

***The Hedge***

:KS

---

### Post by brawnypandora0 on 2011-03-03
What's the difference between using free burning software and simply dragging icons onto the CD in Windows?

If there is a difference, why isn't the software provided in Windows?

---

### Post by nickleboyblue on 2011-03-03
Windows doesn't support burning iso files to a disc last I checked.  If you want to burn one, you'll have to get one of the many available free programs for that.  Dragging and dropping in the CD drive in windows won't work.

As to why it won't work, my guess is that windows doesn't want you replacing your operating system.  Bad for business, you know.  Of course, I could be wrong, but I doubt it.

---

### Post by brawnypandora0 on 2011-03-03
OMG! Foiled by Bill Gates yet again. Is the same true with Mac?

---

### Post by beew on 2011-03-03
If you can boot from usb and have a usb flash drive around it is a lot easier to make a live usb instead of a live CD, it is a lot faster too. 

Download the Lubuntu ISO image and get LILI

[URL="http://www.linuxliveusb.com/"]http://www.linuxliveusb.com/
[/URL]

---

### Post by Ben Page on 2011-03-03
> **nickleboyblue said:**
> Windows doesn't support burning iso files to a disc last I checked.  If you want to burn one, you'll have to get one of the many available free programs for that.  Dragging and dropping in the CD drive in windows won't work.

As to why it won't work, my guess is that windows doesn't want you replacing your operating system.  Bad for business, you know.  Of course, I could be wrong, but I doubt it.

Windows has a built in burning application, it just lacks advanced options that other burning software offers. I know XP can burn CD/DVDs, but it's been a while I used XP for burning a CD. Windows 7 has a dead simple tool for burning .iso files to a CD/DVD. Just double click the .iso image and Windows will burn it as a functional bootable CD. (thats if you don't have another CD/DVD burning software installed and set up as default .iso handler).

The poster made a mistake because he burned a CD as a data CD, so that CD was not bootable, you can't burn a bootable CD by dragging files to it. Even if you drag .iso file onto a blank CD, Windows will assume that you want to burn that FILE ONTO a CD, not to burn a bootable CD.

To avoid confusion, I recommend a small, free and fully functional Windows application for burning CD/DVDs called CDBurnerXP: [http://cdburnerxp.se/](http://cdburnerxp.se/) Works on XP and up

---

### Post by mcduck on 2011-03-03
> **brawnypandora0 said:**
> What's the difference between using free burning software and simply dragging icons onto the CD in Windows?

If there is a difference, why isn't the software provided in Windows?
The thing is you don't want to burn a CD with the .iso file in it, you want to burn a CD that's exact copy of the .iso file itself.

.iso files are disk images, which means that instead of just containing a bunch of files, they actually contain the whole file system, exactly as it would be if it was an actual physical CD and not just a file on your computer. Kind of like if it was a photograph of the exact structure of a CD (which is why they are called *disk images*)

As a result, you need to burn the CD using a program that can duplicate the file system contained in the .iso file into a CD. Just burning the .iso file itself, or it's contents, doesn't work.

Also, the reason why you though that the file you downloaded was a .zip (or similar) archive is that many archiving programs are able to extract the contents of .iso files, and therefore tend to (at least on Windows) assign the files to themselves, giving the .iso file whatever icons the archive application might use. So .iso file would get a similar icon to, say, a .zip file. I *really* recommend configuring Windows to show file name extensions by default, it avoids many confusing problems like this, allowing you to identify files based on their whole name instead of just relying on the icons.

---

### Post by Mark Phelps on 2011-03-03
> **nickleboyblue said:**
> Windows doesn't support burning iso files to a disc last I checked.  

There are plenty of FREE MS Windows apps that WILL burn ISOs to CDs and DVDs.

One of the best out there is ImgBurn.  It even supports burning to blue-rays disks!

---

### Post by Anuovis on 2011-03-03
Like people said, some versions of Windows allow you to burn a CD. But it is usually a very lame option of dragging several files into a window and then clicking a button. Not suitable for your case since it does not understand the .iso files.

Think of .iso as a sealed package that includes everything that should be on that final CD. If you want to install an OS, generally you need to download an .iso file. There might be options to install from USB sticks and whatnot but stick to CDs for the first time, it is somewhat easier for beginners.

Now, you need a decent burning program for Windows. There are a lot of them that are free and good, I used those back in the day. Just be sure it has an option to read .iso files and make the CD *out of them*.

EDIT: I checked CDBurnerXP suggested by another person in a thread, it used to work well for me.

---

### Post by dfreer on 2011-03-03
> **brawnypandora0 said:**
> I went to the lubuntu website and clicked on the download link which resulted in a single ZIP file.

The actual link to download lubuntu is here:
[http://people.ubuntu.com/~gilir/lubuntu-10.10.iso](http://people.ubuntu.com/~gilir/lubuntu-10.10.iso)
Which is clearly an .iso file. The problem you likely encountered is that .iso files can be treated like an archive, just like .zip. Most likely, you have "Hide known file extensions" checked in your "Folder View" options (it's checked by default), and the archive manager program you have installed (winzip, 7zip, or windows itself) creates an icon for your .iso file that looks exactly like your .zip files.
And Windows 7 supports burning .iso files simply by right-clicking and selecting "Burn Disc Image". I believe on windows XP you need to use software like ImgBurn.

> **brawnypandora0 said:**
> Also, after the files were successfully engraved onto the CD, I ejected the CD and inserted it in again. Autoplay did not run, so I didn't know what to do next. There was this icon called Wubi that offered to install Xubuntu or Ubuntu, but strangely lubuntu was not an option. What's going on here?
WUBI is a different way of installing Ubuntu, I would suggest reading up on it or asking on the forums for a more detailed explanation of what it is and whether it is what you want to use. I have no idea why lubuntu wasn't an option.

---

