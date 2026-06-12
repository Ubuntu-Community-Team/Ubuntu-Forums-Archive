---
title: "HOWTO: Easy File Sharing (both reading and writing, with NO passwords, but secure)"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by Yfrwlf on 2008-09-07
I wanted to have a file server and struggled with the best way to do so for a long time.  Linux permissions can be a pain and it can be difficult for a normal user to figure out how to get permissions doing what they need.  So, I hope this guide will help someone, as [COLOR="Blue"]it's the simplest way I can come up with to quickly share files as well as provide write access to anyone, without worrying about any passwords or administrator access of any kind[/COLOR].  [COLOR="Red"]All I'm going to be doing here, for those who understand it, is changing the default guest Samba user to the default user to allow ownership of all network-copied files, and making sure file ownership is set correctly.[/COLOR]

Set Up and Problem: File server is on a network with some Windows PCs as well as Linux ones (doesn't matter), and I'm going to be using Samba for simplified sharing.  In my setup, the file server is running a 2.3TB RAID5 array (very easy to set up using the Alternate Install CD) which also happens to function as a desktop computer for our HDTV (XBMC is great, btw!), and I want those files to be shared out and easily accessible.  I also want to allow users to write files to the server easily.

Other users will only be able to read the files you share out, and will only be able to write and have full control over certain folders if you grant it (I create an empty "Upload" folder for all uploads):

[COLOR="Blue"]Step 1[/COLOR]: Make sure device/folders/files are owned by you.  One way to do this is to go to where the folder/files/device is, and try to create some files there or copy/modify files there.  If you can, skip to step 2.  If you can't, or if you think that there may be a few files which aren't owned by you and should be, change the ownership of the folder (and all it's contents) you want to share to your user by doing either of the following:

A ) If you don't know how to use the terminal and navigate to the location of the folder you want to change permissions on, go to B, but if you do, navigate there now into the folder and skip B.

B ) Open Synaptic by going to System > Administration > Synaptic Package Manager, and do a package name search for "nautilus".  Install nautilus-open-terminal and/or nautilus-gksu.  Click apply and then after it's finished installing close Synaptic.  Go to System > Administration > System Monitor, go to the Processes tab, find nautilus, right click and select "end".  Nautilus should close and then restart automatically.  For those who don't know, this is your file manager, so if you have any file manager windows open, browsing your files, these will close, and a single window should come back up.  If it doesn't come back up, you can hit Alt-F2, type in nautilus, and that will restart it.  If you have any problems and somehow can't do anything, you may have to restart your GUI (Xorg) by hitting Control-Alt-Backspace.

Now, depending on which you did above, you will do one of two things:

A ) Right click on the folder you want shared out that you are having problems with permissions, and select "Open as Administrator" if you installed nautilus-gksu.  Put in your password.  You are now operating as root and have absolute permissions within **only this window**, so be careful!  Right click on the folder that you want to fully belong to you and select Properties.  Click on the Permissions tab, change the owner and group to your user name, and give yourself the permissions you want.  After this is done, be sure to click on "Apply Permissions to Enclosed Files" in order to own everything within that folder.  **Be sure to close this root file manager window when you are done**, and test to make sure you can now create folders/files in that folder like normal.

B ) If you installed nautilus-terminal, right-click on the folder and select "Open in Terminal".  You then need to type in the following:```
sudo chown -Rv username:username ../FolderName
```Be sure to spell the folder name exactly, and if there is a space, use "\ " for it, like:```
sudo chown -Rv yfrwlf:yfrwlf ../My\ Folder/
```Hitting TAB can help you autocomplete the name of the folder.  If you did it correctly, it will spit out a list of all your files and tell you which ones it had to change ownership on and which ones it didn't have to do anything.

[COLOR="Blue"]Step 2[/COLOR]: The hardest part is over if you got past, or don't need to get past, step 1.  Right click on a folder you want to share out, go to sharing, check share and guest access.  Then, for added security, create a new folder for "Uploading".  This will allow other users on your network to copy/move files to your server and gives them permission to modify or delete or move anything within this upload folder, but won't allow them or anyone else to freely delete any of the other files you have shared out.  To do this, create an upload folder where you want it, and in the sharing box for it be sure to also check "Allow other people to write to this folder".  Then, here's the tricky bit: If you want to then have full control over these uploaded files once they are copied to the server, so that they can be moved elsewhere and sorted out, without having to take on root/Admin access each time, you need to change the Samba guest user to your user's name.  Do this by opening a terminal, and typing:```
sudo gedit /etc/samba/smb.conf
```Scroll down (or do a search) until you see```
;   guest account = nobody
```The ";", like the other "#"'s in the document, makes the line a comment which means it will not be listened to.  Remove the ";", and change "nobody" to your user name.  Example:```
   guest account = yfrwlf
```> Note: While you're in here, if you'd like to change the Samba Workgroup that your file server will show up in, go to the line that says```
   workgroup = WORKGROUP
``` or whatever it says, and change the WORKGROUP to whatever workgroup you want.Save and exit gedit.  In the terminal, type:```
sudo /etc/init.d/samba restart
``` to restart Samba and have the settings take effect.

Now, any files which are copied to your upload folder by other users will be owned by you, and you can then manipulate them, move them elsewhere, etc, easily, but your other shared files are read-only and protected from modification.

Hope that helps someone somewhere. ^^

---

