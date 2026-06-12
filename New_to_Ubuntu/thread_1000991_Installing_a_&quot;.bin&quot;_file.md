---
title: "Installing a &quot;.bin&quot; file"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by thadacto on 2008-12-03
I have downloaded RealPlayer from their site and it is now on my desktop as RealPlayerGOLD.bin 
How do I install it so that it is a functioning program?

---

### Post by Het Irv on 2008-12-03
you should be able to change the permissions:

Right-click on the file, click properties, goto the security tab, and make sure the box that allows the program to be run as an excutable is checked and then just double click the .bin file.

---

### Post by philinux on 2008-12-03
If your running 8.10 it's in the medibuntu repo.

Click the link below.

You'll then be able to install the deb file from synaptic.

---

### Post by Bölvaður on 2008-12-03
[http://www.youtube.com/watch?v=B6QrBtk3U4o]("http://www.youtube.com/watch?v=B6QrBtk3U4o")

Shows how to do it with gui and lets you see the terminal commands in description

---

### Post by Michael.Godawski on 2008-12-03
Or you can install the Helix Player. 

To install a bin file:

Open a shell and do this:
  ```
./<file name>.bin
```

Where <file name>.bin is the name of the bin file.
If this doesn't work, do this:
  
 ```
sudo chmod 755 <file name>.bin
```

---

### Post by oldos2er on 2008-12-03
> **thadacto said:**
> I have downloaded RealPlayer from their site and it is now on my desktop as RealPlayerGOLD.bin 
How do I install it so that it is a functioning program?

 Open a terminal, and run these commands one at a time:

 cd Desktop

 chmod a+x RealPlayer11GOLD.bin

 sudo ./RealPlayer11GOLD.bin

 After that's done, go to Applications, Sound & Video, and you should see RealPlayer 11 there. Clcik on it to complete the install.

---

### Post by thadacto on 2008-12-03
Got to Permissions (this is the security?) and enabled read - write which removed the "lock" above the icon on the desktop.I then enabled "Allow executing file as program. Clicked CLOSE.
Double left click on the icon and
"Couldn't display "/home/george/Desktop/RealPlayer11GOLD.bin".
There is no application installed for this file type"

Next move?

---

### Post by LowSky on 2008-12-03
Real offers the .Deb package right on there wedsite
[http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.deb](http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.deb)

---

### Post by thadacto on 2008-12-03
I'm running - or trying to run (but not very successfully) 8.04 (Hardy?)
chmod is not working as the RealPlayer file is on the desktop and not in my home folder.

chmod a+x RealPlayer11GOLD.bin
chmod: cannot access `RealPlayer11GOLD.bin': No such file or directory

---

### Post by billjoie on 2008-12-03
The big advantage of Ubuntu is that it works with packages (".deb" files), which take care of all the dependencies for you.  You should always absolutely prefer installing programs through packages, it will keep your system a lot more robust and up to date.  I recommend you enable the "medibuntu" repository (tons of forums explaining how, just google) and install realplayer through synaptic.  Or else, if you prefer, download the ".deb" file from the Realplayer website and open it with Gdebi, which makes sure all dependancies are taken care of.

---

### Post by Michael.Godawski on 2008-12-03
You have to navigate in terminal to the directory in which the bin file is located.

So when it is on your Desktop type

```
cd Desktop
```
Then 
```
ls -a
```

to list all files in this directory ( it makes it easier to navigate )
then when you are sure the file is in this directory you are currently in, perform the chmod command.

---

### Post by thadacto on 2008-12-03
Real offers the .Deb package right on there wedsite

Downloaded it again, the Deb package - "wrong architecture"

I'm running 8.04 and 64 architecture

---

### Post by billjoie on 2008-12-03
> **thadacto said:**
> Real offers the .Deb package right on there wedsite

Downloaded it again, the Deb package - "wrong architecture"

I'm running 8.04 and 64 architecture


Then I really recommend you (1) enable medibuntu package, (2) run synaptic, and use it to search and install the right realplayer package for your achitecture.

---

### Post by thadacto on 2008-12-03
I got to the Desktop in the terminal
processed the chmod ... OK

then:
george@george-desktop:~/Desktop$ chmod a+x RealPlayer11GOLD.bin
george@george-desktop:~/Desktop$ sudo ./RealPlayer11GOLD.bin
+[sudo] password for george: 

Once I have to type in the password, nothing happens - nothing gets typed, the cursor doesn't move.

I GIVE UP!!!!!

---

### Post by Michael.Godawski on 2008-12-03
> Once I have to type in the password, nothing happens - nothing gets typed, the cursor doesn't move.

:D That is normal.  Just type in your password and hit enter. You won't see any action during the input of your password.

You must not give up.:popcorn:

---

