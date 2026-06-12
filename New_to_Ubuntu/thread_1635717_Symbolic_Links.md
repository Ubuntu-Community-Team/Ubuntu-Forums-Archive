---
title: "Symbolic Links"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by r.peel on 2010-12-02
Hi,

I'm wanting to store my /home files on an NTFS drive to allow it to be shared with Windows and also to separate my data from the OS so I can re-format at will.

I've tried and failed to mount an NTFS drive as /home but stubled across something abut symbolic links which looks promising. Would it be possible to create a link between, /home/<user> and /files/<user> so all the files are saved in /files/<user> but Ubuntu and any applications think they are saving to /home/<user>?

How would I do this?

---

### Post by AngusH on 2010-12-02
Whilst I'm sure you could do what you wanted could you not make /home an ext partition and then read it from windows using this: [http://www.fs-driver.org/](http://www.fs-driver.org/)
If you need help with making a separate /home partition then check out this: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by coffeecat on 2010-12-02
> **r.peel said:**
> I've tried and failed to mount an NTFS drive as /home but stubled across something abut symbolic links which looks promising. Would it be possible to create a link between, /home/<user> and /files/<user> so all the files are saved in /files/<user> but Ubuntu and any applications think they are saving to /home/<user>?

This is a perfectly valid idea, and easily achieved. First a couple of questions. When you say NTFS drive, do you mean an NTFS partition on an internal drive rather than an external drive? Also - to do this properly the partition needs to be mounted at bootup with an entry in /etc/fstab. Have you done this yet?

Anyway, there are two ways of making symbolic links. 

1 - from the terminal for which we need the exact path and partition mountpoint.

2 - Using the GUI.

I'll take you through 2, and we can come back to the terminal if need be.

First, make sure the NTFS partition is mounted. Double-click on the desktop icon to open a nautilus browser window. Select a folder for which you want a symlink. Let's assume this is 'Music'. Right-click on the Music folder and select 'Make Link'. A new folder will appear called 'Link to Music' with an arrow on the folder icon. Now open your home folder and drag and drop the 'Link to Music' folder across to the home folder. A new link folder will be created in your home folder and if you open it you will see that it contains exactly what you want - all the contents of the 'Music' folder. You will be able to read and write to the link folder as though you are read and writing to the Music folder.

You can now delete the original 'Link to Music' folder in your NTFS partition and rename the link folder in your home partition if you wish. Simply repeat for every folder in your NTFS partition that you want links for.

If you want help with /etc/fstab, simply post back.

By the way, the fs-driver that the previous poster mentions will be no use to you. It does not support the ext4 filesystem now used by Linux. There is, I believe, an ext4 driver now available for Windows but I don't know how reliable it is and, personally, I would not have Windows rummaging around in my Linux filesystems. Your idea of a separate NTFS partition and symlinks is a good one, and one I have used in the past. You could then take this to its logical conclusion and make shortcuts in your Windows home folder as well. :)

---

### Post by mcduck on 2010-12-02
> **r.peel said:**
> Hi,

I'm wanting to store my /home files on an NTFS drive to allow it to be shared with Windows and also to separate my data from the OS so I can re-format at will.

I've tried and failed to mount an NTFS drive as /home but stubled across something abut symbolic links which looks promising. Would it be possible to create a link between, /home/<user> and /files/<user> so all the files are saved in /files/<user> but Ubuntu and any applications think they are saving to /home/<user>?

How would I do this?

Yes, although linking between /home/*user*/ and any location that is on NTFS will just give you the same problems as mounting that NTFS location directly as /home/user would, namely the NTFS's lack of support for file ownerships and permissions as Linux uses them. And certain files in your home are required to have correct ownership and permissions...

What you *can* do is instead of trying to link anything to /home/*user*/ you should link to it's *subdirectories*. For example /home/*user*/Documents <-> /files/*user*/documents/

---

### Post by r.peel on 2010-12-03
> **coffeecat said:**
> This is a perfectly valid idea, and easily achieved. First a couple of questions. When you say NTFS drive, do you mean an NTFS partition on an internal drive rather than an external drive? Also - to do this properly the partition needs to be mounted at bootup with an entry in /etc/fstab. Have you done this yet?

Anyway, there are two ways of making symbolic links. 

1 - from the terminal for which we need the exact path and partition mountpoint.

2 - Using the GUI.

I'll take you through 2, and we can come back to the terminal if need be.

First, make sure the NTFS partition is mounted. Double-click on the desktop icon to open a nautilus browser window. Select a folder for which you want a symlink. Let's assume this is 'Music'. Right-click on the Music folder and select 'Make Link'. A new folder will appear called 'Link to Music' with an arrow on the folder icon. Now open your home folder and drag and drop the 'Link to Music' folder across to the home folder. A new link folder will be created in your home folder and if you open it you will see that it contains exactly what you want - all the contents of the 'Music' folder. You will be able to read and write to the link folder as though you are read and writing to the Music folder.

You can now delete the original 'Link to Music' folder in your NTFS partition and rename the link folder in your home partition if you wish. Simply repeat for every folder in your NTFS partition that you want links for.

If you want help with /etc/fstab, simply post back.

By the way, the fs-driver that the previous poster mentions will be no use to you. It does not support the ext4 filesystem now used by Linux. There is, I believe, an ext4 driver now available for Windows but I don't know how reliable it is and, personally, I would not have Windows rummaging around in my Linux filesystems. Your idea of a separate NTFS partition and symlinks is a good one, and one I have used in the past. You could then take this to its logical conclusion and make shortcuts in your Windows home folder as well. :)

Thanks, my preference was not to have to use a driver in Windows to access a EXTx partition.

I'd already been doing this in Windows for years but couldnt find a tutorial to simply move the /home/<user>/xyz folders in Linux.

My ultimate goal is to setup a NAS which will sync with the folders on my hard drive in both Linux and Windows.

---

### Post by coffeecat on 2010-12-03
mcduck made an important point. I had assumed in my post that you wanted to make symlinks for subfolders - Music, Videos, etc - and what I describe works fine for this. But you can't have the whole of your home on the NTFS drive symlinked to your /home on your root partition. There are hidden files and folders in /home with special permissions, as mcduck points out, which NTFS doesn't support. But your ordinary documents, MP3's and whatever will be fine.

---

### Post by r.peel on 2010-12-03
> **coffeecat said:**
> mcduck made an important point. I had assumed in my post that you wanted to make symlinks for subfolders - Music, Videos, etc - and what I describe works fine for this. But you can't have the whole of your home on the NTFS drive symlinked to your /home on your root partition. There are hidden files and folders in /home with special permissions, as mcduck points out, which NTFS doesn't support. But your ordinary documents, MP3's and whatever will be fine.

Don't worry, you assumed correctly.

---

