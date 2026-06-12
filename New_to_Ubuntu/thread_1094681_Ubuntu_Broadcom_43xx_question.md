---
title: "Ubuntu Broadcom 43xx question"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by EnergySamus on 2009-03-12
Hi!
Well, I haven't used Ubuntu in quite a while, so I have decided to dual boot it with Windows XP on an old Acer laptop. 

When I had Ubuntu 8.04 before (on this laptop), I had issues with the Broadcom 43xx WI-FI drivers. How do you configure the drivers for the 43xx? I remember having to do a few things before it actually worked (like downloading files).

Also, a few other questions before I install Ubuntu:

1. Should I wait for the new Ubuntu to come out? I believe that a new one is coming out soon.
2. Are there codecs avalible that will let me play ACC files (I heard that Ubuntu doesn't work with these).
3. Are there any good OSX looking themes for Ubuntu (I remember having some themes on my old Ubuntu installation.


Thanks!
EnergySamus

---

### Post by anewguy on 2009-03-12
There is a restricted driver (b43) now that works with those cards.  I believe you probably remember having to use ndiswrapper in the past.  You should be able to enable the restricted driver and it should work for you.

Dave :)

---

### Post by EnergySamus on 2009-03-12
I didn't use Ndiswrapper, but it was something similar.

So, is the 43xx already in the restricted drivers section when I install Ubuntu? Or do I have to install ndiswrapper to get it there? Wow, I have forgot alot!

EnergyXP

---

### Post by anewguy on 2009-03-13
See this link, then follow the links off it:

[https://help.ubuntu.com/community/WifiDocs/Driver/b43]("https://help.ubuntu.com/community/WifiDocs/Driver/b43")


dave :)

---

### Post by Glavata on 2009-03-13
I have the same wireless card in my HP laptop and I had lots of troubles with it prior to Ubuntu 8.10. On 8.10 everything works pretty much 'out of the box.' Just install it and you are ready to use the wifi card.

---

### Post by EnergySamus on 2009-03-13
> **anewguy said:**
> See this link, then follow the links off it:

[https://help.ubuntu.com/community/WifiDocs/Driver/b43]("https://help.ubuntu.com/community/WifiDocs/Driver/b43")


dave :)

That is the exact page that I used, Thanks!

---

### Post by rotwang888 on 2009-03-13
Yuck.  Thanks for the bad memories.  My first Ubuntu install was on a laptop with one of those cards.  I got it working, but eventually replaced the card with a $20 Intel that worked much better.  Should have done it in the first place.
 Your other questions..
1. There is always a new Ubuntu coming out soon.  They come out every 6 months.  The only real reason you might want to wait for the latest one is that it includes the ext4 file system, which is supposed to be more efficient, boot faster, etc..
2.Yes there are. You can play any audio format in Ubuntu except DRM encrypted files like things purchased from itunes.  If you try to play a file for which Ubuntu doesn't have a pre-installed codec, it will prompt you to install it. Easy.
3. Check out gnome-look.org for themes.  I haven't looked closely at them, but there are a number of OSX-style themes there.  You can even have your window buttons on the left side if you wish.

---

### Post by EnergySamus on 2009-03-13
> **rotwang888 said:**
> 
1. There is always a new Ubuntu coming out soon.  They come out every 6 months.  The only real reason you might want to wait for the latest one is that it includes the ext4 file system, which is supposed to be more efficient, boot faster, etc..
3. Check out gnome-look.org for themes.  I haven't looked closely at them, but there are a number of OSX-style themes there.  You can even have your window buttons on the left side if you wish.

But I can always update to the new one anyway!

Also, I had the buttons on the left side on my old installation. Do you know how to do this?

---

### Post by rotwang888 on 2009-03-13
> **EnergySamus said:**
> But I can always update to the new one anyway!
 Yes, but to use ext4 you'll have to reinstall from scratch.  At least I think so.
> Also, I had the buttons on the left side on my old installation. Do you know how to do this?
Never tried it, but I think most of the "OSX" window themes use Emerald.  So you'd need to install Emerald, and load one of those themes with the Emerald manager.

---

### Post by stchman on 2009-03-13
> **EnergySamus said:**
> Hi!
Well, I haven't used Ubuntu in quite a while, so I have decided to dual boot it with Windows XP on an old Acer laptop. 

When I had Ubuntu 8.04 before (on this laptop), I had issues with the Broadcom 43xx WI-FI drivers. How do you configure the drivers for the 43xx? I remember having to do a few things before it actually worked (like downloading files).

Also, a few other questions before I install Ubuntu:

1. Should I wait for the new Ubuntu to come out? I believe that a new one is coming out soon.
2. Are there codecs avalible that will let me play ACC files (I heard that Ubuntu doesn't work with these).
3. Are there any good OSX looking themes for Ubuntu (I remember having some themes on my old Ubuntu installation.


Thanks!
EnergySamus

The cutter works with those cards.

```
sudo apt-get install b43-fwcutter
```

Your card should work then.

---

### Post by BOZG on 2009-03-13
With regards to the b43 drivers being under the restricted drivers menu in Intrepid, I've just installed 8.10 on a Dell Latitude C600 with a Broadcom controller and there was no option to enable the restricted b43 drivers.  The ability to enable the b43 drivers only appeared after installing updates, which is obviously a bit pointless considering your initial problem is that you can't access the internet. 

While b43-fwcutter is an option for those with a wired connection, it's not particularly feasible when you've no internet access on that particular machine.  It's really an unfortunate problem that most wireless driver problems are dependent on internet access on the machine in question.  For anyone in such a position, I'd recommend using this site: [http://www.omattos.com/omattos/broadcom/](http://www.omattos.com/omattos/broadcom/)

Once you can get internet access on another machine, you only have to download the tarball and extract it to /lib/firmware on your problem machine and a reboot should have things working straight away.

---

### Post by anewguy on 2009-03-13
> **BOZG said:**
> With regards to the b43 drivers being under the restricted drivers menu in Intrepid, I've just installed 8.10 on a Dell Latitude C600 with a Broadcom controller and there was no option to enable the restricted b43 drivers.  The ability to enable the b43 drivers only appeared after installing updates, which is obviously a bit pointless considering your initial problem is that you can't access the internet. 

While b43-fwcutter is an option for those with a wired connection, it's not particularly feasible when you've no internet access on that particular machine.  It's really an unfortunate problem that most wireless driver problems are dependent on internet access on the machine in question.  For anyone in such a position, I'd recommend using this site: [http://www.omattos.com/omattos/broadcom/](http://www.omattos.com/omattos/broadcom/)

Once you can get internet access on another machine, you only have to download the tarball and extract it to /lib/firmware on your problem machine and a reboot should have things working straight away.

This dependency is why it is sometimes suggested to use ndiswrapper.  Ndiswrapper can be installed directly from the installation CD (as can it's gui front end ndisgtk).  Most people already have a windows driver on disk.  This is the beauty of ndiswrapper.  I appreciate the move to restricted drivers, but ndiswrapper can work in most cases with no need to have internet access, no need to download something from another computer, etc..  In short, for the people who are new and asking for help, the easiest set of instructions is installing ndiswrapper from the installation CD and then using the windows driver.

Just another thought on your very valid point.

dave :)

---

### Post by BOZG on 2009-03-13
I've had problems with using the CD as a software source in the past, sometimes working, sometimes not.  Might just be me though.

As for "ndisgtk", are you sure it's on the disc?  Definately not on the Kubuntu discs as I've just spent the past 2 hours trying to get my Realtek 8185 drivers working and I've been forced to acquaint myself with ndiswrapper through the command line.

---

### Post by anewguy on 2009-03-13
Yep -- if instead of using the disk as a software source for synaptic, and instead just "explore" it with "places", you can find ndisgtk and ndiswrapper both.  Starting at the root of the installation CD (at least for a "normal" Ubuntu install), the packages are located at:

/pool/main/n/ndisgtk

and 

/pool/main/n/ndiswrapper

Just double-clicking on each of the files in each of those folders will install them.

I have never installed kubuntu, just added KDE to a normal install, so I don't know if you can navigate the disk and find them or not.  For the regular Ubuntu install CD, once you get to "main" you find the folders that represent the old disk sets.  I'd be curious to know (as would others reading the post) if you can find them by navigating the disk for kubuntu instead of using it as a source for the package management software.

The b43 firmware cutter is also under the /pool/main/b folder, as is build-essential.  The thing to remember is that these things are mainly there to help you in such circumstances as not being able to get on the net initially - they may well be out of date as of the time you do an install.  It's always important that as soon as you have internet access to be sure to use the package manager and also let Ubuntu install the updates it finds automatically.

Dave :)

---

### Post by BOZG on 2009-03-16
> **anewguy said:**
> Yep -- if instead of using the disk as a software source for synaptic, and instead just "explore" it with "places", you can find ndisgtk and ndiswrapper both.  Starting at the root of the installation CD (at least for a "normal" Ubuntu install), the packages are located at:

/pool/main/n/ndisgtk

and 

/pool/main/n/ndiswrapper

Just double-clicking on each of the files in each of those folders will install them.

I have never installed kubuntu, just added KDE to a normal install, so I don't know if you can navigate the disk and find them or not.  For the regular Ubuntu install CD, once you get to "main" you find the folders that represent the old disk sets.  I'd be curious to know (as would others reading the post) if you can find them by navigating the disk for kubuntu instead of using it as a source for the package management software.

The b43 firmware cutter is also under the /pool/main/b folder, as is build-essential.  The thing to remember is that these things are mainly there to help you in such circumstances as not being able to get on the net initially - they may well be out of date as of the time you do an install.  It's always important that as soon as you have internet access to be sure to use the package manager and also let Ubuntu install the updates it finds automatically.

Dave :)

You learn something new everyday!  I'll bear this is mind in the future.

As for the KDE disc, fw-cutter and ndiswrapper are both available but there's no sign of build-essential or ndisgtk  I've been playing around with using the disc as a repository and I think a glitch might have been responsible for why I've had problems with using the disc as a repository in the past.  The disc is automatically listed in the menu as a Software Source in Kubuntu, but it's not enabling.  Even after enabling and reloading, it doesn't seem to work properly.  When I manually choose the option to add another disc, it seems to work fine.

---

### Post by anewguy on 2009-03-16
> **BOZG said:**
> You learn something new everyday!  I'll bear this is mind in the future.

As for the KDE disc, fw-cutter and ndiswrapper are both available but there's no sign of build-essential or ndisgtk  I've been playing around with using the disc as a repository and I think a glitch might have been responsible for why I've had problems with using the disc as a repository in the past.  The disc is automatically listed in the menu as a Software Source in Kubuntu, but it's not enabling.  Even after enabling and reloading, it doesn't seem to work properly.  When I manually choose the option to add another disc, it seems to work fine.

Thanks for the info on the KDE disk.  Having never used it, this adds to my knowledge base.

Dave :)

---

### Post by EnergySamus on 2009-03-18
I don't know if anybody could tell me, but I downloaded the OSx theme from here: [http://www.gnome-look.org/content/show.php/MacOS-X+Aqua+Theme?content=13548](http://www.gnome-look.org/content/show.php/MacOS-X+Aqua+Theme?content=13548)

How do you install this theme? The instructions say to put the OSx Metacity folder into my "~./themes" folder, but when I do, it says that I don't have access to the folder.


EnergySamus

---

### Post by BOZG on 2009-03-18
cd to the directory that the folder was unpacked to and try

```
sudo mv foldername ~/.themes
```

It should ask you for your password and then move the folder.

---

### Post by EnergySamus on 2009-03-18
> **BOZG said:**
> cd to the directory that the folder was unpacked to and
try

```
sudo mv foldername ~/.themes
```

It should ask you for your password and then move the folder.

Not to sound nooby, but what does cd mean? I unpacked it to my desktop, so what do I do?

Thanks for your help!
EnergySamus

---

### Post by anewguy on 2009-03-18
cd stands for change directory (or more specifically, change default directory).  When in a terminal window (what some call the command line), you have a default path the Linux looks in - when you first log on this is ~, or your home directory.  Technically with Ubuntu it will be pointing to /home/<your user id>.  When you first log on, if you do a ls (list) it will show the contents of your home folder.  In that list you should see Desktop.  Considering you place this on your Desktop, you need to "change directory" to "Desktop".  Replace "change directoy" with the Linux command "cd", add a space, the add the destination - in this case "Desktop" and you get:

cd Desktop <press enter>

After you have done that, follow BOZG's last post:

sudo mv foldername ~/.themes


EDIT:  BTW, if you need to get to the command line (open a terminal window), just go to the top menu bar and click Applications, then Accessories, then scroll over and down to Terminal and click.  This will open a terminal window for you and show the command line.
Dave :)

---

### Post by EnergySamus on 2009-03-18
Thanks for your help! I have everything working!

---

### Post by BOZG on 2009-03-19
> **EnergySamus said:**
> I have everything working!


Those are possibly the four nicest words to read on these forums!

---

