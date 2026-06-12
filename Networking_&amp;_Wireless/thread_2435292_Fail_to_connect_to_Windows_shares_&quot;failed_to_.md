---
title: "Fail to connect to Windows shares: &quot;failed to retrieve share list from server&quot;"
date: 2020-01-18
forum: Networking &amp; Wireless
---

### Post by stringtheory on 2020-01-18
I thought that problems connecting with Windows shares had been solved previously (much editing of config files, etc).  But Samba seems temperamental.

Error message is: "failed to retrieve share list from server: No route to host"

or "failed to retrieve share list from server: Connection timed out"

This depends on setting of 'name resolve order' in smb.conf
(Perhaps a clue?)

Is there a recommended procedure for debugging this?

---

### Post by TheFu on 2020-01-18
ooops. dbl post. Don't know how that happened.

---

### Post by TheFu on 2020-01-18
It isn't samba. It is your name resolution or a failed routing table.  If the machines are on the same subnet, try connecting using the IP address.  Does that work?  If so, then it is that the client doesn't know where to find the server on the network. There are many different ways to solve that. The best solution depends on how well managed your LAN is.  If it isn't well-managed, then some sort of zero-conf is probably easiest.

About 3 times a year, my only remaining Windows box will stop sharing to anyone.  The machine hasn't had any new programs installed in years - including patches.  But it will just stop sharing.

I didn't think smb.conf had anything to do with client access.  That is just for running a samba server, right?

First, perhaps if you would be extremely clear about which is the client machine and which is the server, then someone smarter than me could help?  Or are you truly using **smbclient** from Ubuntu to connect to a Windows share?

---

### Post by Morbius1 on 2020-01-19
What version of Windows are you running?

Accessing a Windows machine depends of which version of Windows is being accessed I'm afraid.

First: I would access the Windows machine by ip address just to make sure it can connect without using netbios names. In your file manager:
smb://192.168.0.100

If it is a legacy Windows system ( anything before Win10 ) and you want to access the server via discovery in your Linux file manager NetBIOS rules and yes the name resolution order does make a difference. If you haven't already done so install samba:
```
sudo apt install samba
```
And right under the [highlight]workgroup = WORKGROUP[/highlight] line add this one:
```
name resolve order = bcast host lmhosts wins
```
Then restart samba in this order:
```
sudo service smbd restart
sudo service nmbd restart
```
NetBIOS is a flaky thing and seems to be dependent on humidity levels, barometric presure, and sun spot activity. It's the reason Microsoft pretty much removed it in Win10.

Speaking of Win10, if you have kept your Win10 machine up to date every time a Linux machine attempts access through the file manager it will always result in [highlight]Failed to retrieve share list from server: Connection timed out[/highlight]. Win10 disables the smb1 dialect ( effectively disabling NetBIOS ) yet because of a bug induced by gnome the file manager can only access by smb1. Your best bet here is a CIFS mount.

For example to temporarily access my Win10 machine I can mount it with:
```
sudo mount -t cifs //win10.local/shared /mnt/Win10Shared -o username=smbuser,password=smbuserpw,uid=morbius
```
This will access the Win10 machine with smb3 instead of smb1. Also note that I'm using the mDNS host name ( win10.local ) not the NetBIOS name for the server.

---

### Post by farscape11 on 2020-04-22
Please help - I suddenly got into this problem but the listed here solutions didn't seem to work for me
It certainly looks like the Windows 10 system is a culprit, but I cannot figure out what happened.
I have 4 PC's in my network ( 2 Win10, 1 Win7, 1 Ubuntu 18.04) - and I was able to transfer files between all of them for 4 months no issues until last week Wednesday (Apr15,2020).
Suddenly, I cannot access shared folders on only one Win10 from Ubuntu - it gives the message 
**["Failed to retrieve share list from server:Connection timed out"]("https://ubuntuforums.org/showthread.php?t=2435292")**

What is puzzling - I can access other Win10 and Win7 from Ubuntu, I can access Ubuntu from all other (both 2 Win10 and Win7) workstations, as well as I can access the Win10 in question from other Win10 and Win7.
I neither change any settings nor installed new software - only can think of some system update, but why it affected only one specific directional combination?

Thank you very much in advance for any help and suggestions

---

### Post by Morbius1 on 2020-04-22
"Failed to retrieve share list from server: Connection timed out" 

You can get that error message from trying to access from your file manager any server that has disabled smb1. It's becasue of a bug in a sub-componenet of gvfs.

Access it this way in your file managers location bar:
```
smb://win10-host-name.local/share-name
```
You have to specify the windows host name and share name explicitly. You can't use smb://win10-host-name.local by itself to see the list of shares.

---

### Post by mommoon on 2020-04-23
if it doesn't work with the host name, try with the IP address

smb://IPAddress.local/share-name

---

### Post by Morbius1 on 2020-04-23
> smb://IPAddress.local/share-name 		
Get rid of the .local at the end.

w**in10-host-name.local** is the mDNS host name ( Windows host name with a .local attached to the end ) of the Windows box. IPAddress.local isn't really anything.

---

### Post by farscape11 on 2020-04-27
Thank you very much everyone
this way it connects nicely

---

### Post by farscape11 on 2020-04-28
Thanks a lot again for your help - as it solved my problem truly effectively
Yet, still a question (rather out of sheer curiosity) remains - why I am having this issue with one Win10 system, but other Win10 and Win7 I can reach and see the share lists, i.e. without explicitly adding [COLOR=#000000]*/share-name?*[/COLOR]

---

### Post by cdoublejj on 2020-09-10
i'm having this same problem with unraid and ubuntu server 20,04 LTS so that takes windows out of the loop as the problem. no host names, only static IP, so that takes networking out of the loop. i can only join *buntu 20.04 LTS to SMB if it's a public share. this is true weather it be unraid (linux) or windows server 2019. AND it work on buntu 18.04 LTS and NOT 20.04 LTS


EDIT: i added "smb:" without quotes and now i get "cifs URL not supported yet"

---

### Post by garibaldy on 2020-11-23
**SMB1.0/CIFS File Sharing Support must be enabled in "Windows Features" in Windows 10**
Open Control Panel. Click on Programs. Click on Turn Windows features on or off link. Expand the SMB 1.0/CIFS File Sharing Support option. Check the SMB 1.0/CIFS Client option. Click the OK button. Click the Restart now button.
Source: [https://ostoday.org/linux/how-to-access-linux-shared-folder-from-windows-10.html](https://ostoday.org/linux/how-to-access-linux-shared-folder-from-windows-10.html)

---

### Post by Prakash_Vishwakarm on 2021-09-26
This helps!

---

### Post by coffeecat on 2021-09-26
Back to sleep, ancient and oft-necromanced thread.

---

