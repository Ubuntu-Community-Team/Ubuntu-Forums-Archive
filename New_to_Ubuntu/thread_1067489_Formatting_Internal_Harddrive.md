---
title: "Formatting Internal Harddrive"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by darc26 on 2009-02-11
Hello,  I just wanted to preface this question by saying that I am aware that there are plenty of threads on this subject.  The reason that I am asking again is because they don't seem to be applying to me.

I have a 500GB internal drive that I would very much like to use.  I have tried mounting and formatting both manually and with GParted.  

I believe that I am very close.  I can see the drive under Computer, but when I try to put files in there I get errors.  One tutorial said to make a new folder in there which I did and then use the chown command to change ownership.  This does not work.  I am a real newbie and would love to get some help.

THanks for any help.

---

### Post by trikster_x on 2009-02-11
So to be clear, will the drive mount?  Could you post any error details that may come up when you try to transfer files?  If you can't mount, any error details there would be good as well.

---

### Post by darc26 on 2009-02-12
It looks like it is mounting.  If I do this command:

sudo mount /dev/sdb1 /media/sdb1

it looks like it goes through fine, and when I right click on the drive icon there is an option to unmount.  

If I try to move a file into a folder there I get this error:

Error opening file '/media/sdb1/Movies/[MY FILE]': Permission denied

where [MY FILE] is the file I am moving.  I am doing this by dragging it into the folder if it makes a difference. 

Also, I noticed that if I go into the Properties/Permissions section under the folder 'Movies' that I created on this drive.  It says that you are not the owner and do not have permission to change the settings.  

But I made this folder, why don't I have permission.  

Not sure if this is a symptom, but thought it might be helpful.  

Thanks for any help you can offer.  Can you also recommend any book that is really good for a newbie like me.  Thanks.

---

### Post by Metallion on 2009-02-12
What filesystem is the hard drive? If it is ntfs then try to mount it with the following command:

```
sudo mount -t ntfs -o uid=yourusername /dev/sdb1 /media/sdb1
```

And replace yourusername with the user name you are using. :)

Right now the problem is that only the root user has access to the drive. If you use sudo, you will be able to move files on it but of course you want to be able to do that as a normal user too right? If the drive is ntfs, this command will take care of that for you.

---

### Post by vanadium on 2009-02-12
You just have a permission issue. You need to adjust ownership. Launch nautilus with root permissions (to do that, issue the command "gksudo nautilus" and provide your login password when asked).

Some file systems do not support linux file permissions. there, you can only set the permissions of the moint point. The entire file system will then acquire the permissions of the mount point.

As Metallion indicated, you can adjust permissions for ntfs or fat drives also using options in the mounting commmand, or in /etc/fstab if you automatically mount at boot time.

---

### Post by darc26 on 2009-02-12
Thanks for the help so far.  I will try these when I get home tonight.  

As far as my file system is concerned.  I am using ext3, which I am not fully aware of the implications of using.  This is just what the tutorial used and so I followed suit.  I would like to eventually be able to share files between my Linux machine, a Mac, and a PC.  Will using this file system cause any future problems?   

Is nautilus a third party program, I don't think I have heard of it.  

Thanks again for the help.

---

### Post by Metallion on 2009-02-12
Hmmm I thought I had replied a second time to this thread but it isn't showing up. :/ Either I'm going mad or something strange happened. Ah well...

Nautilus is the default file manager in Ubuntu. The place where you click on files and folders much like windows' explorer.

Your problem is indeed related to permissions and running nautilus as root would solve it but it's a bit of a bad practice. Another thing you could try is this command:
```
sudo chmod 777 /media/sdb1
```

To share files between windows and ubuntu you will need to install a driver for it on your windows system. You can get that at [http://www.fs-driver.org/](http://www.fs-driver.org/) It will mount your ext3 partition as ext2 but that works just fine. I'm using it myself too. I have no experience with mac but you could try to google for a similar driver. Since it's open source, it probably exists :D

---

### Post by vanadium on 2009-02-13
> o share files between windows and ubuntu you will need to install a driver for it on your windows system. You can get that at [http://www.fs-driver.org/](http://www.fs-driver.org/) 

I understand that Metallion has different machines running Windows and Mac. In that case, the files need to be shared using some protocol before they can be accessed from other computers. Probably, samba is the only choice for compatibility with both mac and windows.

ext3 is the best choice you could have made in your scenario.

---

### Post by ugm6hr on 2009-02-13
Follow the advice here: [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

This will give you permission to write to it, and also ensure it is auto-mounted at boot.

---

