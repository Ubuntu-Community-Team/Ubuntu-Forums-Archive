---
title: "Help with file sharing command please"
date: 2005-11-12
forum: Networking &amp; Wireless
---

### Post by Matchless on 2005-11-12
Hi,
   I would appreciate it if someone can just have a look at the Howto below and help me with the last part, sharing a file from a windows PC on Ubuntu.

_Howto share a folder for your accounting programs between Windows and kubuntu_

If you have Windows as well as Ubuntu machines on your lan it may be necessary to have a shared public folder that can hold the database files of your accounting programs in them for use from all your PC's. Normally this would reside on your server PC, but in a small home environment, it may not be sure if the linux box or the Windows PC is actually your server. In some cases you would prefer to keep these files on the Ubuntu server in a public folder, but with Ubuntu being continually updated and upgraded, you may feel safer keeping them on the Windows machine, or you may want to keep on both, using the other as a backup.
I have Moneydance installed on both my Windows and Kubuntu machines and they share the same database file, held on Kubuntu. I also have Quickbooks installed in the same way. On Kubuntu QB is installed on Crossover Office 5.0.0 with a menu icon on the desktop and it opens seamlessly and fast as if installed in linux. Ensure that you have Samba and Smbfs installed via Synaptic.

_Using Ubuntu as the server_
Basically create a public folder in the /home folder, put the Moneydance and Quickbooks database files in there. Now share this new folder with Samba and map it on the Windows PC to a drive such as Z. No on both Ubuntu and Windows point the programs to the files and use from any PC. Obviously your lan setup should be working as correctly before doing this.
Steps for Ubuntu PC:
sudo mkdir  /home/winpublic
sudo chmod 777  /home/winpublic/
sudo kwrite  /etc/samba/smb.conf
    Find the line
       ;    security = user
    and change to
       security = share              (remove the ; as well!)
   
    Add the following lines to the end of the file:
comment = Public Folder
path = /home/winpublic
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

  Save the edited file
sudo testparm
sudo  /etc/init.d/samba restart

_Steps for Window PC:_
Go to My Network Places, check that you can see the shared Ubuntu folder. Go to Tools and Map Network Drive and map to Z for example and under My Computer you should see a Z drive now that is actually your Ubuntu folder

Now move your files you want to share into the folder /home/public and change the permissions to allow all to read and write. The above example requires no authentication and is maybe suitable for a home environment where security is not a big issue. This works well, serving from the linux box.

_Using windows as the server (my problem area)_
Here you basically need to set up a windows folder on the windows PC and share it fully as i.e. winpublic. Also make sure that your firewall allows the network neighbourhood traffic. There seems to be some problems with NTFS and it would be a good idea to partition your NTFS harddrive with a small FAT32 partition for the sharing part. Acronis Partition Expert does this very easily, there are many good partition programs out there, but be careful and backup before changing partitions, although very safe with Acronis. Now you can go to Network Folders  on your Ubuntu PC and ensure that you can see the shared folder. If so, you are nearly there. Now create a directory /mnt/winpublic on the ubuntu PC. This shared folder now needs to be mounted and then you should be able to point the QB and Moneydance to the files. Again check the permissions of the files and test from both sides
Method:
sudo mkdir  /mnt/winpublic
sudo kwrite  /etc/fstab

[COLOR="Red"]To mount automatically after each reboot add this line at the end of the file /etc/fstab:
//192/168.0.2/winpublic    /media/public   smbfs vfat    iocharset=utf8,umask=000        0          0


Manual mounting and has to be done after each reboot:
sudo smbmount  //192.168.0.2/winpublic   /media/winpublic vfat  -o  iocharset=utf8,umask=000[/COLOR]

The manual command works, but I do not have the correct permissions on the file and cannot change it and QB on Kubuntu says it cannot read the file..
The /ect/fstab entry does not work and must be wrong. I am not a experienced in command line commands and would appreciate anyone correcting this. Is there any way doing the above from the Desktop Gui?
Much appreciated.

---

