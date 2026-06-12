---
title: "Moving to Virtualbox not-OSE"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by bcoffield on 2009-12-29
Hi, I recently got Virtualbox all set up and working nicely to have access to xp in my 9.10 install.  The only issue I was having was the usb not working.  Upon searching I found that the open source edition doesn't have usb support....

So, if I export my appliance and then remove the OSE and install the closed source edition will I be able to import that appliance and will it be the exact everything as I had it?  My guess is yes, but I really would like to be sure before doing it because I've spent a good bit of time getting this xp to the point where it is now.  Thanks a lot!

---

### Post by zoglesby on 2009-12-29
I can't find anything that says you can't move from one to the other, but this is my suggestion if possible make a backup of your ~/.VirtualBox folder, if you have the extra disk space on your machine just do.
```
cp -r ~/.VirtualBox ~/VirtualBox.bkp
```
Then try to install the non open source version, if it work then your set if not reinstall the OSE and do the following
```
rm -rf ~/.VirtualBox
mv ~/VirtualBox.bkp ~/.VirtualBox
```

---

### Post by glubbdrubb on 2009-12-29
Do the back up as suggested by bcofield.

But there are two files that you must insure you back up: the virtual harddrive and the .VMDK file. Once you uninstall the OSE version and install the non-OSE version you should be able to simply import those two files.

Check this link for details: [http://www.linux-mag.com/cache/7631/1.html](http://www.linux-mag.com/cache/7631/1.html)

---

### Post by bcoffield on 2009-12-30
Thank you both so much for your help.  I did what you both said and felt very secure in removing the OSE version.  

I have everything up and working with USB support now and didn't lose my virtual machine in the process!

Actually all I had to do was remove the OSE version and then in order to avoid conflicts with installing the new version I had to remove some other packages.  Once that was cleared out I installed the Personal edition and whammo my virtual machine was in the list and I didn't even have to import it or overwrite the folder with my copied backup folder.  It was really quite seamless.

Thanks again!

---

### Post by glubbdrubb on 2009-12-30
Great to hear it works!
Could you mark this thread as resolved using the "Thread Tools" at the top of this page?

---

