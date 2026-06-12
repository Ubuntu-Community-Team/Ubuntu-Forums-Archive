---
title: "network folder visible in file manager, but not in  program/open"
date: 2021-04-10
forum: Networking &amp; Wireless
---

### Post by cmacc77 on 2021-04-10
my usb hard drive connected to my router is now showing up in the file manager.  I'm trying to open an audacity file, in audactiy, but when I open the open button, i can only browse local folders.

---

### Post by hk42 on 2021-04-10
To have full access to a network disk you have to mount it on a mount point with an entry in /etc/fstab
The trick used by file managers only allows limited action from inside the file managers.

---

### Post by deadflowr on 2021-04-10
Most likely a snap issue,
see [https://forum.snapcraft.io/t/difficulty-viewing-mounted-fileystems-via-samba-nfs-gvfs-interface/14680]("https://forum.snapcraft.io/t/difficulty-viewing-mounted-fileystems-via-samba-nfs-gvfs-interface/14680")
about a general discussion on this.

I don't know of a workaround for this,
but you should be able to remove the snap version and install the apt version.
```
snap remove audacity
```
```
sudo apt install audacity
```

---

### Post by CelticWarrior on 2021-04-10
The above notwithstanding, if you installed the Audacity via snap then like any other snap the default is local access only. Please open the software app, search Audicity and if it is a snap you'll see a huge red Permissions button in its page. Click it to enable additional permissions. Everything should be self-explanatory.

---

### Post by cmacc77 on 2021-04-10
the uninstall and reinstall were successful but stil can't open files from the network location

---

### Post by Morbius1 on 2021-04-11
After you connect to the network folder in Nautilus it will be mounted under: **/run/user/1000/gvfs**

If you make a bookmark in Nautilus to the "gvfs" folder it will show up under Audacity. But you have to connect to the share first in Nautilus.

---

### Post by cmacc77 on 2021-04-11
how do i bookmark the gvfs folder?  I typed the path you put below and it was not found.  I made a bookmark to the network folder, which showed up in the file manager, which i assume is Nautilus?, and the network drive was not available in audacity.

---

### Post by CelticWarrior on 2021-04-11
Yes, it seems Audacity wants local files only. It actually makes sense.

---

### Post by Morbius1 on 2021-04-11
** First I connected to the "public" share of an Ubuntu server ( vubsrv2004 ) in Nautilus.

** Then I go to /run/user/1000/gvfs in Nautilus:
[ATTACH=CONFIG]288277[/ATTACH]

** On the side panel of Nautilus I will see the link to the mount:
[ATTACH=CONFIG]288278[/ATTACH]

** If I right click that I can create a bookmark:
[ATTACH=CONFIG]288279[/ATTACH]
** If I now to to Audacity > Open  > Other Locations > I will see the Bookmarked mount point:
[ATTACH=CONFIG]288280[/ATTACH]

---

### Post by cmacc77 on 2021-04-11
step 1.  how do i complete step 1?

I went to the network folder i'm trying to access, is that right?

step 2.
I was able to navigate to here.

step 3:
there was no link to mount

step 4:
there is not option to create a bookmark on right click.  I tried to insert a screen shot here but the only option is via url

---

### Post by deadflowr on 2021-04-11
> I tried to insert a screen shot here but the only option is via url

Use the attachments feature to upload the screenshot.
(Use the Reply to Thread and select the paperclip icon in the toolbar.
Then select the Add file option and upload the screenshot from your computer.
It'll automatically add it to the field, so you can usually just click ok and it'll be done)

---

### Post by Morbius1 on 2021-04-11
Can you do this:
[ATTACH=CONFIG]288283[/ATTACH]

---

### Post by cmacc77 on 2021-04-11
figured it out, it worked.  thanks dude

---

