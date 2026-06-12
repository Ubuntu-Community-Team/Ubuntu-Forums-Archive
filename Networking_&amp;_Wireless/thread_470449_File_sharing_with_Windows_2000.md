---
title: "File sharing with Windows 2000"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by cgaski on 2007-06-11
I have absolutely no knowledge of Linux or Ubuntu but thought that maybe I should remedy this situation so yesterday I downloaded the latest version of Ubuntu and installed it on a spare PC. 

I had no problems with this and Ubuntu seems to work very well although of course I am still feeling my way around it. 

I connected the machine to my router and can connect to the Internet with no problem but I need help with file sharing from the other two Windows 2000 machines on my, (wired), network. These two machines use NTFS and during installation I selected the default file system on the Ubuntu machine which I think was called ext3. 

I cannot see the Ubuntu machine from either of the two Windows machines but at the moment this is not a problem because of course there is as yet nothing on this machine to share. In any case I understand that the installation of an application called Samba will solve this problem. 

The Ubuntu machine can see the two Windows machines on the network and can see the shared folders on them. However when I try and open any of these folders I get a pop-up asking for authentication. 

There are three lines to be filled in the first being "User name". By default the name of the Ubuntu machine appears in this field. I have tried putting the name of the machine to which I am trying to connect in this field but it doesn't work - quite possibly because the other information is wrong. 

The second-line is "Domain" - by default MSHOME appears in this field - I suspect that this is where my problem lies as I'm not really sure what to put in here. I have tried using the names of the Windows machines, "workgroup", and the IP address of the router all without success. 

The third line is "Password" - I have tried the passwords for all three machines again without success. 

I have run out of ideas and would appreciate some help. 

David

---

### Post by cgaski on 2007-06-11
It seems from the fact that I haven't received any responses to my enquiry and from browsing similar threads that it is only possible to connect a Ubuntu machine to a Windows network by downloading various additional applications and inserting large quantities of, to me, incomprehensible code. 

I presume that the desktop Places/Network/etc is only for setting up networks of Ubuntu machines. If this is indeed the case it's a pity that this isn't mentioned in the help files. 

I'm disappointed that is apparently impossible for someone like me, who has no knowledge of the operating system, to connect a Ubuntu machine to a Windows network. Without this ability, whatever its other attractions, Ubuntu is of no use to me. 

Unless someone knows of a method of connecting to a network which doesn't involve lots of downloads and yards of code I will reluctantly have to abandon Ubuntu. 

David

---

### Post by Stian24 on 2007-06-11
Hello
First off all you need to install samba.
You can do this by going to the share folder menu in system settings.
If you haven't installed samba it will ask you for  to install it.
I think you have installed a firewall  like firestarter. you should first try to disable the firewall in ubuntu and see if the network starts to work. If that is the problem you need to enable samba sharing in your firewall.
Hope the problem gets solved

Post if you have any more questions and you can always try to ask questions at launchpad.net 
You can also read more at: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server)

---

### Post by merlinus on 2007-06-11
Have you tried searching for information on this forum and elsewhere?

This may help:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Networking](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Networking)

Good luck!

-merlin

---

### Post by cgaski on 2007-06-12
Many thanks for your responses. 

As you suggested I have installed samba and my configuration is generally as shown at: 

[http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html](http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html) 

On the Ubuntu machine if I click Places/Network I see two icons. One is "David3", (the name of the Ubuntu machine), and the other is "Microsoft Network" 

If I click the latter I see two icons, "MShome" and "Workgroup". Within Workgroup I see the Windows machines connected to my network. 

As I said previously I can see the shared folders on these Windows machines but if I try open any of them I get a pop up asking for User name, Domain and password. 

If I insert the name of the machine as User name, "Workgroup" as the domain and the password for the machine in question I get another pop up saying "The folder contents could not be displayed" 

Within MShome there is simply the icon for the Ubuntu machine. 

On any of the Windows machines if I go:-  My Network Places/Entire Network/Microsoft Windows Network I see two domains, MShome, (if the Ubuntu machine is connected ), and Workgroup. 

Within Workgroup I see the Windows machines on the network. In MShome I see the Ubuntu machine with the comment "David3 server (Samba, Ubuntu)". 

If I click this I get a pop up entitled Enter Network Password. Beneath this it says "Incorrect password or unknown user name for \ \David3" 

There are two fields "Connect as" and "Password". I have tried every combination of user names and passwords I can think of and none of them work. 

In summary: 

The Windows machines can see the Ubuntu machine but can't access it. 

The Ubuntu machine can see the Windows machines and the shared folders on them but can't access these folders. 

I think that I need to get the Ubuntu machine on to the Workgroup domain but can't see a way doing this. 

I would be very grateful for your further help, 

David

---

### Post by cgaski on 2007-06-12
I suspect from the lack of response to my request for help that it may not be possible to use a machine running Ubuntu and one running Windows 2000 on the same network. 

If anybody has indeed managed to achieve this I would be grateful for details. 

David

---

### Post by captaintrav on 2007-06-12
Open a terminal.

Try

"sudo gedit /etc/samba/smb.conf"

in the "global" section add this line:

"map to guest = bad user"

then at the bottom of the file, there is a section for each share.

add "guest ok = yes" to each share
and also "writable = yes" if you want read/write access.

---

### Post by cgaski on 2007-06-13
Many thanks for your response. 

I can now see, and indeed open, files on the Ubuntu machine from the Windows machines. I cannot however modify these files or copy files from the Windows machines into the Ubuntu machine. 

Although this is less important I still cannot open folders on the Windows machine from the Ubuntu machine - it just says that the files are inaccessible. 

I have put a copy  of smb.conf with the changes I have made highlighted in red at: 

[http://www.consul-net.net/smb.conf.odt](http://www.consul-net.net/smb.conf.odt)

(It's just too big to send as an attachment) 

I would be very grateful for any further suggestions. 

David

---

### Post by dave-ubu on 2007-06-13
HI

and excellent guide to samba and networking with windows is  :- [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Hope that helps

Regards

Dave

---

### Post by cgaski on 2007-06-13
Dave, 

Thanks for your response. 

I had in fact seen a posting with a reference to that Samba Networking Guide but I am a bit reluctant to start from square one again because, as you see from my previous posting, it's nearly working as it is. 

I'm hoping that someone can "Put the last brick in the wall" for me! 

David

---

### Post by nbelite on 2007-06-13
gotta same probleme... but version of windows is XP in my case.. looking forward for help

---

### Post by stchman on 2007-06-13
> **cgaski said:**
> I have absolutely no knowledge of Linux or Ubuntu but thought that maybe I should remedy this situation so yesterday I downloaded the latest version of Ubuntu and installed it on a spare PC. 

I had no problems with this and Ubuntu seems to work very well although of course I am still feeling my way around it. 

I connected the machine to my router and can connect to the Internet with no problem but I need help with file sharing from the other two Windows 2000 machines on my, (wired), network. These two machines use NTFS and during installation I selected the default file system on the Ubuntu machine which I think was called ext3. 

I cannot see the Ubuntu machine from either of the two Windows machines but at the moment this is not a problem because of course there is as yet nothing on this machine to share. In any case I understand that the installation of an application called Samba will solve this problem. 

The Ubuntu machine can see the two Windows machines on the network and can see the shared folders on them. However when I try and open any of these folders I get a pop-up asking for authentication. 

There are three lines to be filled in the first being "User name". By default the name of the Ubuntu machine appears in this field. I have tried putting the name of the machine to which I am trying to connect in this field but it doesn't work - quite possibly because the other information is wrong. 

The second-line is "Domain" - by default MSHOME appears in this field - I suspect that this is where my problem lies as I'm not really sure what to put in here. I have tried using the names of the Windows machines, "workgroup", and the IP address of the router all without success. 

The third line is "Password" - I have tried the passwords for all three machines again without success. 

I have run out of ideas and would appreciate some help. 

David

I have a procedure on my website for sharing files.

[http://www.stchman.com/share.html](http://www.stchman.com/share.html)

It worked well for me.

---

### Post by cgaski on 2007-06-14
> **stchman said:**
> I have a procedure on my website for sharing files.

[http://www.stchman.com/share.html](http://www.stchman.com/share.html)

It worked well for me.


Many thanks for that. 

The installation is simple and the instructions are very clear. 

Everything works in the installation process exactly as specified until I get to the last step: 

"You should then right click on the share and select Mount-->as SMB.  This will bring up a Nautilus file manager that will contain the shared drive files and folders" 

When I select Mount-->as SMB on any shared folder I get a pop-up which says "failed to mount". 

I have checked that Nautilus is where it should be and that the mnt folder has been created. 

I'm not sure whether I should have deleted the pre-existing smb.conf so I have not done so. 

I'll be very grateful for your suggestions as to what I might have done wrong. 

David

---

### Post by cgaski on 2007-06-14
> **stchman said:**
> I have a procedure on my website for sharing files.

[http://www.stchman.com/share.html](http://www.stchman.com/share.html)

It worked well for me.

Before I installed this I could open files on the Ubuntu machine from a Windows machine even though I couldn't edit them. 

Now when I try to connect to the Ubuntu machine from a Windows machine I get an error message that the server isn't started... 

Maybe this is related to the fact that I can't mount folders? 

David

---

### Post by stchman on 2007-06-25
> **cgaski said:**
> Many thanks for that. 

The installation is simple and the instructions are very clear. 

Everything works in the installation process exactly as specified until I get to the last step: 

"You should then right click on the share and select Mount-->as SMB.  This will bring up a Nautilus file manager that will contain the shared drive files and folders" 

When I select Mount-->as SMB on any shared folder I get a pop-up which says "failed to mount". 

I have checked that Nautilus is where it should be and that the mnt folder has been created. 

I'm not sure whether I should have deleted the pre-existing smb.conf so I have not done so. 

I'll be very grateful for your suggestions as to what I might have done wrong. 

David

Did you select a mount point in which you have both read and write access?  I put mine in my home folder:

~/mnt

I just tried it and it worked.

---

