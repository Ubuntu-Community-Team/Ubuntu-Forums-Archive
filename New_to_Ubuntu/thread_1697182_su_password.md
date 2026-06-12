---
title: "su password"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by euriboyka on 2011-02-28
i downloaded skdownloader and as given in its installation instructions it requires SU PASSWORD.
what should i enter there ???
or in other words what is the default SU password ??

---

### Post by vivek.pandey on 2011-02-28
> **euriboyka said:**
> i downloaded skdownloader and as given in its installation instructions it requires SU PASSWORD.
what should i enter there ???
or in other words what is the default SU password ??

su is your root password or sudo password or the login password.by default all password are same

---

### Post by euriboyka on 2011-02-28
but what is that "default" password ?

---

### Post by houseworkshy on 2011-02-28
SU means super user.  It is asking for you to work in root.  However this is not recomended and you don't need to.  In ubuntu one uses sudo which is a tempory elevation of privalages.  Perhaps the program was designed with another version of linux in mind, many do use root.  If it is aimed at Ubuntu and a mistake than whatever password you use to log in it should be ok to run sudo.  If they are asking to to go to root I'd forget it.  You could post what you've been asked to do so far,  as root can be enabled in Ubuntu and you really need to know if that is what the instructions have told you to do. 
In fact, far better, ditch it and get some other client from the repositories.  There are quite a lot of them and you have one in a default install anyway ( transmission ).  Deluge and qbittorrent are also popular.  The programs in the repositories have been checked and are safe.

---

### Post by euriboyka on 2011-02-28
but that's what i am asking !!
i mean what is DEFAULT pasword?

---

### Post by vivek.pandey on 2011-02-28
listen you would be asked a password at login time this is the same password..clear enough?

---

### Post by Hippytaff on 2011-02-28
There is no default root password in ubuntu as far as I know. The su password is the one you provided when you installed.

---

### Post by Rubi1200 on 2011-02-28
The root account is locked in Ubuntu and as such there is no default password.

You can elevate privileges and use sudo. You enter the password you used to install Ubuntu, log on with etc. (it is the same password).

See here for more information:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by euriboyka on 2011-02-28
sory last reply was by mistake.

and below are the exact commands they are instructing.
		 		 		 			 				 					**SKDownloader**

 					[CENTER][[IMG]http://www.toolsbysk.com/skdownloader/images/download.gif[/IMG]]("http://www.toolsbysk.com/skdownloader/downloads/linux/gui/skdownloader_linux_installer.sh")[/CENTER]
 				 			**_ 			How to install 			_**  			
[LIST][COLOR=#0000FF] 				
[*]Download installer using the above download button to your  computer (say at /tmp/skdownloader_linux_installer.sh) and run following  commands in command line. 				
[*]> cd /tmp 				
[*]> su (You will have to provide root password here) 				
[*]> sh ./skdownloader_linux_installer.sh  				
[*]Once done, you can run skdownloader by typing "skdownloader" in command line or by clicking on the desktop shortcut. 				[/COLOR]
[/LIST]

---

### Post by houseworkshy on 2011-02-28
Just looked at the site.  Yeah it wants root.  And it's a limited freeware licence which can be changed, they often become cripple ware ie, spend some cash to get the extra funky features which you'd have had for nothing in an open source application anyway.  So you'd be installing a Java app ( which is a virtual machine remember ) using root.
I have no reason to suspect this as dodgey but why bother?  Just bung in one of the many free and tested ones in the repositories.  They work just fine and are specifically designed for Ubuntu ( assuming that is what your op is ).
There are many ways of installing, just go to Applications> Software centre....and browse.  Or go to System>Administration>Synaptic Package manager and do similar. You will be asked for a password on installing and this is the same as you log in with, but it will run sudo not full root which is far safer.   If this is too basic no offence intended, I note that you haven't posted much so guess that you may be a fairly new user ( in which case welcome :)  )

And the following are excellent and free ( well the pdf downloads are ).

[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)

Got me started right anyway.

Have fun.

---

### Post by ZeroAdam on 2011-02-28
I agree with the others here. Skip the su command in the instructions and sudo the next line.

[COLOR=black]sudo [/COLOR][COLOR=black]skdownloader_linux_installer.sh
or
sudo sh [/COLOR][COLOR=black]skdownloader_linux_installer.sh

I'm not sure about the sh command or whether or not you need it call it implicitly.
[/COLOR]

---

### Post by Rubi1200 on 2011-02-28
I recommend you not to install software from outside the official repositories. You may compromise the stability and security of your system.

There are enough good download managers and torrent clients available. Search in the Ubuntu Software Center for what is there.

qtbittorrent is really good as my personal suggestion.

---

### Post by euriboyka on 2011-02-28
i searched the repositories ..but was unable to find any.
there are mostly bittorrent clients,which i suppose are meant for downloading only torrents and not OTHER files.

---

### Post by euriboyka on 2011-02-28
ok ..i found some of them.
thanx evybody for replying .

---

