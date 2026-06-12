---
title: "Getting Airport Extreme Disk Sharing Work Under Ubuntu"
date: 2007-07-21
forum: Networking &amp; Wireless
---

### Post by eastern_strider on 2007-07-21
If you have multiple operating systems and can access your disks through Mac or Windows but not Ubuntu, here is what you need to do:

First install Samba if you don't have it:

```

sudo aptitude install smbfs

```


Using Airport Utility configure your base station (AU should run on Mac or Windows, since I think Ubuntu does not have this tool):

[INDENT]
Airport Utility --> Base Station --> Manual Setup --> Disks --> File Sharing
Check "Enable File Sharing"
Set a password method. I use "With Base Station Password"
Set guest access to "Read and Write"
You can leave "Enable Disks Over Ethernet WAN Port" unchecked (we don't need it for local access)
[/INDENT]

When you click Update your airport base station will restart. Once it restarts write down your base station's local IP address. We'll need it later.

In Ubuntu go to Places-->Network Servers

If you are lucky here you'll see the name of your Base Station. When you double click on it, you should see the partitions of your USB disk connected to the base station.

If things don't go as expected, that is if you are unlucky, you'll not see the base station's name; or when you double click the partitions will not appear. In this case you can go to Places-->Connect To Server and select Windows Share from the Service Type. Write your base station's IP address in the Server field and click Connect. You should now see your disk as a network location.

Assuming that you were able to see your disk, here is what you can do to automatically mount it whenever you restart your computer.

First create a mount point. Assume that we are doing it under a folder called /mnt (we'll need sudo access):

```

sudo mkdir /mnt/folder_name

```

Then enter the following in your /etc/fstab file. You again need to use sudo.

```

sudo vi /etc/fstab

```

You can use any other text editor, if you don't want to use vi. Add the following line to the end of the fstab file:

```

//base_station_local_ip/folder_name /mnt/folder_name smbfs password=base_station_password,uid=your_username,gid=your_group 0 0

```

If you don't want to reveal your password here (this would be dangerous since fstab can be read by anyone!), you can use a credentials file. For that create a file in your home folder and give read/write access only to yourself:

```

echo password=base_station_password >> .smbpasswd
chmod 600 .smbpasswd

```

The filename can be anything. It doesn't have to be .smbpasswd (but it is just convenient). Then you can add the following to your /etc/fstab file:

```

//base_station_local_ip/folder_name /mnt/folder_name smbfs credentials=/home/username/.smbpasswd,uid=your_username,gid=your_group 0 0

```

For example my fstab entry looks like this:

```

//10.0.1.1/BACKUP /mnt/BACKUP smbfs credentials=/home/akyuz/.smbpasswd,uid=akyuz,gid=46 0 0

```

Now when you restart your computer, your disk should be mounted in the location you specified. If you would like to have more than one mount points (maybe because your disk has multiple partitions) then you need to add a new entry to the fstab file for each partition and corresponding mount point.

I hope this would be helpful to someone. At least knowing that it is possible should give you the motivation to make it work for yourself too :)

---

