---
title: "Permanant Samba mount"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by idanool on 2008-03-22
I'm trying to mount a windows share with the command:

sudo smbmount //sagie/d /media/sagie-d/ -o username=guest

I get the error:

"mount error: could not find target server. TCP name sagie/d not found
No ip address specified and hostname not found"

No password is needed for that share.
I can access the share through nautilus without any problems, but I want it to be permanent under /media.

---

### Post by fmartinez on 2008-03-22
> **idanool said:**
> I'm trying to mount a windows share with the command:

sudo smbmount //sagie/d /media/sagie-d/ -o username=guest

I get the error:

"mount error: could not find target server. TCP name sagie/d not found
No ip address specified and hostname not found"

No password is needed for that share.
I can access the share through nautilus without any problems, but I want it to be permanent under /media.

Is this Linux => Linux or Linux => Windows 
Linux => Linux: You should use NFS to mount the mount the partition
Linux => Windows: You should edit /etc/samba/smb.conf file and add the directories you want to share.... 
If none of the above
Edit your /etc/fstab file to include the devices you want to mount on start up

---

### Post by idanool on 2008-03-22
I asked for accessing a windows share from ubuntu.
editing /etc/fstab didn't work either, as mounting using smbmount didn't work...

---

### Post by jetsam on 2008-03-22
If the Windows computer has a static ip address, you can just use the ip address in your mount command, like so:
```
sudo smbmount //<ip_address_of_server>/d /media/sagie-d/ -o username=guest
```  

Alternately, you could put the ip address into your host file at /etc/hosts along with the name of the server to get name resolution to work properly.  

If the windows computer doesn't have a static ip address, you can install winbind on the ubuntu machine to do name resolution with netbios names.  

See here for a howto on mounting samba shares using winbind and cifs: 
[http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")

You'll likely want to use cifs for your mount at any rate.  Smbmount uses smbfs, and it is deprecated and  doesn't have very good unicode support.

---

### Post by jimbo99 on 2008-03-22
ABSOLUTELY NEVER EVER use the IP Address.  PERIOD!

---

### Post by jetsam on 2008-03-22
> ABSOLUTELY NEVER EVER use the IP Address. PERIOD!

Jimbo, can you explain why you say that?  There are some situations where people have no choice (if name resolution is borked), and it's useful at the very least for testing.  

I use host files on my network to avoid having winbind running as an extra process.  I think not making name resolution dependent on microsoft's problematic protocols can add a lot of stability to a small network.  Granted, it's more maintenance if you change the network, and it's unmanageable for large networks, but I don't think it's necessarily a bad practice...

---

### Post by idanool on 2008-03-22
using static IP seems to work. I'll try the name resolution later.
thanks.

---

### Post by elustran on 2008-04-08
> **jetsam said:**
> If the Windows computer has a static ip address, you can just use the ip You'll likely want to use cifs for your mount at any rate.  Smbmount uses smbfs, and it is deprecated and  doesn't have very good unicode support.

I'm not familiar with cifs - will it improve stability if the windows share goes down, i.e. the winpc gets shut down?  I've been having problems with slowdowns when users accidentally open a mounted windows share that's been taken offline - it's bad enough that I usually have to restart the computer, not just x-serve.

---

### Post by Eiríkr on 2008-04-08
Using the CIFS filesystem type is now *mandatory*.  The SMBFS filesystem type has been deprecated for some time, and finally seems to be broken as of Samba version 3.024 or 3.026, possibly even earlier.  From the smbmount man page:
> WARNING: smbmount is deprecated and not maintained any longer.  mount.cifs (mount -t cifs) should be used instead of smbmount.

Testing the SMBFS type, I've run into corrupted filesystem issues that required a reboot to fix -- unmounting the borked share wouldn't work.  Have a look at the following to familiarize yourself with the moutn options for this type.
```
man mount.cifs
```

My only gripe about the Samba folks' shift to CIFS is that they now use the option "user" to mean "username".  This causes problems when attempting to define a mount point that can be mounted by a user, as this same "user" option is supposed to be used by mount for this purpose, but mount.cifs overrides this behaviour.  < sigh. >  I hope a future version of the Samba package might use saner option names; there's really no need to shorten "username" to "user" except for sheer laziness, and plenty reason *not* to when it results in a name collision.  

Anyway, good luck with your setup!  :)

Cheers,

Eiríkr

---

### Post by jetsam on 2008-04-08
elustran: 
I just did a (very limited) test, and it seems better to me.  I get an indefinite hang when I try to access a mounted share that I took off line with smbfs, versus about a 10 second lag and an error message with cifs.  

There's even an option for it in cifs.  This is from the options section of the mount.cifs man page:   
> 
hard
    The program accessing a file on the cifs mounted file system will hang when the server crashes.

soft
    (default) The program accessing a file on the cifs mounted file system will not hang when the server crashes and will return errors to the user application.

They're mad with options-- why would you ever want "hard"?

---

### Post by elustran on 2008-04-08
Thanks guys.

I did run into a problem with cifs not being able to mount based on my computer's netbios name (I kept on getting TCP errors).  In case anybody else had this problem, somebody posted some instructions on how to fix that in this thread:
[http://ubuntuforums.org/showthread.php?t=88206&highlight=netbios]("http://ubuntuforums.org/showthread.php?t=88206&highlight=netbios")

---

### Post by Eiríkr on 2008-04-08
The problem is that XP's name resolution behaviour is itself buggy.  One workaround is to install the full **samba** package and configure your Ubuntu machine to be the authoritative Windows networking server, only not set up any shares (unless so needed), simply to have consistent behaviour.  I'd suggest the following simplified smb.conf file for such a setup.  This effectively establishes the Ubuntu Samba setup as a Windows NetBIOS name server, and prevents the oddball now-it-works-now-it-doesn't problems often seen when leaving name resolution to XP.  
```
[global]
# Name resolution options
   netbios name = ubuntu
   workgroup = mshome
   name resolve order = wins lmhosts bcast
   wins support = yes
# Master browser options
   local master = yes
   domain master = yes
   preferred master = yes
# Network security options
   hosts allow = 127. 192.168.1.
   interfaces = 127.0.0.1/8 192.168.1.0/24
# Logging options
   log file = /var/log/samba/samba.log
   max log size = 1000
# User security options
   security = user
   encrypt passwords = yes
   obey pam restrictions = yes
   passwd program = /usr/bin/passwd '%u'
   passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
```

The keys here are the name resolution and master browser options.  This simplified setup should make your Windows network browsing more stable.

HTH,

Eiríkr

---

