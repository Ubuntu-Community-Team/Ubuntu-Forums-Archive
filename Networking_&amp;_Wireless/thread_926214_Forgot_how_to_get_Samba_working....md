---
title: "Forgot how to get Samba working..."
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by Sturm on 2008-09-21
So, it's been a good year.5 since I've last had to set up Samba.  I know people have told me not to do so in the past, but I can't help but do a fresh, clean install of an OS every year or so.  A "flush 'n fill," I call it.

So now I've got Hardy (8.04) up and running again on my 'server' computer, with all the /media drives mounted upon bootup with labels and all...  Now, I just need to get those drives (partitions, really) shared across my windows network.  I made a point to copy the contents of my old /etc/samba/smb.conf file to Evernote before I wiped the drive, just so I could get it back the way it needs to be.

However, it seems I must be missing some things, as I am still unable to see the shared folders from my Windows Vista PC.  I *do* see the "Ubuntu" server, but I am unable to get inside it, being blocked by the message:

> Windows cannot access \\UBUNTU.  Check the spelling of the name, etc.

I'm willing to bet it has something to do with setting usernames and groups in Ubuntu, but I've forgotten how to do so.  Also, I cannot seem to set permissions for any of the mounted partitions--when I right-click and choose "Properties," then go to the "Permissions" tab, I am given the message:

> The permissions of "**x**" could not be determined.
(replace "**x**" with any of my mounted drives, such as "images", "video", etc.)

I *did* finally realize that, although I had re-pasted all the smb.conf info back into /etc/samba/smb.conf, I had not installed Samba yet on my fresh new Ubuntu system, so I went ahead and did that with:
```
sudo apt-get install samba
```

Also, when I attempt to do a restart via:
```
/etc/init.d/samba restart
```
I get a bunch of errors:

> sturm@media-server:~$ /etc/init.d/samba restart
open: Permission denied
 * Stopping Samba daemons                                                       start-stop-daemon: warning: failed to kill 5362: Operation not permitted
start-stop-daemon: warning: failed to kill 5365: No such process
rm: cannot remove `/var/run/samba/smbd.pid': Permission denied
open: Permission denied
                                                                         [ OK ]
open: Permission denied
 * Starting Samba daemons                                                       open: Permission denied
                                                                         [ OK ]
sturm@media-server:~$ 


Can anyone help me figure out what I'm missing?  Lastly, here's my smb.conf, as I'm sure it might help to diagnose my problem(s):

> 
[global]
    netbios name = Ubuntu
    server string = Ubuntu
    workgroup = SOLAMNIA
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    guest ok = yes
    guest account = smbguest
    browseable = yes

    passdb backend = tdbsam
    security = share
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes


[music]
    path = /media/music
    available = yes
   
    public = yes
   
    guest ok = yes

browsable = yes
writable = yes
[archives]
    path = /media/archives
    available = yes
   
    public = yes
   
    guest ok = yes

browsable = yes
writable = yes
[images]
    path = /media/images
    available = yes
   
    public = yes
   
    guest ok = yes

browsable = yes
writable = yes
[video]
    path = /media/video
    available = yes
   
    public = yes
   
    guest ok = yes

browsable = yes
writable = yes
[misc]
    path = /media/misc
    available = yes
   
    public = yes
   
    guest ok = yes
browsable = yes
writable = yes
[printers]
    comment = All Printers
    broweseable = yes
    path = /tmp
    printable = yes
    public = yes
    writable = no
    create mode = 0700
    printcap name = /etc/printcap
    print command = /usr/bin/lpr -P%p -r %s
    printing = cups


Thanks for taking the time to read this!

---

### Post by gregphil on 2008-09-21
I have not read throught all your config files, but you do need to setup the Samba passwords database by adding each Windows user:

smbpasswd -a USER
password
password

Next, ubuntu 8.04 introduced a new bug and broke file browsing of authenticated windows shares (but anonymous shares can still be browsed)  see: (ignore reference to ADS in title)

[Bug #207072 in gvfs (Ubuntu Hardy): “nautilus does not display samba shares for machines inside an ADS network.”]("https://bugs.launchpad.net/ubuntu/hardy/+source/gvfs/+bug/207072") 

[Bug 524485 - nautilus does not display samba shares for machines inside an ADS network. (gvfs)]("http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26")

---

### Post by lisati on 2008-09-21
It looks like you've already done a lot of the work to get things going. You might find this thread interesting: [http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")

---

### Post by Sturm on 2008-09-21
I don't remember ever using the "smbpasswd" command last year when I set up Samba, but my memory is rather faulty, after all...

So, I tried using:
```
sudo smbpasswd -L -a smbguest
sudo smbpasswd -L -e smbguest
sudo smbpasswd -L -a sturm
sudo smbpasswd -L -e sturm
sudo smbpasswd -L -a Sturm
sudo smbpasswd -L -e Sturm
```
*smbguest* is the one I referenced in my /etc/samba/smb.conf file, *sturm* is the username I use to log into the Ubuntu computer, and *Sturm* is the username of the account I use to log into the Windows Vista machine.

I used the passwords for the first two (smbguest and sturm), but I don't have a password for my Windows login (Sturm), so I left it blank.  I also set permissions for the folders from the command line:

```
sudo chmod 0777 /media/{music, images, video, archive, misc}
```

Then I restarted Samba:

```
sudo /etc/init.d/samba restart
```

Still no go--same error message in Windows.

---

### Post by Sturm on 2008-09-21
Great.  I just made a bad situation worse. :(

I thought changing ownership of everything would help:

```
sudo chown -R smbguest /media
```

All it seemed to do was cause Windows to not see Ubuntu anymore!  Sure, I couldn't see any shared folders last time, but at least I could see that Ubuntu was being shared--now it's gone completely!

---

### Post by dmizer on 2008-09-22
No, you're local directory needs to be owned by the samba group, not the remote computer. The smb.conf handles the permissions between systems so you don't have to hand configure everything locally. That would be a nightmare.

Your best bet is to closely follow the link that lisati posted in post [#3](http://ubuntuforums.org/showpost.php?p=5832012&postcount=3).

---

### Post by Sturm on 2008-09-23
FIXED!

I was about to scrap the whole thing and reinstall again from scratch, having gone through the instructional guide lisati posted a link to ([http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)) step-by-step without success.  Then I noticed an almost-buried link at the bottom of that guide:  [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch12_:_Samba_Security_and_Troubleshooting](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch12_:_Samba_Security_and_Troubleshooting)

I figured I might as well give it a shot; the worst that could happen is that I lose a little bit of time in case this troubleshooting guide doesn't work.  Amazingly, it did.  And it might even have all been due to one small error in my smb.conf:  I had no [tmp] section in it.

I'm still not certain if such a section is really necessary, but it really does seem as though things started to fall into place after I fixed that issue.  (It was during step #5 in that troubleshooting guide.)

So, whether that was the fix or something else was, *Hallelujah!*  Now things are working beautifully, including iTunes, which I've always had to fiddle with in the past!  *Yay!!* :D

Thanks for all of your help, dmizer, lisati, and gregphil!  I have a habit of coming back to these posts soon afterward with a new problem or the same one coming back, but let's hope that I won't have to do so this time!  Hehehe...

---

