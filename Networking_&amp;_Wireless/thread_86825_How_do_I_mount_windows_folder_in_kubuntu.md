---
title: "How do I mount windows folder in kubuntu?"
date: 2005-11-06
forum: Networking &amp; Wireless
---

### Post by Matchless on 2005-11-06
Hi,
   I need some guidance as how to mount a windows folder in ubuntu. I can see the folder in kubuntu when using network folders, it is shared in windows. I need to access the same datafile on my windows pc used for my accounting program from my kubuntu pc.
Samba and Smbfs are installed, I have shared the folder with Samba (simple sharing) as I do not want to use username and password in this case, if possible.
I have created a folder in /media and can share this folder with Samba, but need to mount it I think, to read it from Crossover Office. Can anyone point me in the right direction here please.
Thanks

---

### Post by earobinson on 2005-11-06
Check this out: [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

---

### Post by Matchless on 2005-11-06
[QUOTE=earobinson]Check this out: [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)[/QUOTE]
 Thanks,
             Looked at many other writings and missed the most obvious one! Will give it a shot tomorrow.

---

### Post by earobinson on 2005-11-07
np good luck.

---

### Post by Maverick911 on 2005-11-07
1. Login as root by running from a terminal su followed by typing the root password.

2. Create a directory in your /mnt folder. This can be done by running mkdir /mnt/X where X is the name of the directory where the NTFS partition will be mounted.

3. Run fdisk -l and note the name of the device file for the NTFS partition. Lets say the device file name is found to be /dev/Y.

4. Open the file /etc/fstab in your favorite text editor.

5. On a new line at the bottom of the file, add the line
/dev/Y /mnt/X ntfs users,owner,ro,umask=000 0 0

where X is the name of the directory you created in step 2.

6. Save and quit the file /etc/fstab

7. Then run mount -a and the NTFS partition will be mounted. It will also be mounted automatically after reboot so that you do not have to do anything after you reboot.

---

### Post by Matchless on 2005-11-11
[QUOTE=Maverick911]1. Login as root by running from a terminal su followed by typing the root password.

2. Create a directory in your /mnt folder. This can be done by running mkdir /mnt/X where X is the name of the directory where the NTFS partition will be mounted.

3. Run fdisk -l and note the name of the device file for the NTFS partition. Lets say the device file name is found to be /dev/Y.

4. Open the file /etc/fstab in your favorite text editor.

5. On a new line at the bottom of the file, add the line
/dev/Y /mnt/X ntfs users,owner,ro,umask=000 0 0

where X is the name of the directory you created in step 2.

6. Save and quit the file /etc/fstab

7. Then run mount -a and the NTFS partition will be mounted. It will also be mounted automatically after reboot so that you do not have to do anything after you reboot.[/QUOTE]

Thanks,
          I still have a problem. I think maybe I did not clarify my situation properly. This folder is on a seperate Windows PC and I would like to mount it on my Kubuntu PC. I can actually share a folder on awindows machine with my Kubuntu maching and the other way areound, but still have some problems with mounting automatically on boot up and then i cannot set the proper permissions to allow me to read and write to the windows share. 
I have added my Howto below and will appreciate it if anyone could help me correct it as it works partially now:

_Howto share a folder for your accounting programs between Windows and kubuntu_

If you have Windows as well as Ubuntu machines on your lan it may be necessary to have a shared public folder that can have the database files of your accounting programs in them for use from all your PC's. Normally this would reside on your server PC, but in a small home environment, it may not be sure if the linux box or the Windows PC is actually your server. In some cases you would prefer to keep these files on the Ubuntu server in a public folder, but with Ubuntu being continually updated and upgraded, you may feel safer keeping them on the Windows machine, or you may want to keep on both, using the other as a backup.
I have Moneydance installed on both my Windows and Kubuntu machines and they share the same database file. I also have Quickbooks installed in the same way. On Kubuntu QB is installed on Crossover Office 5.0.0 with a menu icon on the desktop and it opens seamlessly and fast as if installed in linux, again I share the folder that contains the QB file with the Windows PC. Ensure that you have Samba and Smbfs installed via Synaptic.

_Using Ubuntu as the server_
Basically create a public folder in the /home folder, put the Moneydance and Quickbooks database files in there, in Windwows map the shared folder to a drive and point the programs to the files and use from any PC, regardless if Ubuntu or Windows. Obviously your lan setup should be working as well. 
Method:
sudo mkdir  /home/public
sudo chmod 777  /home/public/
sudo kwrite  /etc/samba/smb.conf
    Find the line
       ;    security = user
    and change to
       security = share              (remove the ; as well!)
   
    Add the following lines to the end of the file:
comment = Public Folder
path = /home/public
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

  Save the edited file
sudo testparm
sudo  /etc/init.d/samba restart


Now move your files you want to share into the folder /home/public and change the permissions to allow all to read and write. The above example requires no authentication and is maybe suitable for a home environment where security is not a big issue. This works well, serving from the linux box.

_Using windows as the server_
Here you basically need to set up a Windows folder i.e public on the Windows PC and share it fully as i.e. winpublic. Also make sure that your firewall allows the network neighbourhood traffic. There seems to be some problems with NTFS and it would be a good idea to partition your NTFS harddrive with a small FAT32 partition for the sharing part. Acronis Partition Expert does this very easily, there are many good partition programs out there, but be careful and backup before changing partitions, although very safe with Acronis. Now you can go to Network Folders  and ensure that you can see the shared folder in Kubuntu. If so you are nearly there. Now create a directory /mnt/winpublic. This shared folder now needs to be mounted and then you should be able to point the QB and Moneydance to the files. Again check the permissions of the files and test from both sides
Method:
sudo mkdir  /mnt/winpublic
sudo kwrite  /etc/fstab

To mount automatically after each reboot add this line at the end of the file /etc/fstab:
//192/168.0.2/winpublic    /media/public   smbfs vfat    iocharset=utf8,umask=000        0          0


Manual mounting and has to be done after each reboot:
sudo smbmount  //192.168.0.2/winpublic   /media/winpublic vfat  -o  iocharset=utf8,umask=000

The manual command works, but I do not have the correct permissions on the file and cannot change.
The /ect/fstab entry does not work and must be wrong. I am not a experienced in command line syntax and would appreciate anyone correcting this. Is there any way doing the above from the Desktop Gui?
Much thanks.
Matchless

---

