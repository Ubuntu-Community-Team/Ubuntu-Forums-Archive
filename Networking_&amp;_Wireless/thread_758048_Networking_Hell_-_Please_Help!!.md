---
title: "Networking Hell - Please Help!!"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by AciD-X on 2008-04-17
Hello Guys,

_Devices related to conflict:_
> Desktop Installation:
  AMD Athlon X2 Dual Core 6000+ (Clocked @ 3.8ghz)
  Windows Vista Ultimate 32-bit
  Ethernet 100mbit connection to Linksys BEFSR41 Router.

>Laptop Installation:
  Intel Core 2 Duo 2.2ghz Custom-Build
  Ubuntu 'Gutsy Gibbon 7.10' 64-bit - with KDE Desktop
  Also currently hardwired to the Linksys BEFSR41 Router. (Also occasionally connect                                                      
  wirelessly to the Mimo XR Router when working at different locations in the house).

Firstly, let me explain how my setup is configured, the situation, my troubleshooting done so far and my conclusion.

So, I'm running a 32MBit Cable broadband connection, which is connected to a mimo XR 54G wireless router, for other machines in the house, not included in the issues experienced so far. From the Mimo router, connected by cat5 cable, is my personal router, a non-wireless linksys BEFSR41, this router is purely configured to forward to the Mimo, and on to the internet. 

Now that i have explained that, let me explain the problem. The internet, wirelessly or wired works absolutely fine on my Ubuntu Laptop, and Vista Desktop. However, sharing is rather interesting. After installing Samba, updating to the latest version, checking for any other updates and generally preparing my machine to be shared for the first time with the help of several step by step guides, i started to experience several peculiar issues.

When connected by ethernet to the Linksys router, both my Vista Desktop and Ubuntu Laptop can 'see' each others shares, and after being asked for a username and password, can access the files and folders, however i cannot copy or stream media from my Vista shares on my Ubuntu Laptop, the 'public' folder on my vista shares could be streamed from but would not allow copying even then. Despite several tutorials, and even an attempt at using the wireless connection to connect to the shares (which, being on a seperate subnet (192.168.0.xxx - Wireless, 129.168.1.xxx - Ethernet), clearly was never going to work, but desperation at that point, took over).

I'm still rather new to Ubuntu, and Linux in general for that matter, but after many years of being let down time after time with poorly written and unstable operating systems provided by Microsoft, I have started my first stage of migration with this laptop, and therefore despite over 100 hours of struggling, guides, Google and coffee, i ask for advice. 

Is there an easier way to prevent copying from stalling when copying from network shares? Also, and more so infact, is there _ANY_ other way to set up shares between Vista and Linux?

If anyone requires any more information, let me know and I'll do my best to provide you with what you need to help me set things up.

Note: Permissions in Vista have been set multiple different ways, including wide-open (allowing 'everyone' full-control of the share, and unsetting read-only attributes) only to result in further failures when attempting to stream or copy from these Vista shares. Vista, also, suffers when viewing Ubuntu, at one point, the Vista machine could browse freely without issues or errors, this for some reason no longer happens, while Ubuntu can, it appears, only 'read' the Vista shares, despite being un-set from read-only.

Any help, muchly appreciated.

Iain

---

### Post by lespaul_rentals on 2008-04-17
Try this:

[i]If Ultimate or Buisness version of Vista - 

- Run secpol.msc 
- Go to: Local Policies > Security Options 
- Find "Network Security: LAN Manager authentication level" 
- Change Setting from "Send NTLMv2 response only" to 
"Send LM & NTLM - use NTLMv2 session security if negotiated"[/i]

If that doesn't work, I have no idea.  Sharing is usually seamless between Samba and XP, since they both use exactly the same protocols with identical authentication types.  However, Vista has some new stuff which might cause problems.  Try the above solution, and let me know if it works.

EDIT: You also asked if there were other ways to share files.  Yes, there are.  The best way that I've found is through sshfs, which stands for SSH file system.  It allows you to remotely mount a drive through SSH.  It's definitely less convenient than Samba/SMB, though.

---

### Post by AciD-X on 2008-04-17
> **lespaul_rentals said:**
> Try this:

[i]If Ultimate or Buisness version of Vista - 

- Run secpol.msc 
- Go to: Local Policies > Security Options 
- Find "Network Security: LAN Manager authentication level" 
- Change Setting from "Send NTLMv2 response only" to 
"Send LM & NTLM - use NTLMv2 session security if negotiated"[/i]

If that doesn't work, I have no idea.  Sharing is usually seamless between Samba and XP, since they both use exactly the same protocols with identical authentication types.  However, Vista has some new stuff which might cause problems.  Try the above solution, and let me know if it works.

EDIT: You also asked if there were other ways to share files.  Yes, there are.  The best way that I've found is through sshfs, which stands for SSH file system.  It allows you to remotely mount a drive through SSH.  It's definitely less convenient than Samba/SMB, though.

Hi, Already done, and also tried with 'send NTLMv2 response only' selected. This is a right mess for me, i need to migrate 100+gb of data and with it getting to 16kb of 2gb for example, or 3mb even, stalls immediately, resulting in a an error saying the file doesn't exist, very inconvenient for me.

How would i go about setting up sshfs as i may very well try this if no one else has any ideas.

thanks

---

### Post by dmizer on 2008-04-17
how are you currently mounting the share?

eg:
through places > connect to server
if this is the case, see the second link in my signature.

or with fstab?
if this is so, please post the contents of your /etc/fstab file.

---

### Post by AciD-X on 2008-04-17
> **dmizer said:**
> how are you currently mounting the share?

eg:
through places > connect to server
if this is the case, see the second link in my signature.

or with fstab?

if this is so, please post the contents of your /etc/fstab file.

I had attempted to mount my share both ways, i removed the mount point from /etc/fstab after I got sick of it not working, its wierd, the connection is sucessful if i manually input the admin user + pass for the windows shares, but it still stalls on copying and wont stream. 

I could re-follow the guide and add them to fstab again? Below is my fstab at present:
[I]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6d06668b-5743-4f65-9052-f09812b6ecd2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=24e27084-4656-415a-9810-980369f01ae5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0[/I]

---

### Post by dmizer on 2008-04-17
if you had to enter a password when mounting with fstab, then you have a problem.

samba is constantly negotiating the connection, and will terminate when it becomes idle.  for this reason, you will need to include the username and password in the fstab line so that the authentication can be negotiated on demand instead of manually entered.

the cifs howto in my signature outlines how to create a somewhat secure password file that is not world readable.

---

### Post by AciD-X on 2008-04-17
> **dmizer said:**
> if you had to enter a password when mounting with fstab, then you have a problem.

samba is constantly negotiating the connection, and will terminate when it becomes idle.  for this reason, you will need to include the username and password in the fstab line so that the authentication can be negotiated on demand instead of manually entered.

the cifs howto in my signature outlines how to create a somewhat secure password file that is not world readable.

Ok,

I will follow that guide tomorrow evening after work, thank you so far. I will let you know of the outcome, perhaps a copy of my fstab after editing?

Thanks

iain.

---

