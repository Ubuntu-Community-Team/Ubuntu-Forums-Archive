---
title: "questions about fstab, samba, and 9.10 karmic koala"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by bradmayne04 on 2010-04-14
hey everyone.  Before I start I ask that you pay attention to the fact that I am using Karmic Koala 9.10.  I say this because a lot of what worked w/ hardy WILL NOT work w/ karmic as far as samba and the fstab file from what I have read.  That said I have a couple questions fstab and how could i set the config file for fstab to mount a static IP address.  I say this because winbind slows down my internet browsing so much it's unbelievable.  I've posted on this for almost a month.  I've had all sorts of replies some helpful and some ridiculus. If you can help or have been through this before let me know.  Here is the problem in a nutshell.  I need winbind so that I can access the windows machines on my network.  Winbind slows down my internet browsing so much that it's unbearable.  When I remove winbind internet browsing speed goes back to normal and all is well except that I can not access the windows computers on my network. Anyone w/ some ideas please feel free to let me know!! All I ask is that you are as descriptive as possible with your fix/workaround and understand that some files are either different or non-existant w/ 9.10 Karmic Koala.

---

### Post by achase79 on 2010-04-14
the only thing required to connect to windows PCs is smbclient.  You can use the ip address instead of the computer name.  you can use "man fstab" to get information on how to set up an entry and just use cifs for the file system type.

---

### Post by Morbius1 on 2010-04-14
If you can access the Windows machine by ip address can you not bookmark it? Or do you need to have it mount automatically on boot? 

[COLOR=Blue]EDIT:[/COLOR] By bookmark I mean enter the following into the location bar of Nautilus: **smb://192.168.0.100**
Then select Bookmarks > add bookmark. It will show up under "Places" on the left panel of Nautilus.

If you want to automount, here's a post :
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

Just ignore the "pre-work" section since it involves installing winbind which clearly isn't working for you. The following section in that post is the classic way of mounting remote shares in fstab and has nothing to do with winbind.

---

### Post by ghostborg on 2010-04-14
I'm not sure if this helps but my issue was that I was having trouble connecting to my Vista machine that doubled as a shared file source.
I went through pages and pages of how to edit these config files and finally figured out Vista mysteriously would occasionally lock out my Ubuntu machine and I would have to simply restart the Vista Box.
Although other Windows boxes could still access the Vista Box.
Did a clean install and merely right clicked on a folder that I wanted to share in my home directory and let Ubuntu install all the Samba stuff required. In fact with Ubuntu I have not directly edited any config files for anything. My Dlink router is setup typical for home network assigning all the IP addresses. When in doubt reboot.

My point being sometimes your sitting there, pulling your hair out, trying to figure out what is wrong with a particular computer and it could be that something else needs to be reset. Or just Vista sucks.

---

### Post by Morbius1 on 2010-04-14
My only point was that if you have static ip addresses on all your machines then instead of spending hours bolting this or that on top of your install just so you can browse to the remote box by machine name, you can simplly access the remote machine by ip address and bookmark it.

---

### Post by bradmayne04 on 2010-04-14
I'm not sure where nautilus is or how to access it.  Synaptic says I have it.  I did go to places>> network and clicked on network and then received an error message... So how do i use nautilus? how do i access it?

> **Morbius1 said:**
> If you can access the Windows machine by ip address can you not bookmark it? Or do you need to have it mount automatically on boot? 

[COLOR=Blue]EDIT:[/COLOR] By bookmark I mean enter the following into the location bar of Nautilus: **smb://192.168.0.100**
Then select Bookmarks > add bookmark. It will show up under "Places" on the left panel of Nautilus.

If you want to automount, here's a post :
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

Just ignore the "pre-work" section since it involves installing winbind which clearly isn't working for you. The following section in that post is the classic way of mounting remote shares in fstab and has nothing to do with winbind.

---

### Post by bradmayne04 on 2010-04-14
w/o winbind i can not access "network" under Places... as far as CIFS I don't know a thing about it.  This may sound stupid but talk to me as if your talking to a second grader.  I have been in prison for awhile and have forgotten quite a bit about ubuntu.  --Thanx!

---

### Post by bradmayne04 on 2010-04-14
If your talking about using the file browser under places then I get an error saying nautilus can not handle this kind of location.

---

### Post by Morbius1 on 2010-04-15
You seem to have a lot of things not working in your install.

For the "cannot handle this kind of location" problem, try this:

Open **Terminal**
Type **sudo apt-get install gvfs-backends**

When it's done installing:
Type **nautilus smb://192.168.0.100**

[COLOR=Blue] Changing 192.168.0.100 to the ip address of the remote machine you're trying to access.[/COLOR]

---

### Post by bradmayne04 on 2010-04-21
okay i did it from the command line but the problem is that i can't acces printer shares now but i can see the other shared files.. the printer access is really the only thing i need to do!!! Any ideas??
BTW this is the output from the command line when i start up nautilus: (keep in mind that the file browser GUI does come up though)
(nautilus:2532): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

should i be running this as root? please help!

---

### Post by Morbius1 on 2010-04-21
Is the printer on the Windows machine?

From the Ubuntu machine:

Administration > Printing > New > Windows Printer via Samba > Browse.
It should find it automatically after it does a network scan. If it can't find through the browse - and I'm guessing it can't - then  fill in the dialog box. For example:
[smb://192.168.0.100/WinPrinterName]("smb://192.168.0.100/WinPrinter")

---

### Post by bradmayne04 on 2010-04-26
> **Morbius1 said:**
> Is the printer on the Windows machine?

From the Ubuntu machine:

Administration > Printing > New > Windows Printer via Samba > Browse.
It should find it automatically after it does a network scan. If it can't find through the browse - and I'm guessing it can't - then  fill in the dialog box. For example:
[smb://192.168.0.100/WinPrinterName]("smb://192.168.0.100/WinPrinter")

Yes I've done that.  It didn't work.  When I had winbind that worked w/o winbind it doesn't work.  That's the problem I can't use winbind but it's like I need it.  I'm using the 64 bit I wonder could that be causing some issues?  This is what happens when I start nautilus.  Keep in mind that i get the GUI coming up like it's supposed to as shown by the screenshot I've also posted here.  please read on
brad@brad-laptop:~$ nautilus: smb://192.168.1.2
No command 'nautilus:' found, did you mean:
 Command 'nautilus' from package 'nautilus' (main)
nautilus:: command not found
brad@brad-laptop:~$ nautilus smb:/192.168.1.2

(nautilus:3705): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
brad@brad-laptop:~$ 

Okay but I get the nautilus GUI (see screenshot).  My problem is that I can't access the printer on the ellen-pc (here is the output of smbtree)
brad@brad-laptop:~$ smbtree
Enter brad's password: 
WORKGROUP
    \\ELLEN-PC               
cli_start_connection: failed to connect to ELLEN-PC<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
    \\BRAD-LAPTOP            
        \\BRAD-LAPTOP\IPC$               IPC Service ()
        \\BRAD-LAPTOP\MyFiles            
        \\BRAD-LAPTOP\print$  
i can't remember the command to open my samba config file but I was wondering could it be that I have to put in my user name and password ahead of time into the config file?  btw- the other machine is a vista machine.  I used to use feisty fawn on my last laptop and everthing was okay.  That was a toshiba satellite a305 s4527 32bit and i issues here and there but overall it was a great computer everything was great w/ that machine.  I had another satellite after that which was nothing but problems (i forget which model number the shitty one was other than it was also a satellite but the a305 is a solid model I'll say that.
Anyways, to get back to the point: it's as if I need winbind.  Should I report this to launchpad?  Any ideas ?

---

### Post by Morbius1 on 2010-04-26
Based on your attachment, ELLEN-PC has only one ( non-administrative ) share: Public. I assume that ELLEN-PC has a static ip address of 192.168.1.2. Also, ELLEN-PC has no shared Printer so there is nothing for the Linux machine to print to.

** [] To access the ELLEN-PC shared folder:**

Open Terminal and type:
```
nautilus smb://192.168.1.2/Public
```Once you're there bookmark it: Nautilus > Bookmarks > Add Bookmark

** [] To access the ELLEN-PC printer:**

*_On Windows_*

Start  > Control Panel  > Printers and Faxes  > right click on your printer > Sharing

check "Share this Printer"
      Share Name: [COLOR=Blue]WinPrinter[/COLOR] or whatever you choose

*_On Ubuntu_*

Administration > Printing > New > Network Printer > Windows Printer via Samba

In the smb:// box enter:
```
192.168.1.2/[COLOR=Blue]WinPrinter[/COLOR]
```

---

### Post by bradmayne04 on 2010-04-26
The vista machine is set up to share the printer.  I double checked after your posting though.  All the other computers on the network can print through the vista machine (ellen-pc) granted they are all windows computers but they can still print w/o any issues.  So, I'm w/o a printer!  I really don't understand what the problem is.  Is there a way to pull up the config file for samba and add my username and password?  Should I even bother doing that? I don't understand why with winbind everything is okay but why is the internet browsing so slow w/ winbind installed?

---

### Post by bradmayne04 on 2010-05-03
Still having issues w/ connecting to the windows printer through ellen-pc.  I can only print and the ellen-pc only comes up on smbtree correctly w/ winbind installed.  I can access through nautilus as someone posted though like i said before the printer issues arrise once again when using nautilus.  I have two printers one is a hp photosmart 7600.  I use a driver that is about the same on that because there is no exact match with  through the printer setup.  Whoever this is w/ winbind installed I can not successfully reach the printer on the vista machine (running 32 bit vista home premium on a hp pavilion) I don't believe it's a firewall or other related issue the the ellen-pc as i can successfully connect w/ winbind.  So what can I do?  Could it be something that needs to go to launchpad?  If so how would I bring it there attention?  Does anyone know anything that hasn't been tried yet?

---

