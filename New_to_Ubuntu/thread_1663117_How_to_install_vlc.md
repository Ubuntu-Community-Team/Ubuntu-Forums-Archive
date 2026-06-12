---
title: "How to install vlc"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by Japster on 2011-01-09
I have downloaded vlc and it came in a .tgz format. How do I now install the program. I'm using Ubuntu 9.10 Pls I don't really know anything about Linux so can you pls just explain it step for step for me pls.

Thanks a lot

:):):)

---

### Post by James_Lochhead on 2011-01-09
Software in Linux is a bit different than in Windows/Mac OS X, although some programs do have installers that come off websites the vast majority of software is installed through Ubuntu's in-built package management programs.

The simple one is called Ubuntu Software Center, you can find it in the main application menu I believe. The second (harder) one is the Synaptic in administration. You can even do it by terminal if you like. 

I would advise going to the Ubuntu Software Center and searching for VLC.

Applications that come in .tgz (archive) format generally require more work and experience than is appropriate for someone new to Linux.

If you do want to install from an applications website make sure you can get a .deb file.

---

### Post by Japster on 2011-01-09
My modem does not work in Linux, so I normally download within windows for the Linux. So if I understand you correct. If I want to download a program that can install in Linux it need to be in the .deb format/file extension.

So what is the tgz file extensions purpose then. I extracted it and found 3 folders inside.

Thanks for the help

---

### Post by leamon.mcnutt on 2011-01-09
the easiest way i found to install vlc is to open up terminal and type this command.

sudo apt-get install vlc

it will ask you for your password enter it and then hit enter and just sit back and watch it install

---

### Post by Japster on 2011-01-09
Thanks for the advice.

If I use the sudo apt-get install vlc pls just tell me this. Must I copy the vlc.tgz file to a specific directory or must I get a vlc.deb file for this method to work? How will Linux know where the file is?

---

### Post by James_Lochhead on 2011-01-09
> **Japster said:**
> If I want to download a program that can install in Linux it need to be in the .deb format/file extension.

That is the easiest way, however, not the only way.

> 
So what is the tgz file extensions purpose then. I extracted it and found 3 folders inside.


The tgz is an archive of files/folders. Although I do not explicitly know what is in it generally it is one of two things:

1) Pre-compiled software that needs to be put in the right place with GNOME configured to use it.
2) Source code that needs compiling.

For a newbie this is a complete pain in the backside.

In addition, you will also have to make sure you manually satisfy the other packages that VLC needs to run, which is also a complete pain.

---

### Post by James_Lochhead on 2011-01-09
> **Japster said:**
> Thanks for the advice.

If I use the sudo apt-get install vlc pls just tell me this. Must I copy the vlc.tgz file to a specific directory or must I get a vlc.deb file for this method to work? How will Linux know where the file is?

Forget sudo apt-get install vlc. That requires software sources either off the Internet, or through a CD.

---

### Post by James_Lochhead on 2011-01-09
I see three solutions that might be practical:

1) Take your computer somewhere where there is Internet access for your Linux. This will be by far the easiest way.

2) Download deb packages from [http://packages.ubuntu.com/maverick/vlc](http://packages.ubuntu.com/maverick/vlc). You will need to download the deb package on this page as well as all the dependencies (in red) and hope you have the dependencies dependencies.

3) Obtain a CD with the necessary packages on.

---

### Post by DavidG24 on 2011-01-09
> **Japster said:**
> My modem does not work in Linux, so I normally download within windows for the Linux. So if I understand you correct. If I want to download a program that can install in Linux it need to be in the .deb format/file extension.

So what is the tgz file extensions purpose then. I extracted it and found 3 folders inside.

Thanks for the help

what are the three files? there should be a readme file which will detail how to install. Also, the tgz extension is a compression format (similar to .zip in Windows ...) type, so first job is to open and extract the files.

---

### Post by Japster on 2011-01-09
The 3 folders inside is as follows: opt, usr and install. there is no readme file

---

### Post by Miljet on 2011-01-09
Part of the ease of using Ubuntu is based on the assumption that you have a working internet connection. Although you can use Ubuntu and install various programs without it, doing so requires more knowledge/expertise than most newbies possess. You also will not be able to install security updates without an internet connection.

So your first priority should be getting your modem to work with Ubuntu. If you will post another thread with details about your modem / internet connection, someone should be able to help you get it working.

---

