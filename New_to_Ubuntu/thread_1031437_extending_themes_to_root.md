---
title: "extending themes to root"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by stonecoldjha on 2009-01-05
i know that themes ,eyecandy preferences are stored in the home directory of a user,but i would like the root too to make use of the same.for example,when i open the synaptic (which requires root previleges as i have to key in my password),it doesn't use those themes(my GTK theme) and looks ugly,the same happens when i launch nautilus using the command "sudo nautilus".
how do i do that?

---

### Post by lazyart on 2009-01-05
you would have to launch the appearance application as root.```
sudo gnome-appearance-properties
```

HOWEVER I would highly recommend against doing that.  As you probably know it's real easy to muck up your system as root.  Having a different theme for root would help you easily differentiate the windows.  If you've got nautilus already open as yourself, then launch one with sudo and for some reason you walk away, you might not instantly be able to tell which is which.  Then you do some copying and moving stuff around and you've trashed the permissions in your home folder... now you've got a mess that while it is fixable, you'll likely be booting to recovery mode to straighten it all out.

Doable? Yes.  Recommended?  No.  I thought about doing this some time ago but since backed away from it.  Yeah, the super-user windows are ugly, but you don't leave them open long.  In fact, being ugly make we want to close them right away.

---

### Post by jerrynewt on 2009-01-05
In terminal enter each of these commands one at a time.

sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.fonts /root/.fonts

that should set you up.

---

### Post by stonecoldjha on 2009-01-06
thanks,it did the job.btw,can you please tell me as to what those commands did?

---

### Post by jordanmthomas on 2009-01-06
> **stonecoldjha said:**
> thanks,it did the job.btw,can you please tell me as to what those commands did?

What this did was create symbolic links to your theme and icon folders in root's home folder.  A symbolic link is *sort of* like a shortcut in Windows, except that you can treat it like a normal file.
For example, try this:
```
ln -s /usr/bin ~/something
```
Now, you can cd ~/something and when you ls it'll show what's in /usr/bin.  If you pwd in ~/something it will show as ~/something and not /usr/bin.

I realize I may have just confused the issue a little, but in essence what happened is root's theme folder was linked to yours.

---

