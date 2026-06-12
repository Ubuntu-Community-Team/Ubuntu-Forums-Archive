---
title: "How to copy files from Ubuntu to DVDs to transfer to Windows?"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by oingk on 2010-04-16
Hi

This question may sound a bit stupid. I'm using Ubuntu and I have to change to Windows for a while (so I can use some Windows programs that I'm required to use for my uni). Now I want to save my files on DVDs so that after the windows install I can transfer them. However, I have never copied files on DVDs using Ubuntu before.

So how should I copy my files on DVD in a way that I can "definetly" be able to transfer them on my Windows later? What program to use?

I'm afraid to try to do it by myself in case I mess up and lose my files. That's why I'm asking. 

The files are mostly media, i.e. video and audio.
My Ubuntu is Ubuntu 9.10.

Thanks

---

### Post by fatfranko on 2010-04-16
Ubuntu 9.10 comes with Brasero which work very well.  Though, I would recommend a usb stick or something.

Have you tried virtualbox or wine for your uni programs?

---

### Post by e4uforums on 2010-04-16
> **fatfranko said:**
> Though, I would recommend a usb stick or something.


I agree.  If you have a lot of media (ie music, movies and the like) then I would probably buy yourself an external hard drive.  If you have a lot of media, it is going to take forever to back them up to DVD's and will take nearly as long to restore the data.  Hard drives are extremely cheap now considering the storage space you get.

Something like this will hold roughly the equivalent of 65 DVD's:


[http://www.newegg.com/Product/Product.aspx?Item=N82E16822101123](http://www.newegg.com/Product/Product.aspx?Item=N82E16822101123)

Also, with an external drive, it's just drag and drop to copy the files.  Couldn't be easier!

---

### Post by oingk on 2010-04-16
thanks.

I never managed to get Wine to work and I never tried Virtualbox.

Nevermind though, I'm determined that I'l dual boot windows with ubuntu. The thing is that for the time being I need to also use the university's computers and sometimes there is a non-compatibility issue.

About USB sticks, I don't have any and on the contrary I do have a couple of DVDs. 

I just found Brasero on my system and it only wants me to drag and drop files on the DVD just like I would with a USB stick or a disk, and then to press "Write to Disk". I tried to but now it asks me the strange question:

Do you really want to add "flyers" to the selection?
The children of this directory will have 7 parent directories.
Brasero can create an image of such a file hierarchy and burn it; but the disc may not be readable on all operating systems.
Note: Such a file hierarchy is known to work on Linux.

and I need to know what on earth it means.

There are two options "Cancel" and "Add File". What do I do?

thanks

---

### Post by oingk on 2010-04-16
I cancelled and tried again, and now it asks:

Do you really want to add "statistics" to the selection?
The children of this directory will have 7 parent directories.
Brasero can create an image of such a file hierarchy and burn it; but the disc may not be readable on all operating systems.
Note: Such a file hierarchy is known to work on Linux.

And there's the same two choices again.

Is Ubuntu taking the p... at me?

---

### Post by srs5694 on 2010-04-16
That's a poorly phrased error message. The issue is this: The ISO-9660 filesystem, which Brasero is using as the basis of its DVD burning attempt, is limited to directories that are eight levels deep, including the root directory. That is, a directory tree like this would be illegal: one/two/three/four/five/six/seven/eight/nine/ten; but one/two/three/four/five is just fine. There are workarounds for this when using various extensions or additional filesystems, and Linux can read discs that employ such extensions just fine. I don't know offhand if Brasero (or more precisely, the underlying tools it uses) creates a disc that will be readable in Windows in such situations.

As I see it, you can either burn your disc and hope that Windows will be able to read it or rearrange your files so that you don't use so many nested directories. If the former, you should be able to recover your files using Linux even if Windows can't read them. To maximize your chances of having it work with Linux, see if you can find an option to include UDF or Joliet support. I don't know offhand if the Linux tools can use these to overcome the ISO-9660 limit, but they're your best bets on this score.

---

