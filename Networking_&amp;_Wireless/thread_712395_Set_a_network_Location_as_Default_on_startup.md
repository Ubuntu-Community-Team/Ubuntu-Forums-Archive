---
title: "Set a network Location as Default on startup"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by VirusX2 on 2008-03-01
Hi, how can i set a saved Network Location as Default, so it loads on startup??:confused:

---

### Post by tact on 2008-03-01
> **VirusX2 said:**
> Hi, how can i set a saved Network Location as Default, so it loads on startup??:confused:

Not really sure what you are wanting from the above description.  When you save a network location its like a bookmark and will open next time you click it....

Let me describe what I have done on my system and you tell me if thats what you are looking for - if so then I can tell you how to do it:
The company I work for has a windows based LAN and there are a couple of network shares (folders/drives) that I like to have automatically available to me whenever I log into the company LAN.  

Using CIFS and a few lines in my /etc/fstab I have those shares mounted automatically, even drive icons show up automatically on my desktop.

Again - if thats what you are looking for then I can give more detail.

Cheers.

---

### Post by dmiller40 on 2008-03-02
I am trying to setup auto mount at startup as well. 

I have edited my /etc/fstab with...

```
//17.1.0.10/Divx /home/dmiller/Videos nfs defaults 0 0
```

the command i use in terminal is

```
sudo mount //17.1.0.10/Divx /home/dmiller/Videos
```

what do i need to enter in my fstab?
thanks
dm

---

### Post by VirusX2 on 2008-03-02
No men, i mean the Network Location as seen below in the attachment. Any ideas???:(:(

---

### Post by tact on 2008-03-02
Are you running v7.10 (Gutsy)?

If so then you have "networkmanager" installed by default.  Network manager automatically brings up wired or wifi network adapters depending what it detects available.  Not just at boot either - if can auto change-over from wired to wifi and back again as needed.

For networkmanager to be in control you have to NOT configure them as per that screenshot you posted.  When you enable the network adapters as shown by your screenshot you take control away from networkmanager.

To give control back to networkmanager - Please try setting autoroam on both the wired and wifi adapters (they will then all have "-" beside them instead of the tick mark).

You should see the network manager icon/indicator in the system notification area (up in the top right portion of the upper tray if you have a default setup).

If you don't see the networkmanager indicator in the notification area press ALT-F2 and type nm-applet and press enter.

Makes sense?

---

### Post by tact on 2008-03-02
> **dmiller40 said:**
> I am trying to setup auto mount at startup as well. 

I have edited my /etc/fstab with...

```
//17.1.0.10/Divx /home/dmiller/Videos nfs defaults 0 0
```

the command i use in terminal is

```
sudo mount //17.1.0.10/Divx /home/dmiller/Videos
```

what do i need to enter in my fstab?
thanks
dm

I am guessing there is a typo above and "nfs" should be "NTFS" - Correct?  

If so the following applies:
Have a look at this thread and follow the directions... 
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

Basically: 
- You have to install smbfs and winbind
- if the share requires a username/password to access it then create a file to put your username/password and secure it (you could put username and password in the fstab file but thats not so clever)
- edit /etc/fstab appropriately

For example:...(its all on one line!)
```
//17.1.0.10/Divx /home/dmiller/Videos  cifs  credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0 
```

(the above assumed a username/password is needed to access the share and you have that information in /root/.smbcredentials)

If you want the share to show up automatically on your desktop then you need to create a mountpoint in /media.    (eg. mkdir /media/Videos) and then mount the share there instead of /home/dmiller/Videos

---

### Post by florian.bw on 2008-03-12
I have the same problem, and it's quite annoying for me as I have to do this twice a day, normally.

I started a brainstorm request, please vote for it if you want to see a change of that.

[http://brainstorm.ubuntu.com/idea/4365/](http://brainstorm.ubuntu.com/idea/4365/)
[[IMG]http://brainstorm.ubuntu.com/idea/4365/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/4365/)

---

