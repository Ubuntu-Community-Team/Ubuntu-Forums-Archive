---
title: "Image Mount"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by YummyOlives on 2011-01-15
hi guys 

i finally managed to install the Ubuntu on a separate partition and loving it , 

a little problem with mounting some applications images,

the application i would like to launch is installed on the vista partition and image to mount is also located in that partition, now how to launch that app in ubuntu ? 

What i have tried: 

g-mount, but it didn't manage to load that iso-image, probably because of the application being in the vista partition and not in the linux, 

please advise

---

### Post by bodhi.zazen on 2011-01-15
Not really sure what you are trying to do.

You can mount the iso from the command line but Linux is not windows so your Windows application is unlikely o run at all.

---

### Post by Smart Viking on 2011-01-15
How to mount iso files:

```
sudo mount -o loop /file/to/mount.iso /where/to/mount/
```

---

### Post by YummyOlives on 2011-01-15
thanks

but please clarify this for me 

whats the 'mount to'  function ?

its the same like G-mount ?

cause if i use 'mount to' to some random location or even in vista partition, the app.exe doesn't recognizes anything 

?

---

### Post by Smart Viking on 2011-01-15
> **YummyOlives said:**
> thanks

but please clarify this for me 

whats the 'mount to'  function ?

its the same like G-mount ?

cause if i use 'mount to' to some random location or even in vista partition, the app.exe doesn't recognizes anything 

?

The "app.exe" is a windows program. it is not designed to work in linux.

You can install wine, and try to run it in a simulated windows environment, but you might not get it to run.

---

### Post by YummyOlives on 2011-01-16
> **Smart Viking said:**
> The "app.exe" is a windows program. it is not designed to work in linux.

You can install wine, and try to run it in a simulated windows environment, but you might not get it to run.


yes i am using wine1.3 to run the application but along with that i need to mount disk1 image to be able to run the app.

so wine is installed and properly launching the application but at the loading screen it asks for the disk1, which i already mounted through Gmount (iso), *not recognizing the iso.image, or maybe i dont know how to use the mount-to function, 

again  application is installed in the vista partition and launches correctly with the help of wine.

also iso image for that application is in the vista partition as well.

:confused:

---

### Post by bodhi.zazen on 2011-01-16
Using the iso in Linux and suing the iso in wine are two completely separate things.

I can not tell from your post where the problem is.

Step 1: Mount the iso.

Let us pick a mount point, say /media/iso , you can change the name of the mount point if you wish.

```
sudo mkdir /media/iso
sudo mount -o loop /file/to/mount.iso /media/iso
```

Or you can use gmount if you want, but you need to know where you mounted it.

Step 2: Use the iso in wine.

You can do this again with the command line

```
cd ~/.wine/dosdevices
ln -s /media/iso d:
```

If that does not work, you will have a lot of reading ahead of you. In general some windows applications work in wine, and some do not. Sometimes you need to do fairly extensive configuration.

You will need to read how wine works, look up the application you are using in the wine application data base

You will need to learn how to use a cdrom and/or iso in wine, etc.

See also winecfg

[http://appdb.winehq.org/](http://appdb.winehq.org/)

But without you telling us more about what you are doing it is impossible to give you more specific instructions. As I said, I really can not tell from your post if you are having a problem with linux (ie can not mount the iso) or wine (wine does not use the iso).

Keep in mind, Linux is not windows and running applications in wine is often complicated.

You may wish to dual boot for this application or use Virtualbox.

---

