---
title: "Issues mounting /home"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by SlightlyChaotic on 2011-04-03
I recently had to re-install ubuntu. I'm booting from a portable hard drive. When I re-installed, I decided to change the partition sizes a bit (I don't know if that's relevant at all), but I set the mount points to be  the same as they were previously.

Now, I'm getting an error message upon bootup that says it can't mount /home, then asks if I want to skip mounting or do it manually. I have no idea what to do for manual mount, but when I skip I get these error messages (which I assume only pop up because /home didn't mount):

"Could not update ICEAuthority file /home/[my user name]/.ICEauthority"
"There is a problem with the configuration server. (/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)"
"Nautilus could not create the following required folders: /home/[my user name]/Desktop, /home/[my user name]/.nautilus"

And then, I get the ubuntu default wallpaper but no toolbars. Is there a way to fix it?

---

### Post by oldfred on 2011-04-03
This will show all your files, so we can see if something is wrong. It not really a boot issue per se, but a file issue.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

If it is mounted, did you change username?:
Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
#Replace all instances of username with your login name or use $USER
sudo chown username:username /home/username/.dmrc
chmod 644 /home/username/.dmrc
sudo chown username:username /home/username     
chmod 755 /home/username

.ICEauthority errors
[http://ubuntuforums.org/showthread.php?p=6161267](http://ubuntuforums.org/showthread.php?p=6161267)
[http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)
sudo chown $USER:$USER /home/username/.ICEauthority
sudo chmod 644 /home/username/.ICEauthority
sudo chmod 600 $HOME/.ICEauthority

---

### Post by SlightlyChaotic on 2011-04-03
Ok cool, but how am I supposed to use the script when I have no toolbars and thus can't open up any programs?

Is there a shortcut to open the terminal and then download the file from there? 

I'm brand new to ubuntu so I don't know squat. I'll need to be walked through this like a n00b.

---

### Post by oldfred on 2011-04-03
It works find from LiveCD. You just will not save it if you reboot, unless you copy it elsewhere.

---

### Post by ditzola on 2011-05-03
_you can edit your partition size in dos mode just try it_[U]..
[/U]

---

### Post by Nerotriple6 on 2011-05-03
Can you see the hard drive if you press "m" for manual mount and at the command line prompt enter
```
sudo fdisk -l
```
This should list all the partitions and drives detected by Linux.
Are your drives IDE or SATA? It doesn't appear to detect the drive/partition at the adress listed in /etc/fstab file.

---

