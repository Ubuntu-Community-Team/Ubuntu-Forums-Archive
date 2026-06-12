---
title: "Why can't I write files to samba share unless sudo? 18.04.2"
date: 2019-04-08
forum: Networking &amp; Wireless
---

### Post by bob-swede on 2019-04-08
I have a media center running Kodi on a Raspberry Pi. I have attached a USB hard drive to it and set up a samba share named "mediadrive". For several years I have only used the share from Windows in order to write video files to the media center. It has always worked great to read and write files.

Now I have this headless Ubuntu _server_ 18.04.2 which is used as a subversion and openvpn server as well as a general web server. I access it using PuTTY from Windows.

When I download videos to it I want to copy these to the kodi media center like I have from Windows.
So I set up a connection to the kodi share via fstab as follows:
```
sudo mkdir /media/kodi
sudo chmod 755 /media/kodi
sudo nano /etc/fstab
Add following line:
//192.168.119.154/mediadrive/  /media/kodi cifs vers=2.1,username=osmc,password=*****  0  0
sudo mount -a
```

Now the share is available and I can read files just fine.
But no matter what I do I have to use sudo in order to write a file to the shared disk...
What can I do to fix this?

I *have* googled this but I never get to the same issue or at least not to a working solution....
Always talk about how to set up the samba share on Ubuntu, but I want to _use_ the share on a different Linux machine...

Note that I use the same user/password from Windows when attaching the share and there are no problems to write files then to the same share. So I assume there must be something the matter with the Ubuntu side concerning the way to set up the mount.

---

### Post by Morbius1 on 2019-04-08
> //192.168.119.154/mediadrive/  /media/kodi cifs vers=2.1,username=osmc,password=*****  0  0
By default mount.cifs will mount that with 755 permissions with owner = root. THe "usename" you passed in fstab is for access to the share not ownership of the mount point. You have an infinite number of options here:

Replace root with yourself by adding the uid=your-user-name so for example if your login username is also osmc the line would look like this:
> //192.168.119.154/mediadrive/  /media/kodi cifs vers=2.1,username=osmc,password=*****,[COLOR=#0000cd]**uid=osmc**[/COLOR]  0  0

You can also keep the owner = root but give permissions to everyone with the dir_mode and file_mode parameters:
> //192.168.119.154/mediadrive/  /media/kodi cifs vers=2.1,username=osmc,password=*****,[COLOR=#0000cd]**dir_mode=0777,file_mode=0777**[/COLOR]  0  0

Since the server is running Linux you may need another parameter added to each of these and that's [COLOR=#0000cd]**nounix**[/COLOR].

Also note that a mount of any kind even a cifs mount always replaces the permissions of the mount point with its own so chmod'ing a mount point before the mount does nothing to the permissions after the mount.

---

### Post by bob-swede on 2019-04-08
Thanks so much for your help!
I changed the line in fstab as follows:
```
//192.168.119.154/mediadrive/  /media/kodi cifs vers=2.1,username=osmc,password=******,dir_mode=0777,file_mode=0777,nounix  0  0
```
I also tried to use uid=osmc,nounix but that did not work, got an error message on mount:
```
 sudo mount -a
bad option uid="osmc"
```

In any case I can skip sudo now and can easily script copying of the files across to kodi!
:p

---

