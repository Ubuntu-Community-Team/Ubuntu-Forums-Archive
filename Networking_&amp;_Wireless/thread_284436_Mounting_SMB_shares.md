---
title: "Mounting SMB shares"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by EmyrB on 2006-10-25
Hi All,

Just a quickie, how to I go about mounting SMB shares so that programs like Amarok can see them? I need to do this in both Gnome and KDE.

Cheers

EmyrB

---

### Post by BitTorrentBuddha on 2006-10-25
Make sure smbfs is installed: ```
sudo aptitude install smbfs
```
Then, you need to make a mount point *(**smbshare** can be anything you want for a mountpoint name)*: ```
sudo mkdir /mnt/**smbshare**
```
Then to actually mount it, one would use smbmount *(replace **hostname** with the hostname or IP address of the windows computer, **sharename** with the name of the share on the windows computer, and **smbshare** with the name of the mountpoint from the command before)*: ```
smbmount //**hostname**/**sharename** /mnt/**smbshare**
```

---

### Post by EmyrB on 2006-10-26
Cheers BitTorrentBuddha, I shall do this tonight and hopefully I can get Amarok to play my music instead of crashing :)

---

### Post by EmyrB on 2006-10-29
Hey BitTorrentBuddha,

Is there anyway to script this so that it mounts automatically when my system starts?

Cheers

EmyrB

---

### Post by BitTorrentBuddha on 2006-10-29
To mount smb shares at boot requires editing the fstab. So open it up with root privileges. It's okay to paste the entire line in, the parts after the "#" won't be run. *(gedit assumes gnome, use the appropriate text editor for your desktop environment)*

[color=red]**Always backup important files before editing them**[/color]:```
sudo aptitude install smbfs # Get the appropriate tools for mounting samba shares
sudo cp /etc/fstab /etc/fstab.bak # This is making the backup
gksu gedit /etc/fstab # This should open the file
```
In that file add the following line *(Replace **HOSTNAME** with the windows hostname or IP address, **SHARE**, with the windows share name, and **MOUNTPOINT** with the directory you created. **SMBUSER** should be replaced with the samba username, and **SMBPASS** with the samba password.)*:```
//**HOSTNAME**/**SHARE** /mnt/**MOUNTPOINT** smbfs username=**SMBUSER**,password=**SMBPASS**,umask 022 0 0
```

If the worst happens and these directions bork your machine (though it is *highly* unlikely,) get to a command prompt and run this command *(write this down before restarting, but **do not run it before restarting**, that will ruin all progress.)*:```
sudo mv /etc/fstab.bak /etc/fstab
```It is now safe to try restarting. The share will be located at the mount point, there should also be a shortcut on the desktop if you're using gnome (I don't know about KDE.) I've tested this on Edgy, which uses a different init system than Dapper, so if you're running Dapper there might be a problem with init not loading samba soon enough, I'm not quite sure of the differences in upstart.

---

### Post by EmyrB on 2006-10-29
Hey BitTorrentBuddha,

That did the trick, I now have a shortcut on my desktop to a SMB share called Music and Amarok has not crashed once.

Thanks for all your help man, and it caused no issues with Edgy either :)

Cheers

EmyrB

---

### Post by EmyrB on 2006-11-07
Hi BitTorrentBuddha,

I have tried what you said here on another edgy PC and it won't mount the share. It says that only root can mount the //ipaddress/sharename /mnt/mountpoint.

I thought root ran fstab?

Any thoughts?

Cheers

EmyrB

---

### Post by BitTorrentBuddha on 2006-11-07
That is really strange, fstab should be mounting things during boot, when does it say fstab must be run as root? While you're booting or after you're already in?

---

### Post by EmyrB on 2006-11-10
Hi BitTorrentBuddha,

Right it gives that error when I type the following
```

smbmount //hostname/sharename /mnt/smbshare
```

Not sure if this makes a difference, but the share is on a windows 2003 server, where as my one at home was on a WindowsXP pc.

Cheers

EmyrB

---

### Post by tomeaprik on 2006-11-10
if you aren't running that in fstab, then I believe you have to use sudo before mount command

---

### Post by EmyrB on 2006-11-10
Sorry, I forgot to say I was using sudo before that command. I think I have solved the problem by substituting the smbfs command in fstab with cifs. Will let you know how I get on :)

---

### Post by noodles12 on 2006-11-14
i entered in 

//tmn12/"My Music" /mnt/smbshare smbfs umask 022 0 0 

and it doesn't mount it at start up. 

however, 

sudo smbmount //tmn12/"My Music" /mnt/smbshare 

does work. 

Any suggestions? 

I'm running edgy with xgl/beryl on a laptop with an x1600.

---

### Post by BitTorrentBuddha on 2006-11-14
I'm terribly sorry, noodles12. The information you followed the first time was inaccurate, to correctly mount the share you ***must*** use the username=,password= part. Simply fill these in with your samba username and password, I believe that it defaults to your login name and password but you can change your password with the **smbpasswd** command.

---

### Post by noodles12 on 2006-11-15
I added in the username and password and it still doesn't auto-mount. Am i doing something wrong? 

//tmn12/"My Music" /mnt/smbshare smbfs username=USERNAME, password=PW,umask
 022 0 0




and of course USERNAME is my username and PW is the pw i set. I put this at the bottom of my /etc/fstab file.

---

### Post by EmyrB on 2006-11-16
OK noodles12 a couple of questions.

1. Is "My Music" shared correctly on the windows box?
2. Does issuing a "smbmount //hostname/sharename /mnt/sharename" mount the share?
3. "My Music" I assume is in "My Documents", try creating another folder in the root of the c drive and share that and issue the command in question 2.

Let me know how you get on.

---

### Post by dmizer on 2006-11-16
@noodles12
i've seen this problem alot in edgy.

add an entry to /etc/rc.local (before the line that says "exit 0") that reads like this:
```
mount /mnt/smbshare
```

---

### Post by Nem1976 on 2007-06-26
I followed the steps listed and if I try and use this command 

smbmount //GHOSTWALKER/C_drive /mnt/ghostwalkerc$

I get an error of this.

27753: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

I havel also tried this option
//HOSTNAME/SHARE /mnt/MOUNTPOINT smbfs username=SMBUSER,password=SMBPASS,umask 022 0 0
and get the same message.

I can browse the network and connect to the share after entering in my domain username/password and I can access the shares and files.  

I did some looking in google and can't seem to resolve this. 

Any suggestions?

thanks
Nem

---

### Post by diggity on 2007-07-06
the correct usage for smbmount is to use the -o paramater (this is for options).
Be sure to separate all options with a comma (,)

example:
sudo smbmount //HOSTNAME/SHARE /MOUNTPOINT -o username=USERNAME,password=PASSWORD

---

### Post by HarshReality on 2007-09-11
Still get errors when mounting in fstab...
This command is designed to be run from within /bin/mount by giving
the option '-t smbfs'. For example:
etc etc. 
# NASLite Automount
//192.168.1.250 /mnt/NAS smbfs username=NAS-User,password=NAS-User,umask=022 0 0

also tried changing my path to a folder in my home directory and the cifs rather than smbfs same thing... I need to be root :/

---

### Post by Zorael on 2007-09-11
fstab wants spaces expressed as \040.

So, replace "My Music" with "My\040Music".

---

### Post by HarshReality on 2007-09-11
I got mine resolved the only issue I found is that my network drives are 250G each and when the system starts and begins mounting it stalls the whole system... not when you go into the fact that there are actually 3 250G network drives.... well you get the idea.... so I simply settle for a DT shortcut.

---

### Post by chebotarev on 2007-11-13
I am new in Ubuntu and maybe that is stupid question: 
Why GUI smb browsing (which is working great for me) implemented in a way so I can not see it anywhere in file system? Why it is not implemented similar to other mounting (like other partiotions and so on). I know I can use smbfs manually but it would be so sad to lose this GUI functionality....

---

