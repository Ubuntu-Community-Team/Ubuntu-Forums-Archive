---
title: "how do i set up my own samba network?"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by Dannylee on 2008-11-18
hi,
i am new here,
and i am trying to set up my own file sharing network, but how do i set it up?
i am trying to set a folder free so that other family members can access the files they or i put in, but i get error messages saying that i have to set it up first, can anyone guide me through these steps?
danny:confused:

---

### Post by superprash2003 on 2008-11-19
hope this helps [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by gpsmikey on 2008-11-19
An excellent source of information is the "Samba-3 by example" which is available either in hard copy from Amazon etc or as a pdf version here: [http://www.samba.org/samba/docs/Samba3-ByExample.pdf](http://www.samba.org/samba/docs/Samba3-ByExample.pdf) -- he has many examples of configurations to do all sorts of things and explains why he uses the configuration he uses.  I found it very helpful recently (I have the hard copy).

mikey

---

### Post by AlanR8 on 2008-11-19
This is what I do but I run KUBUNTU not Ubuntu. Same under the skin, just a different interface!

First off, by default samba is not installed. (Why?) What is installed is samba common.

I download the following applications:

samba
smb4k
system-config-samba
smbfs

Either do this with the your package manager of choice or you can do it from the command line as follows:

> sudo apt-get install samba smb4k system-config-samba smbfs

Enter your Root password when requested and watch as the applications download and install.

A word about smb4k. It's a small application that allows the easy mounting of remote shares. (I believe the standard file manager in Ubuntu, Nautilus, will do this for you so you might not need this).

Next, I make sure my Kubuntu machine is in the same work-group as my other machines. I have five machines on my network, three Kubuntu, one Pure XP and the wife's that dual boots.

To do this I edit my smb.conf file. Using Kubuntu, the text editor is called Kate so substitute kate in the code below with the text editor you use.

> sudo kate /etc/samba/smb.conf

Look for the line under Global Settings about 20 down from the top that says:

> workgroup = workgroup

and change the = workgroup name to that of your workgroup. Save the file.

Might be a good idea to reboot the machine at this stage to keep things real.

When you're up and running again, go to your file manager, I use Dolphin, Ubuntu uses Nautilus, and open your home folder. Create a new folder if you want, or select a folder you want to share across the network.

In Kubuntu, I right click the chosen folder then "Properties" to open the dialogue box. Then click the "Permissions" tab and allow read and write access to Owner, Group and Others. 

Click OK to confirm.

Next I run Samba from the main menu, (Applications/Settings) under Kubuntu, or I right click the desktop to open up a "Run Program" widget (KDE4.1.*. Alt+F2 will probably work in Ubuntu) and just type "samba" without the quotes.

A proper window, not a command line, will open up that will list any shares already available on your computer, for instance a printer. Click on the "Add" button and from the drop down box, "Browse" to the folder you want to share.

Select the folder and check the boxes "Writeable" and "Visible". Provide a "Share name" and a "Description" then click the "Access" tab.

Check "Allow access to everyone" if that's what you need, and I suspect you do.

Click OK to save and go back to the original window.

Now, from the "Preferences" menu, select "Samba Users" and a sub window will open up with the default username, (yours), and "nobody"

Select your username then click "Edit". Delete the contents of the "Password" box (************) and delete the contents of the "Confirm Samba Password" box, (also ************).

Click "OK" to confirm and to return to the previous screen.

Do the same for the account called "nobody".

You're done.

Reboot to make sure all the changes have taken effect, I'm sure someone will say this is not necessary or will suggest a way to get around it but what the hey......

When the machine is up and running, go to a Windows machine, sorry can't remember if you have one on your network, but if you do open "My network Places", click in the window somewhere to liven it up and press F5 to refresh the window. 

Your new Linux share will appear and you should be able to copy and paste files to the share.

Finally, smb4k.

I open the program on each Linux box and it will show all the machines in the workgroup and by clicking on a machine, the shares available. By clicking a share it mounts it so it's then available.

Let me know how you get on.

---

### Post by Dannylee on 2008-11-19
thanks everybody, but alanr8, i installed samba and the other packages like you said, but when i open a terminal and type in samba, it says that it could not be found.
what do i do?
please help
danny

---

### Post by Iowan on 2008-11-19
Samba is not really an executable command.  [This]("https://help.ubuntu.com/community/SettingUpSamba") page goes into more detail.
Also, [this]("http://ubuntuforums.org/showthread.php?t=202605") is another good Samba How-To.

---

### Post by AlanR8 on 2008-11-20
Dannylee

Don't you get a menu item for samba? On my Kubuntu boxes I get an item on the start menu /Applications/Settings and another under /System Settings then under the Advanced Tab.

---

