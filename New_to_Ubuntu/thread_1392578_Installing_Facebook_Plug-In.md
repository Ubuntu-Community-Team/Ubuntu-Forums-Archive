---
title: "Installing Facebook Plug-In"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by mcgreenw on 2010-01-28
Sitting in my Downloads folder is the Facebook plugin, helpful for photo uploader and the sort. It is a .tar.gz file but I am at a loss for what to do with it. Obviously I need to unarchive it but where should that file go? I am currently running Google chrome and Hardy Heron 8.04. 

Thanks for any advice you can lend!

---

### Post by muffinboy on 2010-01-28
You should be able to just double click the file and open it with the Archive Manager.

---

### Post by mcgreenw on 2010-01-28
> **muffinboy said:**
> You should be able to just double click the file and open it with the Archive Manager.

I thought that too but I have it unarchived either way, the folder is now just sitting there but I don't know how to make the next step install the .so that I assume will fix the problem. I read the READMEs and the Install reads:

#!/bin/sh
#
# The most complicated, convoluted, complex installation
# in the history of the Internet.
#
echo -n "Copying libnpfbook_1_0_1.so to $HOME/.mozilla/plugins/libnpfbook_1_0_1.so..."
mkdir -p "$HOME"/.mozilla/plugins
cp libnpfbook_1_0_1.so "$HOME"/.mozilla/plugins/libnpfbook_1_0_1.so

if [ $? -eq 0 ]; then
echo " done."
else
echo " failed."
fi


But if I still have the file in "Downloads", don't I need to move it or make a directory for it somewhere?

---

### Post by muffinboy on 2010-01-28
CD into the directory where the libnpfbook_1_0_1.so is located, Copy and paste this into Terminal and press Enter:
> **mcgreenw said:**
> 
#!/bin/sh
#
# The most complicated, convoluted, complex installation
# in the history of the Internet.
#
echo -n "Copying libnpfbook_1_0_1.so to $HOME/.mozilla/plugins/libnpfbook_1_0_1.so..."
mkdir -p "$HOME"/.mozilla/plugins
cp libnpfbook_1_0_1.so "$HOME"/.mozilla/plugins/libnpfbook_1_0_1.so

if [ $? -eq 0 ]; then
echo " done."
else
echo " failed."
fi




It copies the file to where it needs to be, so the original in the downloads folder will still exist.

Then try to see if it works! :3

---

### Post by mcgreenw on 2010-01-28
> **muffinboy said:**
> It copied the file to where it needs to be, so the original in the downloads folder will still exist.

Have you tried to see if worked on Facebook?

I didn't run that install in Terminal, I just opened the .sh file and saw what it said. Does that make sense or am I just n00b rambling?

---

### Post by muffinboy on 2010-01-28
Run it in terminal.

Sorry i edited my post.

---

### Post by mcgreenw on 2010-01-28
Bam, success! Thank you! It's running fine in Firefox and I'll just do my uploading from there. Chrome is great but it has enough problems to where I'm not going to try and overload this onto it too. Thank you!

---

### Post by muffinboy on 2010-01-28
Your welcome. I'm happy to have helped.

=]

---

### Post by travelour on 2010-02-22
I ran it in terminal, but got a different result -- failure (see below).   Not sure what's happening.  The uploader used to work for me.  At some point it stopped, but I don't know when that was.  I can say that I tried to upgrade to Firefox 3.6.  Didn't like it and went back to 3.0.18.  I tried reinstalling the .so file after I realized it no longer worked...  

marcus@marcus-laptop:~$ echo -n "Copying libnpfbook_1_0_1.so to $HOME/.mozilla/plugins/libnpfbook_1_0_1.so..."
Copying libnpfbook_1_0_1.so to /home/marcus/.mozilla/plugins/libnpfbook_1_0_1.so...marcus@marcus-laptop:~$ mkdir -p "$HOME"/.mozilla/plugins
marcus@marcus-laptop:~$ cp libnpfbook_1_0_1.so "$HOME"/.mozilla/plugins/libnpfbook_1_0_1.so
cp: cannot stat `libnpfbook_1_0_1.so': No such file or directory
marcus@marcus-laptop:~$ 
marcus@marcus-laptop:~$ if [ $? -eq 0 ]; then
> echo " done."
> else
> echo " failed."
> fi
 failed.
 
Any advice would be greatly appreciated.

---

### Post by tom.swartz07 on 2010-02-22
> **travelour said:**
> I ran it in terminal, but got a different result -- failure (see below).   Not sure what's happening.  The uploader used to work for me.  At some point it stopped, but I don't know when that was.  I can say that I tried to upgrade to Firefox 3.6.  Didn't like it and went back to 3.0.18.  I tried reinstalling the .so file after I realized it no longer worked...  

marcus@marcus-laptop:~$ echo -n "Copying libnpfbook_1_0_1.so to $HOME/.mozilla/plugins/libnpfbook_1_0_1.so..."
Copying libnpfbook_1_0_1.so to /home/marcus/.mozilla/plugins/libnpfbook_1_0_1.so...marcus@marcus-laptop:~$ mkdir -p "$HOME"/.mozilla/plugins
marcus@marcus-laptop:~$ cp libnpfbook_1_0_1.so "$HOME"/.mozilla/plugins/libnpfbook_1_0_1.so
cp: cannot stat `libnpfbook_1_0_1.so': No such file or directory
marcus@marcus-laptop:~$ 
marcus@marcus-laptop:~$ if [ $? -eq 0 ]; then
> echo " done."
> else
> echo " failed."
> fi
 failed.
 
Any advice would be greatly appreciated.


The previous post was incorrect in saying to copy the contents of the file there. you should run the install file as a script instead.

you should open the archive, extract it. Then in a terminal, CD to that location and look for a install script
you could use ```
ls -l
``` to look for them in the folder
then all you need to do is ```
./"install script name"
```
99.9% of the time its called install.sh or similar.

---

### Post by Tibuda on 2010-02-22
I just would like to note that now you can use Facebook chat without any plugin, because Facebook is now using XMPP.

Instructions here:
[http://www.omgubuntu.co.uk/2010/02/facebook-chat-in-pidgin-empathy-with-no.html](http://www.omgubuntu.co.uk/2010/02/facebook-chat-in-pidgin-empathy-with-no.html)

EDIT: Sorry, this is not what you are looking for. I thought you were talking about the Pidgin plugin.

---

### Post by bernardomh on 2010-02-28
Hello everyone, this is what i did.
-Downloaded the file.
-Moved it to my home folder
-In the terminal

```

tar -xzf FacebookPlugIn-1.0.3.tar.gz
cd FacebookPlugIn-1.0.3
sudo chmod a+x FacebookPlugIn_Install.sh
./FacebookPlugIn_Install.sh

```

at the end of this process i got this result at the terminal.
Copying libnpfbook_1_0_3.so to /home/uhu/.mozilla/plugins/libnpfbook_1_0_3.so... done.
However i normally use Chrome and not Firefox, has anybody got an idea on how i can install the plugin to Chrome?
Thanx!

---

### Post by tom.swartz07 on 2010-02-28
> **bernardomh said:**
> Hello everyone, this is what i did.
-Downloaded the file.
-Moved it to my home folder
-In the terminal

```

tar -xzf FacebookPlugIn-1.0.3.tar.gz
cd FacebookPlugIn-1.0.3
sudo chmod a+x FacebookPlugIn_Install.sh
./FacebookPlugIn_Install.sh

```

at the end of this process i got this result at the terminal.
Copying libnpfbook_1_0_3.so to /home/uhu/.mozilla/plugins/libnpfbook_1_0_3.so... done.
However i normally use Chrome and not Firefox, has anybody got an idea on how i can install the plugin to Chrome?
Thanx!

Copy it the file (/home/uhu/.mozilla/plugins/libnpfbook_1_0_3.so) to the folder (you might need to make it) ```
~/.config/google-chrome/Plugins
```

That should take care of it!

---

### Post by amitevron on 2010-03-01
I followed the instructions to install the plugin but facebook still doesn't recognize it... Has anyone else had the same problem?

```
amit@amit-laptop:~/.mozilla/plugins$ ls -ltr
total 9360
-rwxr-xr-x 1 amit amit 9567556 2010-03-01 09:39 libnpfbook_1_0_3.so

```

---

### Post by Kike89 on 2010-03-03
I do

---

### Post by SlickRick on 2010-03-03
From what I understand, it doesn't matter if you use the script or just copy the plugin into the correct folder as it's only a single library file. I installed it but it doesn't work. I guess I'm stuck with the simple photo uploader for now.

---

### Post by samh785 on 2010-03-03
Having the same problem here. I ran the script, but facebook isn't recognizing it.

---

### Post by ericmitz on 2010-03-07
same here, here is the error i get when running firefox from the terminal.

```

(firefox:2971): GLib-WARNING **: g_set_prgname() called multiple times
LoadPlugin: failed to initialize shared library /home/eric/.mozilla/plugins/libnpfbook_1_0_3.so [/home/eric/.mozilla/plugins/libnpfbook_1_0_3.so: undefined symbol: idna_strerror]

```

---

### Post by dreamersword on 2010-03-07
You don't want to use the facebook plug-in anymore it won't work because facebook uses XMPP now.

[http://www.facebook.com/sitetour/chat.php](http://www.facebook.com/sitetour/chat.php)

---

### Post by linuxman94 on 2010-03-07
> **dreamersword said:**
> You don't want to use the facebook plug-in anymore it won't work because facebook uses XMPP now.

[http://www.facebook.com/sitetour/chat.php](http://www.facebook.com/sitetour/chat.php)

This post isn't about the facebook chat plug-in, it's about a facebook up-loader plug-in

---

### Post by mcgreenw on 2010-03-11
Naturally, I am having the same problem as the above users. I ran the script, it is in the plug-ins program and yet nothing. Did anyone find a solution other than just using the simple photo uploader? Damn you, Facebook.

---

### Post by jalirious on 2010-03-18
Bloom used to work well, but as of now it is ******.

---

### Post by jalirious on 2010-03-19
Ok, everything else failed - but there is a quick and easy way to upload photos to facebook using fspot.

Install F-Spot

Open F-Spot (Applications > Graphics > F-Spot Photo Manager)

Edit > Manage Extensions > Export (click on arrow to open menu) > Facebook Export > Enable (from right side) > Close

Selecting Images to Export to Facebook

Import (green plus sign) > Select Folder > Open
Select Images for export to Facebook
Photo > Export to > Facebook (This opens a new window)
Login > Opens browser for Facebook permission > Allow > Close
Close Windows “Waiting for Authentication”

Create New Album or Use Existing Album
Add Name, Location or Description (not required)
Add Caption (not required)
Add “In This Photo” (not required)

Add

Done

---

