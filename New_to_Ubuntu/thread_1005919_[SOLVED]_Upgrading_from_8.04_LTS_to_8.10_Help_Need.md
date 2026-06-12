---
title: "[SOLVED] Upgrading from 8.04 LTS to 8.10 Help Needed"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by stefandwight85 on 2008-12-08
Hi All,

I am trying to upgrade from 8.04 LTS to 8.10. When i run the Upgrade Manager it goes through to Setting New Software Channels and then flags this error

> The upgrade aborts now. The upgrade needs a total of 62.9M free space on disk '/boot'. Please free at least an additional 44.7M of disk space on '/boot'. Empty your Deleted Items folder and remove temporary packages of former installations using 'sudo apt-get clean'.

What can i do to get round this?

Cheers in advance

Stefan

---

### Post by bobbob1016 on 2008-12-08
No way to "get around" this that I know of.  Might be able to unmount /boot, and resize it, or delete some of the leftover kernels in there.  It *should* be safe to go into your /boot folder, and remove everything but the newest kernels, as in remove initrd.img-2.6.27-7-whatever, if there is -2.6.27-8-whatever.  That *should* be ok.

---

### Post by Therion on 2008-12-08
> **stefandwight85 said:**
> Hi All,

I am trying to upgrade from 8.04 LTS to 8.10. When i run the Upgrade Manager it goes through to Setting New Software Channels and then flags this error



What can i do to get round this?

Cheers in advance

Stefan
Well, have you tried emptying your Deleted Items folder and removing temporary packages of former installations using 'sudo apt-get clean'?

Do you have the necessary disk space on your hard drive?  If you don't you need to make room.  

There's really no "getting around" not having enough room to install.

---

### Post by damis648 on 2008-12-08
Please read the error and then you will realize what the problem is: you are out of space. (On /boot, that will most likely be on / unless partitioned otherwise). Try in terminal to free some space:
```
sudo apt-get clean
sudo apt-get autoremove
```
and also empty your trash.

---

### Post by stefandwight85 on 2008-12-08
> **bobbob1016 said:**
> No way to "get around" this that I know of.  Might be able to unmount /boot, and resize it, or delete some of the leftover kernels in there.  It *should* be safe to go into your /boot folder, and remove everything but the newest kernels, as in remove initrd.img-2.6.27-7-whatever, if there is -2.6.27-8-whatever.  That *should* be ok.

I have tried to do this but it says

> rm: remove write-protected regular file `abi-2.6.20-16-generic'? y
rm: cannot remove `abi-2.6.20-16-generic': Permission denied


---

### Post by stefandwight85 on 2008-12-08
> **damis648 said:**
> Please read the error and then you will realize what the problem is: you are out of space. (On /boot, that will most likely be on / unless partitioned otherwise). Try in terminal to free some space:
```
sudo apt-get clean
sudo apt-get autoremove
```
and also empty your trash.

i have also tried this, i know that there is plenty of free space ~10+GB

---

### Post by stefandwight85 on 2008-12-08
sorted it needed sudo first before rm

thanks anyway guys :)

---

### Post by pastalavista on 2008-12-08
If you plan to upgrade, you should also first open (System > Administration >) Synaptic Package Manager. Search for linux-image and completely remove all the installed ones except the latest. Then go into Software Sources on the Update tab, at the bottom, select normal releases instead of long-term releases. Then just run update-manager again.

---

