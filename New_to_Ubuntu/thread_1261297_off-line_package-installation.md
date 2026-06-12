---
title: "off-line package-installation"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by sigosaur on 2009-09-08
[FONT=Trebuchet MS]I'm purdy sure I'm SOL, but I'll ask anyway ...

So, I'm trying to set-up a homemade DVR to record ATSC football.

The card I bought requires Vista ... or, possibly, Ubuntu 9.04.

I installed the latter on an older IBM tower ... which went ok.

However, when I tried to install the card's software, I got something about "*dialog*" missing.  I think I've found the right package, now ... and therein lies the problem.  I have no internet at home.  So I've copied the file(s) to a flash-drive ... and I'll have to try to install them at home.

I know enough UNIX/Linux to be dangerous.  And in Windows, I'm actually not too shabby.  But I'm afraid there's obviously a lot I don't understand about how Linux works.  Until now, I didn't care.

So, if I'm gettin' this right, I ***should*** be using a "*package manager*" rather than "*downloading and installing*", myself.  But, without an internet connection, I don't see that happening.

So, how bad 'o shape am I in, here?  As soon as I try to install "*dialog*", is it gonna bark about something else I need?

Is there another "*release*"/"*distribution*" that might include such things ... so I don't need to keep running to the local coffee shop to download whatever's next?

I've read a couple of the beginner things around here.  At least, skimmed them.  I'd really rather not spend weeks reading various technical manuals on the inner workings of Linux just to figure out how to install drivers for a particular piece of hardware.  Yet, apparently, that's precisely what the manufacturer's left me with ... or, Vista.

I don't mean to sound like a complete imbecile ... it's just that, from what I've read, as of yet, I think most Linux experts misjudge what folks new to Linux may or may not already know.

Moreover, I don't really need to know that ll will list files, or cp will copy them.  I need to know why there's several of the same folder names on nearly any Linux/UNIX file-system ... and why I should care ... about each one.

For instance, for all I know, I'm simply trying to install the drivers in the wrong "*directory*" and, from there, "*dialog*" simply can't be found ... not that it's not on the system.  Which, as I understand it, would be really be something.  :(

Anyhow, this is clearly where the manufacturer has gone wrong.  They've completely misjudged my own understanding of Linux.  Their directions for installing the drivers (*I'm guessing you call them drivers*) are severely lacking.  They have a text-file for "*troubleshooting*" that suggests to me that, if "*dialog*" is not found, I should install that.  ](*,)
[/FONT]

---

### Post by zvacet on 2009-09-09
It is difficult to work without internet connection,but it is not impossible.You can try to find your package [here.]("http://packages.ubuntu.com/")If your package have other packages marked with red ball then you have to download them all and install amrked ones first(they are dependencies).Other way is to try [Keryx.]("http://keryxproject.org/")

---

### Post by Bartender on 2009-09-09
sigosaur -
I've been beating my head against the dial-up at home wall for years.  Have tried AptonCd, Keryx, etc.  None of them work as well as a direct connection.  Which means they don't work.

For instance, try getting nVidia drivers.  Easy with the PC connected to the net.  I don't know if it's even possible offline.  Sure ain't easy.

Can you take the PC to someone's house who has broadband and a router?  I just about guarantee you're going to waste time trying to hand-fit drivers and packages into your installation.  Especially if you're used to the Windows way of dropping some file into a folder and having it work.

---

### Post by sigosaur on 2009-09-09
[FONT=Trebuchet MS]Thanks Gentlemen!

I was afraid of that.  Oh well.

I don't like to, but in this case, what I might do is bring the whole works to work with me one day.

The way I envisioned this, once it's all working, I shouldn't need, nor want, any internet connection for anything.  Although, I 'spose, at some point, something'll happen and I'll have to bring the whole works back to work, again.  Hopefully that won't be very often.

Really too bad those package downloads don't have an "*auto-cascade*" option.  Is there even a variant of "*apt get*" that'll look to a CD or flash-drive, instead of the internet?

Thanks again!

[/FONT]

---

### Post by winotree on 2009-09-09
I don't know how appropriate this is to your discussion, but at the moment it seems to me that  [http://beans.seartipy.com/2006/05/06/update-or-install-applications-on-debianubuntu-without-an-internet-connection/](http://beans.seartipy.com/2006/05/06/update-or-install-applications-on-debianubuntu-without-an-internet-connection/)  might work.   If it doesn't, maybe someone else will find it useful sometime.  ;)

---

### Post by sigosaur on 2009-09-09
[FONT=Trebuchet MS]That's purdy much what I need ... thanks!

Now I just gotta make some heads 'n tails of it.

Here's the gist of it, if anyone wants to try to explain it to me ...

[/FONT]Here is an example of how you can install the package **lynx** on your local machine using the above procedure:
 
[LIST=1]
[*] On local machine:  sh# apt-get -qq ––print-uris install lynx | awk -F\‘ ‘{ print $2 }‘ > get.lst
sh# cp get.lst /media/cdrom
sh# umount /media/cdrom 
 **Update:** If you are getting errors with the above awk command, you can try with a perl script. More details in [this comment]("http://beans.seartipy.com/2006/05/06/update-or-install-applications-on-debianubuntu-without-an-internet-connection/#comment-545").
[*]Copy the file get.lst to the machine with fast Internet connection(using a CD etc):  sh# mkdir /home/user/debs
sh# cp /media/cdrom/get.lst /home/user/debs
sh# cd /home/user/debs
sh# wget -c -i get.lst
sh# cp *.deb /media/cdrom
sh# umount /media/cdrom 
[*]Copy all the .deb files to the local machine(again, using CD etc) in
*/root/debshare* directory:  sh# mkdir /root/debshare
sh# cp /media/cdrom/*.deb /root/debshare
sh# cd /root
sh# dpkg-scanpackages sharedebs /dev/null | gzip > sharedebs/Packages.gz 
[*]Add a line in the /etc/sources.list file and install the application using *apt-get*:  sh# emacs -nw /etc/apt/sources.list
 [INDENT]deb file:/root sharedebs/
[/INDENT]  sh# apt-get update
sh# apt-get install lynx 
[/LIST]
             
FWIW, I'll be using a flash-drive ... if I can.

I suppose "*emacs*" is some sort of editor ... wholly unlike Notepad?  :cry:

---

### Post by lykwydchykyn on 2009-09-09
> **sigosaur said:**
> 
I suppose "*emacs*" is some sort of editor ... wholly unlike Notepad?  :cry:

Yes.  But you can accomplish the same with any text editor.  I would recommend nano, as it is simple for new users and (unlike emacs) is installed by default.  Just substitute "nano" for anywhere you see "emacs -nw".

---

### Post by mac9416 on 2009-09-17
> I've been beating my head against the dial-up at home wall for years. Have tried AptonCd, Keryx, etc. None of them work as well as a direct connection. Which means they don't work.
I would like to speak up for Keryx. I think we all agree that there is not much anything better than a direct connection, but that doesn't make everything else useless.

> 
For instance, try getting nVidia drivers. Easy with the PC connected to the net. I don't know if it's even possible offline. Sure ain't easy.
**Anything that can be installed online with APT can be installed offline with Keryx.** I have installed Nvidia drivers on my offline computer with Keryx. You simply have to know the name of the package. It's been a while since I installed the drivers, but I believe it's "nvidi-glx-<version #>".

> Really too bad those package downloads don't have an "auto-cascade" option. Is there even a variant of "apt get" that'll look to a CD or flash-drive, instead of the internet?
You can make what's called a "local repository" once you have all the .debs you need, then you can install all the software with apt-get. All this can be done with Keryx and a little Python script I have written, but it's a rather complicated procedure (although it will be made very simple with the coming Keryx 1.0), and I can't explain it all here.

I hope someone finds this info useful! :)
-mac

---

