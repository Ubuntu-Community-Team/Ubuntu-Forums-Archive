---
title: "Sharing folders"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by iitywygms on 2008-08-13
I cant share folders. On my desktop computer, (main) i right click a folder and select share folder.
I go to my laptop, browse the network, see windows network, then nothing shows up.
I can print to my main computer from my laptop. I can also view my main computer from the laptop using remote desktop.
I just cant see any shared folders.  Any ideas?

Both machines running hardy with latest updates.

I can get further if I use remote desktop from my laptop.  Once I connect using remote desktop, then I can go to network places and click on windows network, then workgroup, then my main computer.  All that shows up then is print$

thanks for the help

---

### Post by linux6994 on 2008-08-13
Best thing to try would be to load system-config-samba this will give you a samba gui that is easy to setup. Also go to the folder you wish to share, go to properties and select share, you will be prompted to install anything that is missing. smbfs is samba outbound, samba is inbound. 

Look into installing nautilus share also. I would attach screen shots but I am not on my ubuntu pc. 

Good Luck.

---

### Post by iitywygms on 2008-08-13
I installed that.  It showed the folders i wanted to share.  I am however still unable to see any folders from my laptop, or any other computer.
Anyone else have any suggestions?
Nautilus share is installed.

---

### Post by iitywygms on 2008-08-13
Bump

---

### Post by iitywygms on 2008-08-14
Anyone?????

---

### Post by Iowan on 2008-08-15
I thought I had bookmarked or subscribed to a thread that mentioned making one Ubuntu box a WINS server, editing /etc/nsswitch.conf, and one more detail (which I can't remember - nor can I find the bookmarked/subscribed thread).

---

### Post by iitywygms on 2008-08-18
> **Iowan said:**
> I thought I had bookmarked or subscribed to a thread that mentioned making one Ubuntu box a WINS server, editing /etc/nsswitch.conf, and one more detail (which I can't remember - nor can I find the bookmarked/subscribed thread).

Ummmm, How does this help me???  Am i missing something?

---

### Post by iitywygms on 2008-08-18
Okay, I just discovered something from another thread.
If I use a terminal and type nautilus smb://x.x.x.x where x is the other computers ip, i can see the other shared folders just fine.
So why is it when I click on places-network, I cant see the shared folders?

---

### Post by Iowan on 2008-08-19
> **iitywygms said:**
> Ummmm, How does this help me???  Am i missing something?Mostly, it bumped your thread.
Secondly, it let you know you weren't being ignored. (No offense to linux6994)
Finally, it suggested some topics you could search for until someone comes along with the "silver bullet" answer how to make shares visible by hostname rather than just IP address.

---

### Post by WebChat006 on 2008-08-19
I have exactly the same issue trying to share folders between windows XP and ubuntu 8.04. If I go to Places->Network and click on "Windows Network", I see that it's at location "smb:///" but the window is emtpy (0 Items).

Yet if I manually enter "smb://192.168.1.100/" (ip of windows computer) in the location bar, all the shared folders from my XP machine show up and I can access them perfectly.

I'm amazed that Ubuntu can't get file sharing to work in a sensible way with an operating system as old as XP.

---

### Post by iitywygms on 2008-08-19
> **Iowan said:**
> I thought I had bookmarked or subscribed to a thread that mentioned making one Ubuntu box a WINS server, editing /etc/nsswitch.conf, and one more detail (which I can't remember - nor can I find the bookmarked/subscribed thread).

I was not trying to be a jerk.  Sorry if I came across like that, I was just confused.  Thank you for the bump.

---

### Post by johnny9794 on 2008-08-19
> **iitywygms said:**
> Okay, I just discovered something from another thread.
If I use a terminal and type nautilus smb://x.x.x.x where x is the other computers ip, i can see the other shared folders just fine.
So why is it when I click on places-network, I cant see the shared folders?

Same thing for me, Im running 2 ubuntu machines 8.04.1 on each

> **WebChat006 said:**
> I have exactly the same issue trying to share folders between windows XP and ubuntu 8.04. If I go to Places->Network and click on "Windows Network", I see that it's at location "smb:///" but the window is emtpy (0 Items).

Yet if I manually enter "smb://192.168.1.100/" (ip of windows computer) in the location bar, all the shared folders from my XP machine show up and I can access them perfectly.

Same Exactly but between both my ubuntu machines.

---

### Post by Iowan on 2008-08-21
I'm finding my trail (my "silver bullet"?)...
[This]("http://ubuntuforums.org/showthread.php?t=288534") is a good How-To on mounting shares. It references [this]("http://ubuntuforums.org/showthread.php?t=190542") thread on Firestarter and name resolution.

The condensed version (as I read it): Install **winbind** and **smbfs** on Ubuntu.  Edit the **/etc/nsswitch.conf ** to include **wins** on the tail end of the *hosts:* line.

---

### Post by iitywygms on 2008-08-21
Iowan.  Thank you very much.  I will give that a shot when I have more time.
I read some of the forum you suggested and was a bit surprised at how much effort was needed to make sharing folders work.
Just imagine if a new person wants to try ubuntu.  He installs ubuntu on two computers, wants to share a file.  So he right clicks on it and selects the option to share it.  Goes to the other computer and cannot see it in network places.  Why even have the option to share if it will not work?

I know ubuntu is free and other than this issue, it is very good for me.  I even have halflife2 installed with no issues!

One other odd thing with my setup.  Even if my other computer is not turned on, when I look it places-network, the other computer shows up and the print$ foler is still visible.  It seems like samba is not updating of something.
Again thank you for the help.

end rant.

---

### Post by bab1 on 2008-08-22
Maybe I can help.  The term sharing seems to be misunderstood.  There is NO peer to peer sharing with Samba. Samba is a client/server protocol.  

When installed on a Linux host (computer) [COLOR="DarkGreen"]**"smbd"**[/COLOR] (the [COLOR="DarkGreen"]Samba server[/COLOR]) waits (listens) for requests to display and "serve" files.  This is a one way proposition.  In other words: a Windows host (client) requests data and the Samba server (daemon) responds.  

If you are on a Linux host, [COLOR="Indigo"]**"smbfs"**[/COLOR] not Samba, requests data from a server in Windows.  Same road different direction.  The reason the [COLOR="Indigo"]"smb://hostname/share"[/COLOR] method (Linux -->>Windows) fails is due to DNS not properly set up.  

Admittedly the GUI setup is flawed in the latest versions of Ubuntu.  Careful manual setup of all of the systems ([COLOR="DarkOrange"]DNS, DHCP (or static IP), Samba and smbfs[/COLOR]) are needed for it all to work.

As far as a "silver bullet", sadly there is none.  Some of the answers are half right.  None are fully correct in my view.  A manual setup of [COLOR="DarkRed"]/etc/samba/smb.conf, smbuser passwords, IP addressing and DNS[/COLOR] is the only way.  

To the OP: first setup DNS.  You should be able to ping all hosts on the local network by name.  The Samba server should have a consistent (static in my view) IP address.  The windows hosts may have dynamic IP addresses but you might find that you can't map the share (bookmark it) as the properties could change.

Then you can move to setting up the rest.  I'll be here if you need me.

---

### Post by thornlord on 2008-08-22
I have been fighting with this myself for several days now.

I don't really have an answer for you but I do have a bunch of websites that I've been collecting to assist my troubleshooting.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba) <- Setting Up Samba - could be good to start from scratch

[http://www.samba.org/samba/docs/using_samba/ch06.html](http://www.samba.org/samba/docs/using_samba/ch06.html) <- O'Reilly's Using Samba ... this will help

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch12_:_Samba_Security_and_Troubleshooting](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch12_:_Samba_Security_and_Troubleshooting) <- Troubleshooting Samba - I've made a lot of progress with this one.

[http://www.oregontechsupport.com/samba/](http://www.oregontechsupport.com/samba/) <- Another Samba link.

I hope this helps.

T.

---

### Post by bab1 on 2008-08-22
I believe you will find [[COLOR="Magenta"]**Samba 3 by example**[/COLOR]]("http://www.samba.org/samba/docs/Samba3-ByExample.pdf") to be one the best howto's out there.

If you have installed Samba with the documentation and [COLOR="Magenta"][COLOR="DarkOrange"]SWAT[/COLOR][/COLOR] then you can point your browser to:[COLOR="Blue"]http://localhost:901[/COLOR] and logging as a user (not root), you will see all the Samba documentation.  This includes an earlier version of the PDF I mentioned at the top of this post.

---

### Post by trikster_x on 2008-08-22
I don't know if this will help or not, but I have the same setup and I am able to share media files between my laptop and desktop with a cat 6 ethernet cable.  When I first tried to set up a shared folder, synaptic prompted me to download usershare.  After that completed, I was able to see my laptop from my desktop, but couldn't get folders to be marked as shared, so I found this thread:  [http://ubuntuforums.org/showthread.php?t=825965&highlight=usershare](http://ubuntuforums.org/showthread.php?t=825965&highlight=usershare) .  When I got the laptop restarted and went to move files from the laptop to the desktop, I couldn't get the workgroup icon to appear at first, but found that it takes about 5-10 minutes before anything will show up past the windows network page.  This could be specific to my setup, but it's worth a try to uninstall the transfer programs you have installed and start over from the beginning.

---

### Post by Iowan on 2008-08-22
As an FYI... Samba is not the only way to share files between Ubuntu (or Linux in general) machines.  For  the reasons you mentioned, some folks recommend NFS or SSHFS.  All require some setup.  I could find/post links from [https://help.ubuntu.com]("https://help.ubuntu.com")

---

### Post by iitywygms on 2008-08-22
There are quite a few ways to share files with linux.  We use nfs at work and it works great.  I guess my main concern is that there is an option to share files by right clicking on a folder and selecting share file.  That would leave me to believe that the folder is now shared and viewable in the network.  That is not really true.  
What I have done is create a launcher and put nautilus smb://x.x.x.x as the command.  x=ip  Now I have a one click option to view my folders that I have shared.
I am happy with this solution and that is all that is important. <-- Lol. Just kidding
Thanks to everyone who has helped.

---

