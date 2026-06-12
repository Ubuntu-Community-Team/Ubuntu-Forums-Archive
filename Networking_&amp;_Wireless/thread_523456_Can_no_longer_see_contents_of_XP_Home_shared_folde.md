---
title: "Can no longer see contents of XP Home shared folders"
date: 2007-08-11
forum: Networking &amp; Wireless
---

### Post by Rewil on 2007-08-11
I have a small home network consisting of an Ubuntu 6.06 machine and a machine running Windows XP Home, which at one time networked properly (I could share folders on each machine as expected). I could also run printer sharing (the printers are on the XP machine).

A month or so ago, I lost the ability to see the XP shared folder contents, and also lost printer sharing. I can still see the XP folders, but if I try to open them, I get "The folder contents could not be displayed". The XP machine can still see my Ubuntu shared folders, and move files back and forth.

I have been searching the web for information on this for several weeks, but can't find anything that seems to work. At this point, I don't know if it is an XP Home setup problem, or Samba that would be causing the problem. Any suggestions?

---

### Post by dstorrez on 2007-08-25
I'm having the same problem. It was working flawlessly and all of a sudden it quit. I can still print. I can still see all share folders on ubuntu and move files with the xp boxes but not from my ubuntu laptop to the rest of the network. I know its not an xp problem or smb.conf problem. I use my laptop at home and work so the problem follows in both networks. I hope someone could direct us in the right direction. I'll keep looking and if I find out I'll post it.

[www.myspace.com/dstorrez](www.myspace.com/dstorrez)

---

### Post by dstorrez on 2007-09-03
Well, I figured out that if you type in "smb://192.168.2.6" I can get access to the drives on that computer running XP.  So far I think it has to be with the way samba is handling the names. you might want to try entering the IP address and see if it works. I'm still looking for a fix.

---

### Post by Rewil on 2007-09-04
Are you entering that from the command line, or in a field somewhere?

If I do it from the command line, I get "no such file or directory". If I do it through "Connect to server" I get the same behaviour as before -- I can see the shared directory names, but not the contents.

I think I am going to have to monitor the network communications when I attempt to connect to the Windows machine and see if they might tell me anything useful. I have never done this before, so there will probably be a stiff learning curve while I figure out what I am looking for.

---

### Post by Peter09 on 2007-09-14
Anyone get a resolution to this as I have exactly the same problem, was working then stopped. I can see the shares but cannot see the contents. In Konquorer I can see the contents, play music files but cannot copy them to my desktop :confused:

Total confused over this ....

---

### Post by dstorrez on 2007-09-14
Ok, here is the deal. instead of doing a search on the network or typing in "smb://neptune" I type in the ip address of that computer. "smb://192.168.2.6" I type this in the Network File Browser. found under Places > Network. I type it on the address bar where it says location. Actually you can do it with just Nautilus. I've tried this in several networks. Its not a fix but a work around. I still searching for the real problem. My only clue is the way smb is handling names. good luck, and if you guys find it, let us know

---

### Post by ant2ne on 2007-09-14
Same boat. Course, I can't say it was working previously, because I just set it up. I think there must be a fudge in a recent samba update. the "smb://192.168.1.x" fix seems to solve it though.

---

### Post by Rewil on 2007-09-30
Found it!

Using Ethereal to monitor the ethernet communications when I tried to open the drive on the XP machine, I found that XP was responding with STATUS_INSUFF_SERVER_RESOURCES. After searching around on the web, I found a Microsoft article ( 177078 ) that indicated that the IRPStackSize parameter in the registry needed to be increased. I changed it from 15 to 18, rebooted, and now I can see the XP files properly.

---

### Post by dstorrez on 2007-10-19
Well,

I've loaded Gusty and all is well. They must have patched the problem.:popcorn:

---

### Post by ant2ne on 2007-10-19
> **Rewil said:**
> Found it!

Using Ethereal to monitor the ethernet communications when I tried to open the drive on the XP machine, I found that XP was responding with STATUS_INSUFF_SERVER_RESOURCES. After searching around on the web, I found a Microsoft article ( 177078 ) that indicated that the IRPStackSize parameter in the registry needed to be increased. I changed it from 15 to 18, rebooted, and now I can see the XP files properly.What registry entry? what value to put in? Can you linky to the documents?

---

### Post by Rewil on 2007-10-20
The direct link is: [http://support.microsoft.com/kb/177078](http://support.microsoft.com/kb/177078). If you go to microsoft.com and search on 177078 you will come up with the article as well as other related links.

In my case, I believe I created the registry entry (IRPStackSize) in an earlier attempt to resolve the problem. As per the microsoft article, I then increased the value until it worked. In my case, adding 3 seemed to be sufficient.

---

### Post by Surly on 2007-10-20
I had a similar problem, which is why I found this thread... but while fiddling with it during the search I have found a solution to my particular problem: Map the network devices in your defined hosts.

System -> Administration -> Network

1. Select the "Hosts" tab.
2. Click "Add"
3. Enter the LAN IP of the device
4. Enter the aliases (host-names)
5. Hit "Ok"

Worked for me, hope it helps.

---

### Post by Cato2 on 2007-10-28
I had a similar problem - in Breezy I could mount an XP Home shared folder OK via cifs (I found smbfs is buggy and no longer supported).

However, in a clean install of Feisty on a different disk, I got various errors.

I'm still not sure what exactly fixed this, but here's what I did:

1. Installed smbfs (aptitude install smbfs) which seems to pull in some useful tools, even though smbfs is deprecated - cifs is better.

2. Added wins to the /etc/nsswitch.conf (put it on the hosts line, after 'files' and before dns or mdns) - here's an extract of the file:

# Trying wins before DNS to get cifs mounts working
hosts:          files wins mdns4_minimal [NOTFOUND=return] dns mdns4

   * This is mostly if you are on a home network - as new PCs arrive on the network they announce themselves in the WINS name system, and other PCs can access them by hostname rather than IP address.   Particularly useful if you have dynamic IP addresses - see [http://www.linuxquestions.org/questions/linux-networking-3/home-network-with-no-server-374290/](http://www.linuxquestions.org/questions/linux-networking-3/home-network-with-no-server-374290/)


3. Installed winbind using aptitude install winbind - this works with nssswitch stuff, providing a server for WINS (it seems) and helps to make everything work. 

4. I already had smbclient installed, but if you don't have samba, install smbclient as well

5. Restarted samba and winbind in that order, based on rc3.d ordering:

   /etc/init.d/samba restart

   /etc/init.d/winbind restart

Another thing to try which worked for me on Xubuntu Gutsy - install pyneighborhood which pulls in various things that help.

Some useful diagnostic commands - here, the XP system is montblanc, specify your host here and ensure  its IP address in in /etc/hosts or DNS (or just use its IP address, preferably static) - do these as root, e.g. in a 'sudo bash' subshell:

# Check we can see the system through SMB
net lookup montblanc
net status -S montblanc shares
smbtree
mkdir /media/test

# try mounting the share - use username on XP box
smbmount //montblanc/data /media/test -o username=richard
# ... and with another tool, with debug output
smbclient -v -d2 -U richard //montblanc/data

This command above worked, so then I put the SMB credentials in /root/.smbcredentials, which contains:

username=richard
password=something

Be sure to do this to secure this file:

   chmod go-rwx /root/.smbcredentials

This needs to match the userid/password on your XP box of course.  After this, I could do this to successully access the share from Linux (but via a user-level tool, smbclient, not via the Linux kernel mounting the share):

   smbclient -v -d2 -A /root/.smbcredentials //montblanc/data

Then I created the final mountpoint:

  mkdir -p /net/montblanc/data

And then I appended this line to /etc/fstab:

   //montblanc/data   /net/montblanc/data   cifs   user,file_mode=0644,dir_mode=0755,credentials=/root/.smbcredentials       0       0

Finally, umount /test and mount /net/montblanc/data mounted the new filesystem - use 'df -Th' to check.

If there are any gurus who can say exactly why this worked, I'd be interested to hear from them here.

See [http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473) for a useful HOWTO on this topic.

---

