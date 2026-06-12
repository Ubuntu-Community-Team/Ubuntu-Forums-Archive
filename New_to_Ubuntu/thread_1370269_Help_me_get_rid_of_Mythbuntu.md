---
title: "Help me get rid of Mythbuntu"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by Garypewitt on 2010-01-02
Well folks I've got a really dumb question for you.  When I booted up my computer yesterday instead of the Ubuntu login I got something called "Mythbuntu".  After I log in all I get is a black screen and nothing works.  I can get into the terminal mode by using Alt-control-F1  but I don't have enough experience to find or remove Mythbuntu.  I'm not even sure what it is.  I hope it's not some kind of virus.  For the time being I can't even get on Linux and have had to reinstall Windoz on my other hard drive to even get on the internet.  

Another problem I was having before this happened is that I can't save any changes to my Invidia setting in /etc/X11/xorg.config.  So every time I log in I have to set it for two monitors again, it won't save the changes at all.  

Any and all help welcomed.  Thanks a bunch.
Gary

---

### Post by Elfy on 2010-01-02
Mythbuntu is not a virus - it is an ubuntu variant - did you install it?

Nvidia-settings needs to run as root in order to save the settings, Alt+F1 then ```
gksudo nvidia-settings
```

---

### Post by Temposs on 2010-01-02
Mythbuntu is Ubuntu with MythTV, which is a program for emulating the functionality of a Digital Video Recorder. Apparently, you accidentally installed this...

If you can get to your terminal, you can try to remove anything related to mythTV with this command:

```
sudo apt-get remove myth*
```

I'm not sure if the regular gnome-desktop was removed, but you could try:

```
sudo apt-get install ubuntu-desktop
```

See if that helps things at all...

---

### Post by HiImTye on 2010-01-02
you can see what is installed so you have a better idea what to remove using aptitude. anything with an 'i' before it is installed. to do so use the search command, i.e.

```
aptitude search myth
```
will show you what is installed for Mythbuntu

hope this helps :)

---

### Post by Garypewitt on 2010-01-06
> **Temposs said:**
> Mythbuntu is Ubuntu with MythTV, which is a program for emulating the functionality of a Digital Video Recorder. Apparently, you accidentally installed this...

If you can get to your terminal, you can try to remove anything related to mythTV with this command:

```
sudo apt-get remove myth*
```I'm not sure if the regular gnome-desktop was removed, but you could try:

```
sudo apt-get install ubuntu-desktop
```See if that helps things at all...


Here I am again.  Ok, I had to install Windoz on my other hard drive in order to be able to get on the internet to ask you nice people for help.  So now I can't boot into Ubuntu at all.  
I downloaded an ISO of Ubuntu 9.10 using windoz and burned it on a DVD.  It works but 
if I use the run-from-CD mode I can't make any changes or even mount my 1TB drive that has Ubuntu on it.  I did manage to get into terminal mode and tried to run grub but it's not there on the disk.  So i used sudo apt-get grub and got it at least temporarily.  None of the excellent suggestions will work in the run-it-from-the-CD mode.  
I can't get into Ubuntu on the hard drive at all.  I -REALLY- don't want to lose all my data again.  I have over 1200 pictures, hundreds of bookmarks, and tons of saved e-mail.  The install process doesn't have a repair option just wipe it out and start over.
How can I get a grub loader back working so at least I can get into terminal on the hard drive and make those changes you so kindly supplied?  Is WUBE the only option?  There was also an option to install side by side but then I'd have two copies of 9.10 on the same drive.  Could I fix the old one that way and then delete the new one?  
Help!   :(   73  Gary

---

### Post by Linux000 on 2010-01-06
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

that should enable grub without destroying data.

W2CVZ

---

### Post by Temposs on 2010-01-06
You should be able to just install Ubuntu on your "other hard drive", overwriting Windows, and then you'd have GRUB again. I personally don't know how to restore GRUB manually.

EDIT: First try the suggestion from Linux000 :-)

---

