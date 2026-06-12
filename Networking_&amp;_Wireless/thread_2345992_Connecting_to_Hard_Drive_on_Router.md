---
title: "Connecting to Hard Drive on Router"
date: 2016-12-10
forum: Networking &amp; Wireless
---

### Post by John_David_Hock on 2016-12-10
Hello,
      I am hoping someone can help me.  I have two computers, a Windows 7 Professional and a Linux Ubuntu 16.04.  The Linux computer is set up as my webserver.  I also have an ASUS RT-AC66U router where I have two hard drives plugged into the USB Ports.  The two Hard Drives are set up to act as kind of a file server that holds all of my files as well as media files such as movies, pictures and music.

I have a folder setup on one of the harddrives connected to the router to act as a backup folder for all of my webfile folders on the Linux websever.  Currently, I manually copy the files from the folders in my webserver to the folder in the router harddrive on a daily basis. I would like to create a cronjob that would do this backup automatically.  

My approach was to create a mountpoint on the linux webserver to the folder in the router harddrive and then create a cronjob to automate the backup but I do not know how to create a mount point for a hardrive connected to the router.   

I have tried several variations of the following and keep receiving mount error(6) or mount error(13) 
david@jdh8865-3:~$ sudo mount //192.168.1.1/JDH8865-FILES /home/david/webfiles/backup
Password for root@//192.168.1.1/JDH8865-FILES:  **********
Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)



Any help would be greatly appreciated.



Thanks,



JDH

---

### Post by ajgreeny on 2016-12-10
My router has a help menu that allows me to do what you want easily. Perhaps this will help even though you are using another router.
> usb file sharing
The Bright Box 2 Wireless Router has a USB port which allows you to connect a USB memory stick or hard drive to the router and share files on your home network. Once connected, the drive will be listed in Network (or My Network Places) if you're using a PC, or Finder if using an Apple Mac. You can also view (or map a network drive) the device at //192.168.1.1.

For most users, we recommend using 'USB File Sharing' in the Basic menu, however if you want to set up specific user accounts with different read/write access to the storage device, this section is for you.

To setup individual USB file sharing accounts:

    Disable 'Auto-Share'.
    Ensure 'Samba function' is enabled and click SAVE SETTINGS.
    Ensure the Workgroup Name matches the Workgroup Name of your network (this is usually Workgroup).
    In the User Account section select 'Add User'.
    Enter a Username and Password, select the required file permissions, i.e. Read only, or Read & Write and click SAVE SETTINGS.
    In the USB device field, select to Share the device, then select the user you wish to share the device with and click SAVE SETTINGS.
    Note that you may need to edit the share name to remove any spaces if you get an error message.
    Next time you try to connect to the storage device, you'll be prompted to enter your new username and password.


---

