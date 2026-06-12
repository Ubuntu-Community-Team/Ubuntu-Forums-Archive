---
title: "Question 1 : Simple guide to Sharing HD"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by zootoxin on 2010-01-02
Hi All, 

I am a very casual linux user so I am hoping for a seriously easy guide to sharing a External HD.

The ExHD was formatted on a windows PC where I ripped all my DVDs to Avi onto it.

I have transfered the ExHD to my Linux Mint machine. 

All my other files can share easily to and from my other linux (ubuntu) and Windows machines.

I want to share this ExHD with all other machines but I dont know where to start and all the tuts I have seen so far confuse me.

Can anyone walk me through the process?

Thanks

---

### Post by theozzlives on 2010-01-02
First create a folder in your /home/<username>/ folder, we'll say external
```
mkdir ~/external
```

Then edit your fstab
```
gksu gedit /etc/fstab
```

You want to mount your drive (say sdb1, for giggles). Put a line at the end of fstab something like
```
/dev/sdb1 /home/<username>/external ntfs relatime 0 1
```

close and save and run
```
sudo mount -a
```

it's just a matter of sharing the "external" folder after that.

---

### Post by zootoxin on 2010-01-04
> **theozzlives said:**
> First create a folder in your /home/<username>/ folder, we'll say external
```
mkdir ~/external
```Then edit your fstab
```
gksu gedit /etc/fstab
```You want to mount your drive (say sdb1, for giggles). Put a line at the end of fstab something like
```
/dev/sdb1 /home/<username>/external ntfs relatime 0 1
```close and save and run
```
sudo mount -a
```it's just a matter of sharing the "external" folder after that.
  Cool thanks I will try this tonight.

Also out of interest could I do the same process with a ExHD that is shared from my Windows machine?

---

### Post by zootoxin on 2010-01-04
Hi there I followed you guide but I can't connect to the folder from Windows or Linuxmint.

I get the following errors 

Win:
\\MINT-DESKTOP\lacie_mint is not accessible. You might not have permission to use this network resource.........

Network access is denied.

Mint:

Unable to mount location

Failed to mount Windows share.

Please could you help me sort out this problem.

Thanks

---

### Post by J V on 2010-01-04
you did share the folder right?

---

### Post by zootoxin on 2010-01-05
Yeah.

Right Click

Sharing options 

Tick
Tick
Tick

Add permissions automatically

---

### Post by zootoxin on 2010-01-06
Help?

---

### Post by Morbius1 on 2010-01-06
Please post the output of the following commands please:

Open **Terminal**
Type **cat /etc/fstab**
Type **net usershare info**
Type **testparm -s**

---

### Post by Morbius1 on 2010-01-06
The more I think about this the more I think there is an easier way.

Don't mount it in fstab, let the system mount it by itself. Then use nautilus to share /media/lacie_mint or whatever the exteranl USB device declares itself to be - just like you originally did with quest access enabled.

_*Here's the problem with doing that:*_

When you insert a usb device into your system it automatically mounts with you as the owner and read /write permissions for you and only you. The remote user is comming across literally as user = "nobody". "nobody" is not you so access is denied.

_*To remedy,*_

[COLOR=Blue]EDIT: Unmount and remove the external USB device first. Sorry about that. details....details[/COLOR]

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Add the following line to the [COLOR=Blue][global][/COLOR] section of smb.conf:
```
force user = your_ubuntu_user_name
```Save the file, exit gedit, and back in the terminal type: [B]sudo service samba restart

[/B]If it works like I think it will, when the remote user tries to access that share, the name "nobody" will be replaced with the name "your_Ubuntu_user_name.[B]"

[/B]The advantage of this is that you do the "force user" once and then you can insert and share all sorts of usb storage devices without adding more lines to fstab.

Just a suggestion.

[COLOR=Blue]EDIT2:[/COLOR] In case you're wondering.... When you went to nautilus and shared the first time you probably clicked on the allow guest option. You'd think that "nobody" would qualify as a guest right? Nautilus-share ( the apps name ) was invented with linux filesystems in mind not windows fileystems. When you click on quests ( which you still have to do ), nautilus-share will also issue a command to change permissions on a linux filesystem. But linux can't change the permissions on a Windows filesystem. The command fails, but it doesn't tell you it fails. That's why the solution is to mount it in fstab with permissions set at mount time ( the only way you can set permisssions on a Windows filesystem ) or use my approach.

---

