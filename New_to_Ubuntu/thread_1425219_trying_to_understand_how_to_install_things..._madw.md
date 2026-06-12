---
title: "trying to understand how to install things... madwifi drivers"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by mikeeey on 2010-03-08
So I'm still trying to get used to linux, but I'm not familiar with how things install. I'm trying to get my WLL4030 Wireless USB adapter to work, and doing some google searching I found that I need to install madwifi drivers. Well browsing through the madwifi folders confused the hell out of me, and trying to understand the tutorials (like this one: [http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html))
keep in mind I'm a windows user, I'm used to just clicking on setup.exe lol :p
Is there any simple way to install madwifi?

I'm off to work now so I'll do some more researching and see what I can find.

**edit:**if it helps, this is the usb adapter I have:
[http://www.airlink101.com/products/awll4030.php](http://www.airlink101.com/products/awll4030.php)

---

### Post by harrisonk on 2010-03-08
[SIZE=2]Hello

If you find a .deb file that is what you most likely are looking for, a .deb is basically the same as a .exe file so you can download and double click like in windows. You most likely will get a window that has install in the top right corner you would click that type your password and wooppy your flying.

Now this most likely will apply to other software but you might get a pop-up window that says, "that there is an older version in the repositorys" this means that there is a previous version on the Ubuntu software servers, this isn't that important but just something to know.

If this is confusing let me know.

Harrison
[/SIZE]

---

### Post by mikeeey on 2010-03-09
ah alright I understand.
and it looks like the madwifi drivers aren't in .deb format anywhere, but I found this easier guide:

[http://dimitar.me/madwifi-drivers-for-ubuntu-9-10-karmic-koala-or-linux-kernels-2-6-29-and-above/](http://dimitar.me/madwifi-drivers-for-ubuntu-9-10-karmic-koala-or-linux-kernels-2-6-29-and-above/)

Now the only thing I'm unsure how to do before I install it is specify the correct directory. I can't seem to copy and paste anything into the linux filesystem folder, but I can paste things onto the desktop. Only problem Is idk what the directory name for my desktop is.
So if I have this code according to the guide:
```
tar -xvzf madwifi-trunk-r4099-20090929.tar.gz
```
(I'm assuming the directory is supposed to be in places of -xvzf? or is -xvzf a real command?

Where are some different places that I'm able to put the file? What is the directory name of the desktop? Can I use a directory that is on the windows partition of the harddrive? I found I'm able to explore there anyway.

Thanks for helping me out through all my noob questions, I understand how frustrating it can be lol

---

### Post by nothingspecial on 2010-03-09
-xvzf are arguments(options) you pass to the command tar.

Most commands have arguments

Type ```
man tar
``` for an explanation.

You need to be in the directory the tar archive is in. So if it is on your Desktop
```

cd ~/Desktop
tar -xvzf madwifi-trunk-r4099-20090929.tar.gz
```

Or if you are somewherelse you need to specify the full path (tell tar that the thing you want to untar is on your Desktop)

```
tar -xvzf ~/Desktop/madwifi-trunk-r4099-20090929.tar.gz
```

Madwifi drivers have been available since Jaunty. You should be able to switch to them in system > administration > hardware drivers

ath_pci are the madwifi drivers
ath5k are the default ones (from memory, I could be wrong)

---

### Post by mikeeey on 2010-03-10
I finally did it! I'm on the internet on ubuntu for the first time, typing this post right now!

I ended up using this guide:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)


Thanks again everyone, now I'm a bit more familiar with Ubuntu, atleast more than I was 2 days ago. I knew absolutely nothing at the time.


edit: how do you change the prefix of a topic? I'd like to change it to SOLVED

---

### Post by anewguy on 2010-03-10
Just use the "Thread Tools" option before the 1st post on your thread.

---

### Post by 3rdalbum on 2010-03-10
> **mikeeey said:**
> 

Now the only thing I'm unsure how to do before I install it is specify the correct directory. I can't seem to copy and paste anything into the linux filesystem folder, but I can paste things onto the desktop. Only problem Is idk what the directory name for my desktop is.
So if I have this code according to the guide:
```
tar -xvzf madwifi-trunk-r4099-20090929.tar.gz
```

If you drag a file or folder onto the terminal, it will fill in the path for you. So you could type:

```
tar -xvzf 
```

put a space, and then drag the madwifi-trunk-etc.tar.gz file onto it.

You can change directories in the same way, by typing 'cd', then a space, and then drag the folder onto the terminal.

---

