---
title: "Windows Network Login"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by Mad_Max_1412 on 2007-07-01
Hi Guys,

I've just installed Ubuntu 7.04 onto a new computer for 2 reasons:

1) To learn about Ubuntu
2) To use it as a NAS for my digital TV shows recorded on my Windows computer

Anyway, during the installation I said for it to call the system "Ubuntu" and the Administrator will be username "Max" and password of "so1357".

I then went to the "System" pulldown menu and selected "Shared Folders" so I could create a folder to put these TV files into.

In the "Share Folder" dialogue box, I selected "Other" and created a new folder called "Ubuntu_Videos" so now the "Max" directory shows 3 folders: "Desktop", "Examples" and "Ubuntu_Videos". 

Also under the "Shared Folder" dialogue box I went to the "General Properties" tab and changed the "Domain/Workgroup" to "NECAU" as this is what my 2 windows computers have as the workgroup.

Now when I go to my Windows machines and open my "Explorer" I can go down to "My Network Places" and under "NECAU" see the Ubuntu computer.

Unfortunately when I click on it, hoping for it to show me the "Ubuntu_Videos" directory, I get prompted for my username and password.  I enter "max" and "so1357" but it doesn't accept it.

Any ideas on what I'm doing wrong?  I've uploaded a screenshot.

By the way, connecting to the Ubunut computer via VNC was so easy and I'm so impressed by that.

Regards

Max

---

### Post by conjur3r on 2007-07-01
The step that you've missed is to add a user account in Samba.  It doesn't operate from the same accounts database as the system.  Open up a terminal and add your account "Max"

# smbpasswd -a Max

It will prompt for a password.  This can differ to the system one you have - or it could be the same, up to you.  Then try again on your windows box.

---

### Post by Mad_Max_1412 on 2007-07-01
Many thanks.  Initially it wasn't prompting me for a password, just kept giving me a list of the options and then I realised that the start of each line was:

max@ubuntu:~$ 

So I had a quick look at a tutorial for NAS and it said to configure Samba you had to log in as Administrator and to do this type

sudo bash

Once I did this, the prompt became:

root@ubuntu:~#

And my entry then worked (ie prompted for a password) and now my Windows machine can see the "Ubuntu_Videos" directory.

Now I just need to work out why my Zensonic Media Player won't see it when I select SMB.  I thought it just looked for any SMB shared computers.  Perhaps it's because the Ubuntu machine doesn't have an IP address allocated.  It's not much good having a NAS when the Zensonic Media Player can't see the repository of files.

Cheers and thanks for your help.

---

