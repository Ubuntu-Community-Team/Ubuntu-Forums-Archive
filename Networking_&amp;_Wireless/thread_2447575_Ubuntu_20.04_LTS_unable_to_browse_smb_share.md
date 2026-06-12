---
title: "Ubuntu 20.04 LTS unable to browse smb share?"
date: 2020-07-21
forum: Networking &amp; Wireless
---

### Post by adrian-h on 2020-07-21
Hope in the correct area Desktop install problem with network access to files.

I have just done a new install of Ubuntru 20.04 LTS on this machine, being slightly more powerful then my others, I have a couple of oldermachines one with Suse and one with Ubuntu 18.04.  On my network I have an old RaspPi running samba shares from a hard disk so basically a network share.

I have followed the help pages in trying to browse for the shares with no success. i.e.
Open the Files application from the Activities overview, and click Other Locations in the sidebar. The file manager will find any computers on your local area network that advertise their ability to serve files  

I can see another linux device one of the Pluto SDR's and an icon for Wndows network, clicking on this says it is empty.

I know the location from Ubuntu 18.04 as smb://192.168.1.104/adrian as a valid share, if I try to enter this into the server location.

I get an error of **Unable to access location failed to retrieve the share list from server:** Software caused connection abort.

I do not appear to have installed samba on Ubuntu 18.04 as if I type samba at the command prompt or smb etc it suggests i install it.

UFW is not running so I believe a firewall issue is not the cause, but I am lost and hope someone can point me in the correct direction to get access to the NFS.

Cheers

Adrian

---

### Post by adrian-h on 2020-07-21
I have got a stage further down the line after more searching with google, I have installed nfs-common with sudo apt install nfs-common

Now I can see the windows shares and browse to my own shared drive on the raspPi but clicking on the share gives an error of [B]Unable to access location Failed to mount Windows share:Software caused connection abort.
[/B]
So I am guessing I have to find a way of adding username and password?[B]

Adrian


[/B]

---

### Post by adrian-h on 2020-07-21
OK so after a reboot I am back to square one the Windows network is again empty.  I will see if anyone can assist before I go futher, I will de-install the nfs-common.

Adrian

---

### Post by TheFu on 2020-07-21
CIFS/Samba and NFS are completely different from each other. They don't impact each other.  Best to pick one to be used and get that working, ignoring the other, then removing/disabling it after you are happy.

NFS is great for Unix-like OSes.  Usually, a r-pi would be the NFS client.  Regardless, the NFS server must have a static IP and must be wired ethernet connected to avoid all sorts of problems.  If you want NFS, let me know and I can help.  Others can help with Samba.

---

### Post by adrian-h on 2020-07-21
I have instant notifications set, but nothing received, so sorry for not seeing your reply.

The raspberry PI does have a fixed IP address, 192.168.1.104, and is wired.  I think the distro is now quite old on it and passed updating but it does run samba to share the directories.  In ubuntu 18.04 I can access it using smb://192.168.1.104/adrian, the system has stored my login and password somewhere?  The thing is I can not remember having to install anything in particular on that machine, if I type samba at a control prompt it suggests I need to install it.

Using the same smb://192.168.1.104/adrian on this machine with 20.04 I get the errors as above and it can not detect any windows shares at all.  Perhaps I did install something on 18 but have just forgotten what I did.

Cheers

Adrian

---

### Post by Morbius1 on 2020-07-22
Ah, now your description makes sense.
> **Software caused connection abort.**
Ubuntu 20 will attempt to access the server with the SMBv2 dialect of samba. If the server only understands SMBv1 ( what samba calls NT1 ) the Ubuntu 20 machine appears to it as speaking gibberish so it disconnects from the client.

Edit /etc/samba/smb.conf on Ubuntu 20 and add the following line under the workgroup = WORKGROUP line:
```
client min protocol = NT1
```
If you want these antique machines to be able to access any Ubuntu 20 samba shares you will need to add this line right under the first:
```
server min protocol = NT1
```

There is another issue and that is the security mode associated with these older systems. You _[COLOR=#ff0000]*may *[/COLOR]_need to adjust for that as well.
```
client lanman auth = yes
ntlm auth = yes

```

You would think that a simple restart of the smbd service would suffice but alas you need to do a reboot.

Then do the **smb://192.168.1.104/adrian **thing again.

---

### Post by adrian-h on 2020-07-23
Thank you Morbious1  I have installed Samba and done as you suggested and it has worked.

I am still very confused over the fact that with My Ubuntu 18.04 install that I am on this moment I do not have Samba installed, there is no /etc/samba/smb.conf but it can access the file shares easily.  What has changed between the two, as far as memory is concerned they were both Normal desktop installs.

Also sorry for the delay but I seemed to have locked myself out of the forum and had to be given access again.

Adrian

---

### Post by Morbius1 on 2020-07-23
The Linux samba client is made possible through the file manager with an smb library ( libsmbclient ) that is present, running, has a predefined set of defaults, and can do all that without an smb.conf file on all versions of Ubuntu.

smb.conf comes from samba-common not from samba ( the server package ) directly so if you didn't want to have a samba server you could have just installed the **smbclient** package. Then you would have an smb.conf file to mess with.

The difference between Ubuntu18 and Ubuntu20 is the version of samba that is used. In Ubuntu20 samba disables SMB1 ( NT1 ).

Despite what the samba documentation states smb.conf is not THE samba config file. It's an override file used against the default settings that you have no access to directly. And that is exactly what you did here. You overrode the new settings for client and server smb protocols with the same one's used in Ubuntu18.

---

### Post by adrian-h on 2020-07-23
Looks like I have got my notifications back.

Thank you again for your answer and assistance, So I can remove samba and install smbclient but keeping the smb.conf as suggested.

I will give that a go and make notes of what I do in a journal.

Adrian

---

### Post by RobertoRecordo on 2020-08-12
Success!

I installed Ubuntu Studio 20.04 and lost my ability to open may samba shares.
When  I tried to open the samba share file I could see the top level folders,  files, but when I try to open Documents I see the error 
   ```
 thunar "failed to mount windows share" software caused connection abort
```

I discovered that samba was not installed, so I installed it.

And then did this one thing
> **Morbius1 said:**
> 
Ubuntu 20 will attempt to access the server with the SMBv2 dialect of samba. If the server only understands SMBv1 ( what samba calls NT1 ) the Ubuntu 20 machine appears to it as speaking gibberish so it disconnects from the client.

Edit /etc/samba/smb.conf on Ubuntu 20 and add the following line under the workgroup = WORKGROUP line:
```
client min protocol = NT1
```


I am now able to open my shared drives.
Thanks!

---

### Post by louisk100 on 2020-10-14
Thank you, it solved my smb file connect problem, after upgrade from Ububtu 18.04 to 20.04.

---

