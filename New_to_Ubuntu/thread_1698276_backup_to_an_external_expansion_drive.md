---
title: "backup to an external expansion drive"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by erelsgl on 2011-03-02
Hi,

I am trying to backup my system to an external 500 GB expansion drive, and I have several problems and questions:

1. I try to "Create startup disk" on my expansion drive, but the operation just fails with no explanation.

2. I try to format my expansion drive, but the program asks me what file system I want - FAT, ext2, or ext4, and I have no idea what to choose? 

I currently have ext3 on my hard-drive (I got this information by opening the "format" dialog and clicking the "drive service program" button).

3. What is the best way to do incremental backup from my hard-drive to my expansion drive?

Thank you!
:KS

---

### Post by Blutkoete on 2011-03-02
Hello erelsgl!

You'll find a quite good backup documentation here: [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem).

It also presents some backup utilities to automate the process. The file system type to format the drive to might depend on the backup utility you choose. In general, *FAT16* is the old Microsoft format, *FAT32* the medium-aged file system type (most USB sticks are formatted this way) and *NTFS* is the newest Microsoft type. *ext*X is used by Linux distributions. I'm no expert on file systems, so I can't tell you more about that; Wikipedia might help here (or other users). Check out [http://en.wikipedia.org/wiki/File_system#Types_of_file_systems](http://en.wikipedia.org/wiki/File_system#Types_of_file_systems).

If you've found a backup utility that suits your needs and you run into problems getting it to work, feel free to ask.

Best regards,

Blutkoete

**EDIT:** PS: When reading the table with the backup utilities on the UbuntuHelp page, don't underestimate the "interface" column: *GUI* means you'll have a **g**raphical **u**ser **i**nterface (windows, mouse and clicking) while *CLI* means you'll have to use the terminal.

---

### Post by seawolf167 on 2011-03-02
NTFS cannot store many *nix attributes, so as long as your external hdd is formatted in something else (i.e. ext3, ext4), you can use commands like rsync & programs that use rsync (like sbackup).

You can manually backup the drive with an rsync command, read the manual for more info

```
man rsync
```

the command could be as simple as 

```
rsync -ruv --delete /source /destination
```

For a GUI approach that does incremental backups, you can use sbackup

```
sudo apt-get install sbackup
```

To clone your entire drive (for easy restoring), I suggest [Clonezilla]("http://www.clonezilla.org"). It is very easy to use, and can clone drives, partitions, etc.

---

### Post by Chrissd on 2011-03-02
Hi,

I personally use DD, referring to the guide below. Only downside is you have to reinstall GRUB2 if/when you need to restore, but that takes about 10 minutes in total using a LiveCD, following a guide available on the internet.

[http://ubuntuforums.org/showthread.php?t=581680](http://ubuntuforums.org/showthread.php?t=581680)

---

### Post by erelsgl on 2011-03-03
Thank you all for the pointers! I understand it is better to use a Linux file system, such as ext*, if I want to use LInux backup tools.

Do you have any idea, why I have only ext2 and ext4 to choose from, although my current file system is ext3?

---

### Post by seawolf167 on 2011-03-03
You should be any to format to any type with GParted which is installed by default (System -> Administration -> GParted)

Note: If you are going to format an NTFS drive for any reason, you should also get the following before you proceed

```
sudo apt-get install ntfsprogs
```

---

### Post by erelsgl on 2011-03-05
Thanks! I formatted the partition with ext3, then used unetbootin to create a boot disk (the default "make startup disk" didn't work), and it worked!

---

