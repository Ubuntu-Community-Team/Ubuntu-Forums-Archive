---
title: "Can't access windows shared folder from Ubuntu"
date: 2019-11-06
forum: Networking &amp; Wireless
---

### Post by py-ohayo on 2019-11-06
Hello,

I connected my Windows machine with the Ubuntu one over Ethernet cable.
Then setup IPv4 at both sides (i.e. Windows & Ubuntu) and check connection using ping. It was Ok.
Then I created shared folder in Windows.
Then I tried to connect windows using "Files"->"Other connections"->then in "Connect to server" I typed "smb://192.168.0.1 (i.e. IP address of Windows for wired connection)
In the opened window I typed User ID and password, then clicked on "Connect".
... and nothing happened.
What should I check/setup in both systems (i.e. Ubuntu & Windows).

Thanks

---

### Post by TheFu on 2019-11-06
Did you install the samba client utilities package, smbclient?

---

### Post by py-ohayo on 2019-11-06
I think yes.
On some resource I've found this instruction:
**sudo apt-get install samba samba-common python-glade2 system-config-samba**
... and executed it.

---

### Post by py-ohayo on 2019-11-06
And just before this:
**sudo apt install smbclient**

---

### Post by oldfred on 2019-11-06
Linux NTFS driver will not read NTFS that is damaged or is hibernated. And Windows default fast start up turns on hibernation flag on all NTFS partitions.
Check if partition is hibernated.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by py-ohayo on 2019-11-06
Thanks.
As suggested in the 1st link I unchecked under Shutdown settings _the box regarding fast startup_.
Didn't help.

---

### Post by TheFu on 2019-11-06
I think Oldfred was thinking the system was dual boot, not 2 different systems.  We both made multiple assumptions about the setup.
I assumed the Windows machine was normal, on the same subnet, able to ping the Ubuntu machine.
I assumed the Ubuntu machine only used EXT3/4 storage, on the same subnet, and able to ping the Windows machine.
Both have static IPs.

I didn't assume either was connected to the internet or even a router, but that would make things easier.

---

### Post by py-ohayo on 2019-11-06
> I think Oldfred was thinking the system was dual boot, not 2 different  systems.  We both made multiple assumptions about the setup.
Frankly speaking I didn't understand what you mean.
As I briefly mentioned in the original post, my setup is as follows:
[LIST]
[*]there are two machines: one running Windows 10, other running Ubuntu 18.04 
[*]two machines are connected by Ethernet cable 
[*]On both machines I assigned static IP address with only last number (in IP) that is different. Subnet mask on both is 255.255.255.0 
[*]I checked connection with ping _on both sides_. It works ! 
[*]I created shared folder on Windows (probably at this point the problem occurs as I don't know how to add credentials for Ubuntu machine) 
[*]Then I proceeded according to this manual: [https://websiteforstudents.com/connecting-to-windows-networks-shares-from-ubuntu-desktop/](https://websiteforstudents.com/connecting-to-windows-networks-shares-from-ubuntu-desktop/) 
[/LIST]
When I trying to connect to the folder using [COLOR=#ff0000][FONT=arial black]smb://{the_name_of_windows_machine}/{name_of_shared_folder}[/FONT][/COLOR] it hangs.

---

### Post by TheFu on 2019-11-06
My reply was trying to address the post from Oldfred.  NTFS doesn't matter when SAMBA/CIFS is being used. THAT was my point.

I don't know how trustworthy websiteforstudents is. There are many reputable sources of Ubuntu guides. In general, they have "Ubuntu" in the domainname.  Like help.ubuntu.com.

Might try NOT adding the share-folder-name.  Just try smb://{the_name_of_windows_machine}/
If any part of the name has spaces in it, change the name.

---

### Post by py-ohayo on 2019-11-06
Other detail: when I click on "Windows Network", it is empty. Does it mean that something wrong with connection despite ping works ?

[IMG]https://i.postimg.cc/HLbKFTFz/Screenshot-from-2019-11-06-18-05-49.png[/IMG]

---

### Post by TheFu on 2019-11-06
[https://askubuntu.com/questions/1050460/how-to-mount-smb-share-on-ubuntu-18-04](https://askubuntu.com/questions/1050460/how-to-mount-smb-share-on-ubuntu-18-04)
shows multiple other options.

There are some thread in these forums specific to win10.  MSFT changed some defaults, I think.  I've never seen or touched Win10.

---

### Post by py-ohayo on 2019-11-06
> Might try NOT adding the share-folder-name.  Just try smb://{the_name_of_windows_machine}/
If any part of the name has spaces in it, change the name.

Doesn't work at all. Error message:[B]
Filed to retrieve share list from server: Connection time out.[/B]

Another detail (when I use request wirh share-folder-name): once request is executed, the credentials I introduced jest before changed:
[LIST]
[*]the field where I enter _windows USERNAME_ changes to _ubuntu USERNAME_
[*]the field where I enter _windows password_ empties
[/LIST]

Is it normal ?

---

### Post by Morbius1 on 2019-11-06
You are getting that error message when connecting to the Win10 machine because it thinks you a speaking gibberish.

In order for the file manager to display a list of servers and their shares it drops down to the smb1 dialect to perform the task. And there it gets stuck.

Problem is WIn10 disables smb1 on the server side and from a SMB2 / SMB3 perspective SMB1 is just a bunch of random 0's and 1's and Windows can't make any sense of it. There's a bug report for this: [https://bugs.launchpad.net/gvfs/+bug/1828107](https://bugs.launchpad.net/gvfs/+bug/1828107)

See my answer here for possible remedies: [https://askubuntu.com/questions/1179576/ubuntu-18-04-problem-to-connect-to-windows-10-smb-share](https://askubuntu.com/questions/1179576/ubuntu-18-04-problem-to-connect-to-windows-10-smb-share)

In short: Either enable smb1 on the server side of WIn10 ( not recommended ) or do a cifs mount which by default can access a WIn10 machine using smb3.02.

---

