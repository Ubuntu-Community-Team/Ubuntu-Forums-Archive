---
title: "Short and Clear SMB mount label"
date: 2020-06-01
forum: Networking &amp; Wireless
---

### Post by deburg0 on 2020-06-01
When I click on "Connect to Server" to mount a smb shared drive, the folder is successively mounted, but the location name is complex and under the "/run" folder.

How can I choose the mount point and label?

I would like to be able to use  rsync from the terminal to regularly sync folders on my machine with the shared drive.

Thank you very much,
don

---

### Post by Morbius1 on 2020-06-01
You can't with the method you are using now.

What you could do is a CIFS mount then you will be able to specify the mount point.

An example of a temporary mount:

[1] Install cifs-utils in case it's 's not installed by default:
```
sudo apt install cifs-utils
```
[2] Create a mount point - best place given the introduction of snap is under /mnt:
```
sudo mkdir /mnt/Share
```
[3] Temporarily mount the share to that mount point:
```
sudo mount -t cifs //server/share /mnt/Share -o username=xxx,password=yyy,uid=your-linux-user-name
```

Once you get that working you can have it mount when you need it by specifying the mount in /etc/fstab if you want.

---

### Post by TheFu on 2020-06-01
If you mount using the fstab, then you have control over the options and location for the mount. Something like ... 

```
//172.22.22.14/D /media/D cifs x-systemd.automount,x-systemd.idle-timeout=600s,iocharset=utf8,uid=deburg0,gid=deburg0,file_mode=0664,dir_mode=0775,credentials=/etc/samba/win7lap-D.credentials 0 2
```

All on 1 line.  Put your CIFS mount credentials into the "credentials" file - be certain that file is owned by root and only readable by root for security reasons.

Obviously, you need to edit the line for your situation.
Use **sudoedit /etc/fstab** to edit the file.

A see  Morbius1 has answered.  that is an easier method which might be sufficient for your needs.  If so, it is probably working and you are happy.

My line above is a little more complex since it mounts the remote storage only when it is actually requested and will umount it 5 minutes after the last use.  This is good for laptops that aren't always on the correct subnet to access the storage.

After the change is made, we need to tell systemd to re-read the fstab
```
 sudo systemctl daemon-reload
```
and force the automounter to restart:
```
 sudo systemctl start media-D.automount
```
This is a by-product of system's mount system.  Restarting the computer could be done too. The "media-D" part of the name is controlled by systemd.

If you don't want the automount method, just remove the two x-????? parts of the line, then run **sudo mount -a**

---

### Post by deburg0 on 2020-06-02
Thank you very much for your replies.

 i am able to mount the shared folder using the "connect to server" feature which creates these labels:


smb-share:server=ukhcdata.mc.uky.edu
share=research/lab/Delisle-b


However, when I try to mount from the cli:


sudo mount -t cifs //ukhcdata.mc.uky.edu/research/lab/Delisle-b /mnt/share -o username=xxxx,password=xxxxx,dom=AD


I receive the error:


mount error(2): No such file or directory


Please advise

---

### Post by TheFu on 2020-06-02
AD changes everything.  That is always an important tidbit to share.  I wouldn't have answered at all if AD was mentioned. Haven't touched AD since 2007 when we switched to LDAP and Linux controlled authentication.

As for the ukhcdata.mc.uky.edu ... can you ping using that name from the client?

---

### Post by deburg0 on 2020-06-02
I am able to ping the server:

deburg0@LinuxWS:~$ ping ukhcdata.mc.uky.edu
PING mc.uky.edu (10.171.194.32) 56(84) bytes of data.
64 bytes from mc16azv2.mc.uky.edu (10.171.194.32): icmp_seq=1 ttl=120 time=68.6 ms
64 bytes from mc16azv2.mc.uky.edu (10.171.194.32): icmp_seq=2 ttl=120 time=67.5 ms
64 bytes from mc16azv2.mc.uky.edu (10.171.194.32): icmp_seq=3 ttl=120 time=68.4 ms
64 bytes from mc16azv2.mc.uky.edu (10.171.194.32): icmp_seq=4 ttl=120 time=67.7 ms
64 bytes from mc16azv2.mc.uky.edu (10.171.194.32): icmp_seq=5 ttl=120 time=68.6 ms
64 bytes from mc16azv2.mc.uky.edu (10.171.194.32): icmp_seq=6 ttl=120 time=67.9 ms

---

### Post by deburg0 on 2020-06-02
I am accessing the shared drive through a VPN connection through a Global Protect client

---

### Post by TheFu on 2020-06-02
> **deburg0 said:**
> I am accessing the shared drive through a VPN connection through a Global Protect client

No idea what "Global Protect client" is.  I've deployed enterprise VPNs for 20K concurrent users, but that was long ago, on Unix infrastructure, using SecurID tokens, from a network company that doesn't exist anymore.  There was a time when SMB didn't work well over VPNs because Windows broadcast "I'm here" broadcast was incompatible with large-scale VPNs.  Don't know if that is still the situation or not now that netbios isn't used. If the AD network has WINS servers, those probably negate the issue, but the client will need to be told about those WINS systems for point-n-click browsing to work. On openVPN, using a TAP connection was required for Netbios to work at all which was much less efficient than the normal TUN connection.

You'll need to lookup or have someone help who knows much more about AD.

I'm fairly certain the workstation would need to be joined to the AD domain for access to work. Also, if they use Kerberos for server-to-server authentications, the client machine will need that configured and approved by the IT AD infra team.  I don't think you can authenticate without their help.

---

### Post by deburg0 on 2020-06-02
I can mount and use the shared drive through the GUI. So mounting is doable. The problem for me is that the mount point is not "user friendly" -- which seems like a trivial problem. Why cannot I do what the GUI is doing but through the CLI where I have more control to define the mount point?

---

### Post by deburg0 on 2020-06-02
Output from verbose option for mount:

mount.cifs kernel mount options: ip=172.24.171.30,unc=\\ukhcdata.mc.uky.edu\research,user=deburg0,prefixpath=lab/Delisle-b,pass=********

I wonder if the "slashes" are not being properly handled so that the source folder is not found.

---

### Post by TheFu on 2020-06-02
Please understand that nobody here works for Canonical. We are just volunteers sharing what little knowledge we have. 

Use forward slashes on Unix.  They actually work on Windows too, BTW.  When I was a cross-platform C++ programmer, we always used forward slashes everywhere, on all platforms. It works, at least for non-GUI stuff.  If you need to use a \, then you'll want to use \\.  If you want \\ then you'll need \\\\.  Much easier to use / or //, yes?

I don't use any GUI much. Just not how I work. Different GUIs have different methods - so Gnome3 and KDE are probably using different code, but IDK. There's is something different about how the GUI does stuff. XFCE and LXQt probably do it different too.

Google offered up **udisksctl** which might work in a way that a GUI uses?  I don't know.  In older releases the GUI used something called GVFS.  [https://wiki.gnome.org/Projects/gvfs](https://wiki.gnome.org/Projects/gvfs) .  The last 2 yrs, the Gnome project claimed they'd worked on gvfs performance. Where it is used, if anywhere on 20.04, I haven't any clue.

---

### Post by Morbius1 on 2020-06-02
Try adding **nodfs** to your list of options:
> sudo mount -t cifs //ukhcdata.mc.uky.edu/research/lab/Delisle-b /mnt/share -o username=xxxx,password=xxxxx,dom=AD,**nodfs**

BTW, you forgot to take possession of the mounted share: uid=your-linux-user-name. Without it you are likely to have read only access.

[URL="https://unix.stackexchange.com/questions/164037/mount-cifs-error2-no-such-file-or-directory-when-using-a-prefixpath"]https://unix.stackexchange.com/questions/164037/mount-cifs-error2-no-such-file-or-directory-when-using-a-prefixpath


[/URL]

---

