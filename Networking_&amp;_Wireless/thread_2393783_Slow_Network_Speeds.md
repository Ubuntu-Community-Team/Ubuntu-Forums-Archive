---
title: "Slow Network Speeds"
date: 2018-06-07
forum: Networking &amp; Wireless
---

### Post by geeky-1 on 2018-06-07
I can only get up to 900 kBps file copies between my Ubuntu 16.04 LTS computer and either my Ubuntu 18.04 LTS server or a Windows 10 Dell laptop when I copy through the Files utility using Samba. However, when I copy from my Ubuntu computer to my laptop through Windows File Manager, I get up to 100 MBps.

I nearly returned my new router because I thought the gigabit ports weren't up to speed since 900 kBps is not even 10 Mbps and I can back up to my external drive via USB 2 ports in minutes, where it was taking days to backup to my server (over an hour just to copy 1 GB)!
So something is very wrong with Ubuntu's networking. I plugged both my Ubuntu computer and the Windows laptop directly into the router with Cat5e cables and disconnected my cable modem to eliminate any other interferences in my network.

---

### Post by Morbius1 on 2018-06-08
I'm telling you upfront that I'm not very good at this type of question since it's never been a problem for me. I'm not in the habit of sending 1GB+ files over the network ether so that may be why.

Ubuntu 16.04, 18.04, and Windows 10 in server mode will communicate using version 3 of the SMB dialect.

Ubuntu 16.04 in client mode will only communicate using version 1 of the SMB dialect.

[COLOR=#0000cd] What I find curious is that your 16.04 machine can access the WIn10 machine at all since Win10 disabled SMB1 - unless you found a way to not have Win10 update.[/COLOR]

Anyway, as a test edit /etc/samba/smb.conf on your 16.04 machine and right under the workgroup = WORKGROUP line add this one:
```
client max protocol = SMB3
```
Then restart smbd:
```
sudo service smbd restart
```

Now the 16.04 client will access both machines using the SMB3 dialect.

[COLOR=#0000cd]*Oh, btw you will lose the ability to "discover" the other hosts in Nautilus so you will have to access them by name explicitly. If you installed avahi-daemon on your 18.04 server you will be able to discover the box however.*[/COLOR]

Your speed will improve. It should double maybe triple the speed so don't expect a 10 fold increase.

---

### Post by geeky-1 on 2018-06-30
I changed to SMB3 and installed avahi-damon, but still get the same speeds, except lost the ability to access the Win10 laptop.
Now, I'm left hoping an upgrade to 18.04 will solve the issue, but an update won't be available for 16.04 LTS for another month...

---

### Post by SeijiSensei on 2018-06-30
For transfers between Linux machines use scp or rsync.  

On Windows, install a copy of WinSCP and use that to communicate with the Linux boxes.  Any better?

---

### Post by geeky-1 on 2018-06-30
Are there graphical versions of scp or rsync or tools that work through Nautilus? It's much more efficient to be able to navigate, drag and drop files and folders through a GUI than command line and also much less likely to make a typo mistake. That's my big complaint about Linux - until they no longer require command line to do common tasks like file management, it will never replace Windows.

---

### Post by The Cog on 2018-06-30
Nautilus can do SCP (or at least used to be able to, I haven't used nautlius for some years - I use thunar these days). In the address bar, enter something like "sftp://user@address/folder/". 
> That's my big complaint about Linux - until they no longer require command line to do common tasks like file management, it will never replace Windows.
Psst! Your ignorance is showing.

---

### Post by oldos2er on 2018-06-30
> **geeky-1 said:**
> Are there graphical versions of scp or rsync or tools that work through Nautilus?

There's grsync, but I can't say if it works with Nautilus or not

---

### Post by SeijiSensei on 2018-07-01
Both Nautilus and KDE Dolphin support sftp://server/share URLs in the address bar.  You need only be running openssh-server on the machine.

---

### Post by geeky-1 on 2018-07-04
SMB3 speeds are a little faster - I now get up to 1.3 Mbps instead of 900 Kbps, but it still took over 1/2 hour to copy a 750 MB folder over the network where I was able to do the same copy to an external USB (2) hard drive in under a minute.

I can't get sftp working. See my other thread:  [URL="https://ubuntuforums.org/showthread.php?t=2392384&p=13768842#post13768842"]https://ubuntuforums.org/showthread.php?t=2392384&p=13768842#post13768842

[/URL]

---

