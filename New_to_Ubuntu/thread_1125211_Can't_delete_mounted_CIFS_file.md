---
title: "Can't delete mounted CIFS file"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by LarryJ2 on 2009-04-14
I have a Ubuntu 8.04 PC which I use as a server.  On it,  I have a shell script which downloads several podcasts to directory named "podcasts".  In gnome on this server PC,  I right click on the directory and indicate I want to share the directory as "podcasts" and allow all to read and write to the directory.

From my Laptop, I can mount and see all the files using my laptops  Nautilus filemanager. I can play any of the media files OK.  But I cannot DELETE or move to trash any of the files I've listened to after I am done with them.  When I attempt to delete a podcast file from within Nautilus on my laptop,  I get a weak error message, "File Input Output Error"

After three years of Linux,  I thought "permissions" but on the server  as seen from my laptop, the mounted "podcasts" directory shows as 777 (drwxrwxrwx 35 lj lj      0 2009-04-14 03:45 )  The user and owner on both laptop and server is lj.

What do I have to do to be able to delete a file from the shared server directory from my laptop using nautilus?

Larry

---

### Post by LarryJ2 on 2009-04-14
Good grief!  That was ugly but I accidentally did something right because now I can now delete a file which was shared from my server  from my laptop within Nautilus.  

What did I do?  I'm not really sure but I attempted to remove everything connected with samba except the gnome desktop which snyaptic offered to do. I then installed ( using  'sudo apt-get install system-config-samba')  System->Admin->Samba. Then from within that  gui, (System->Admin->Samba) I deleted all my shared folders and then shared them out again.  

I also installed samba swat.  But other than editing the /etc/xinetd.d/swat file  to enable swat  by putting your firefox to [http://localhost:901](http://localhost:901),  I just looked at the configuration file and shook my head.  Very complicated.  But something I did along the way, fixed the problem so I hope this helps you too.

Larry

---

