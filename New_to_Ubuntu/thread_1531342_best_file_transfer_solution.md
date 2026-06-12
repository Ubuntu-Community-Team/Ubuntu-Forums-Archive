---
title: "best file transfer solution?"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by ubscott on 2010-07-14
hi,
 
i'm new here. i have been researching this topic via the search engine, so i hope i'm not repeating an existing thread.
 
i want to have a couple of Ubuntu PCs and a Windows network. i want to be able to transfer files between the Ubuntu and Windows machine. (this is particularly true with images and other media files that i download from a Ubuntu machine.)
 
i've gotten started with Ubuntu. i now have a Ubuntu box. i've configured Real VNC on a Windows machine that enables me to take control over the Linux machine.
 
however, i haven't figured out how to transfer files between the Windows and Linux machines using Real VNC.
 
I understand i can connect a USB device to one and copy data to it, then upload it to the other machine. however, i'm hoping for a solution without external storage.
 
i also understand i can use SFTP and copy files from the Linux machine to some server, then on the Windows side download them. However, this seems bandwidth intensive.
 
I also know about dual-booting. however, i haven't figured out if that helps you transfer files or not.
 
so what's a good strategy to use that enables to transfer files from Windows to Linux and vice versa? 
 
thanks.

---

### Post by CharlesA on 2010-07-14
you cannot transfer files between Windows and Linux using any kind of file transfer in VNC, it's a Windows only thing as far as I know.

You could use sftp or scp to transfer files, or throwing them on a thumb drive to move between machines.

You can use sftp to copy files from a linux box directly to the Windows box. You can use something like Filezilla to do so.

---

### Post by ubscott on 2010-07-14
thanks.  this is helpful.  
 
i'll focus on the Filezilla solution.

---

### Post by belkinsa on 2010-07-14
Make sure you mark this "SOLVED"

---

### Post by masque7 on 2010-07-14
Fundamentally the VNC protocol sends an image of 1 desktop to another. It then says you've sent a request to move the mouse in 1 direction or the other and then implements that on the hosts screen, and then sends the image back to the clients. It does not provide file transfer. It's remote connectivity.
 
Whilst (s)FTP and SCP are methods that are great for grabbing files off of external computers, what you need to do is get all your computers onto a network where they're all talking to each other. The small complication here is that you have Linux, and Windows. Ideally you want to be able to share files; read them, write them, edit them.. transfer them. Hey, why not share a printer, too?

Linux can read Windows partitons, both FAT and NTFS. If I point you in the right direction without writing a book on home network shares, you should be good to go. 

You need to download (or get the rest of) the SAMBA software found in your Synaptic package manger. Read more about SAMBA written by the Ubuntu team [here]("https://help.ubuntu.com/community/SettingUpSamba") and [here]("https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html"). 

For some tutorials to get Linux and Windows shares going together, I found some here on our forums but they're quite old, but probably still relevant. Maybe see if you can find some more up-to-date ones, or maybe google for some.

[**HOWTO: Setup Samba peer-to-peer with Windows**]("http://ubuntuforums.org/showthread.php?t=202605[URL=%22http://ubuntuforums.org/showthread.php?t=202605[/URL%22")

[**How to share files using Samba (the more secure way)**]("http://ubuntuforums.org/showthread.php?t=26438&highlight=samba+howto[URL=%22http://ubuntuforums.org/showthread.php?t=26438&highlight=samba+howto[/URL%22")

---

### Post by 3rdalbum on 2010-07-14
As far as I can tell, you haven't really been given advice in enough detail to actually solve your problem.

The solution I would suggest would be to set up "Samba" file sharing on the Linux computer. This is basically the method that Windows computers use to do file sharing, so you can transfer files Linux-to-Linux and Windows-to-Linux this way.

Most people don't know this, but Ubuntu's included documentation shows you how to do this. Click on the Help icon on your top panel or go to System > Help And Support, then click on Internet And Networks, and then "Share Files and Folders with other computers". Use the method that involves running the "shares-admin" program.

Then Windows' own network browser should be able to detect your shared folders on the Ubuntu machine and then interact with them.

---

### Post by ubscott on 2010-07-15
3rdalbum and masque7, thanks for the help!  i now have a much clearer idea how to proceed.
 
btw, i'm not sure how i mark a thread as 'closed', but i think i've got enough info to get working.

---

### Post by YesWeCan on 2010-07-15
Top of this page, "Thread Tools", mark as solved.

Another way: if you can see your ubuntu desktop from your windows machine, using vnc, then you can just use built-in Nautilus:
Places->Connect to server->windows share
You just add a Windows network shared folder (that you created on your windows machine) to your ubuntu desktop and drag and drop files to it. Very simple for manual file transfers.

---

