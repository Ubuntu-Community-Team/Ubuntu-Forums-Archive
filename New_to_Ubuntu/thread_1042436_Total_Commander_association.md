---
title: "Total Commander association ?"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by J0ker on 2009-01-17
Hi, after trying some linux alternatives to Total Commander, I decided to try run TC with wine in my Ubuntu 8.10. It worked really great and I liked it till the moment, when I tried to open .doc file directly from it - it is not associated with openoffice and I cant figure out how I can add this manualy. Can someone please help me with this ?

Thank you for your answers.

---

### Post by Catboy~ on 2009-01-17
Right click the file and click the button that says "Open With Other Application" and find openoffice in the list :)

---

### Post by northern lights on 2009-01-17
Never used "Total Commander", but I am not very fond of the idea of using a Windows native filemanager through wine for frequent/regualr fileoperations on a GNU/Linux system.

What features are you missing / do you need?

Try *gnome-commander* if you're not satisfied with *nautilus*. Run```
sudo apt-get install gnome-commander
```to install.

---

### Post by Hendrixski on 2009-01-17
THIS ugly thing? [http://www.ghisler.com/picture.htm](http://www.ghisler.com/picture.htm) 

Well, it's "proprietary", which means that you can't modify it.  If you can't modify it when it's broken then you can't fix it.

My advice:  The file manager's for Ubuntu are probably better... and if you need FTP, try filezilla or something.

---

### Post by northern lights on 2009-01-17
> **Hendrixski said:**
> THIS ugly thing? [http://www.ghisler.com/picture.htm](http://www.ghisler.com/picture.htm) 

Well, it's "proprietary", which means that you can't modify it.  If you can't modify it when it's broken then you can't fix it.

My advice:  The file manager's for Ubuntu are probably better... and if you need FTP, try filezilla or something.
Didn't figure it wasn't a filemanager but an FTP client.

Still not a good idea to use a Windows native FTP client through wine.

+1 for filezilla, gFTP should do the job also.

Man, get rid of "Total Commander" (+1 again for it being ugly). On top of its looks, it's a huge waste of resources to not use some gtk app.

---

### Post by Hendrixski on 2009-01-17
> **northern lights said:**
> Didn't figure it wasn't a filemanager but an FTP client.

Still not a good idea to use a Windows native FTP client through wine.

+1 for filezilla, gFTP should do the job also.

Man, get rid of "Total Commander" (+1 again for it being ugly). On top of its looks, it's a huge waste of resources to not use some gtk app.

It said FTP on the picture of it that I found... so, yeah.
I'd never heard of gnome commander before.  Cool.  But I love nautilus.  The tabbed browsing is AWESOME. Just like firefox.

---

### Post by J0ker on 2009-01-17
I tried gnome commander and I am missing built in acces to the rar and zip archives, it is annoying when you click on archive and ubuntu default manager will pop-up. In TC you can simply open it and pres F5 to decompres it wherever you want. And there are some other things I am used to after 5+ years of using TC in win :/ It is not ugly think for me, it is daily bread :)

I use FTP only once a month so it is not a big issue for me ... Can you recommend me some alternatives which I should try if this problem with TC will stay unsolved ?

---

### Post by albinootje on 2009-01-17
> **J0ker said:**
> I tried gnome commander and I am missing built in acces to the rar and zip archives, it is annoying when you click on archive and ubuntu default manager will pop-up. In TC you can simply open it and pres F5 to decompres it wherever you want. And there are some other things I am used to after 5+ years of using TC in win :/ It is not ugly think for me, it is daily bread :)

I use FTP only once a month so it is not a big issue for me ... Can you recommend me some alternatives which I should try if this problem with TC will stay unsolved ?

Nautilus was mentioned.
My favorite file manager since many years is Midnight Commander (sudo apt-get install mc), but that is console based, not GUI.

[http://en.wikipedia.org/wiki/Midnight_Commander](http://en.wikipedia.org/wiki/Midnight_Commander)
Can handle archives (provided that you have installed unrar,unzip etc.).
Can do ftp in one panel with : cd [ftp://hostname](ftp://hostname)
I always enable the "Lynx style navigation" which makes browsing through directories *very* fast.

---

### Post by northern lights on 2009-01-17
In *nautilus* you can right-click an archive and choose "Extrtact here".

---

### Post by Hendrixski on 2009-01-17
> **albinootje said:**
> Nautilus was mentioned.
My favorite file manager since many years is Midnight Commander (sudo apt-get install mc), but that is console based, not GUI.

[http://en.wikipedia.org/wiki/Midnight_Commander](http://en.wikipedia.org/wiki/Midnight_Commander)
Can handle archives (provided that you have installed unrar,unzip etc.).
Can do ftp in one panel with : cd [ftp://hostname](ftp://hostname)
I always enable the "Lynx style navigation" which makes browsing through directories *very* fast.

Oh yeah, well my favorite file manager is Emacs!  I'm still looking for a good text editor though :-p

---

### Post by northern lights on 2009-01-17
> **Hendrixski said:**
> Oh yeah, well my favorite file manager is Emacs!  I'm still looking for a good text editor though :-p
:lol:

That's a good one.

Still chuckling.

---

### Post by morningboat on 2009-01-17
You can have a look on MuCommander for a tc style comander with archive browsing support.

---

### Post by Thradya on 2009-02-06
Oh god, you linux people ale really terrible at nonlinux stuff.
NONE of your silly little apps come even remotely close to TC. Period.

Solution for file associations can be found here:
[http://ghisler.ch/board/viewtopic.php?t=17082&postdays=0&postorder=asc&start=0](http://ghisler.ch/board/viewtopic.php?t=17082&postdays=0&postorder=asc&start=0)

---

### Post by albinootje on 2009-02-07
> **Thradya said:**
> Oh god, you linux people ale really terrible at nonlinux stuff.
NONE of your silly little apps come even remotely close to TC. Period.

I've seen Total Commander "in action", why would I ever want to use such an ugly looking piece of closed source software as my default file manager ?

The command line, Midnight Commander and also Nautilus are more than enough for me since years.

---

### Post by x33a on 2009-02-07
i've been a regular user of total commander for years on windows, and i was totally in love with it. it's one of the best file manager out there for any os. the only minus point is its being closed source.

as for it being ugly, well that screenshot is of an older version and the newer ones look much better. and, a lot of linux apps look uglier, but still provide superb functionality.

on topic: despite being a fan of TC, i too would say, that you need to use a native linux file manager. there are a lot of good ones there including krusader, midnight commander etc.

---

### Post by Achilles124 on 2009-02-07
I have used Total commander so I know what you are talking about. I use **xfe** under Linux.

[http://roland65.free.fr/xfe/index.php?page=home]("http://roland65.free.fr/xfe/index.php?page=home")

You can download it on your system by way of synaptic manager.

---

### Post by oldos2er on 2009-02-07
How well does a Windows file manager handle Linux file permissions?

---

