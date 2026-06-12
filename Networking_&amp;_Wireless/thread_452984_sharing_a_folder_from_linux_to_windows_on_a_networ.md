---
title: "sharing a folder from linux to windows on a network"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by Hoaxe on 2007-05-23
k so who wants to give this one a try?

my mom and I are both behind the same router, so we both have internal ip addresses. Is there a way i can share a folder that she can access from her windows laptop and copy folders from? 3rd party applications welcome of course.

this must be a pretty tough problem but i'd appreciate any help or guiding.

---

### Post by tgm4883 on 2007-05-23
actually it's pretty easy

Install samba and swat.  Samba is what you need to do this, SWAT is what you need to configure it easily

---

### Post by II_V_I on 2007-05-24
Hi Hoaxe,

I configured Samba, followed the advice of several other users on accessing my shared Ubuntu folders and volumes from a Windows machine, but I couldn't get it to work. The Windows machine (in my case a ThinkPad running Win2K) continues to ask for a username and password.

No problems whatsoever going the other way, though. From soon after the installation was complete, once I had access to the router and poked in the network access values I've had access to the shared folders on the Windows machine from the Ubuntu machine. Maybe the suggestions about changing security values [from {user} to {share}] only work for WinXP. I dunno.

Here's hoping some of the forum suggestions work for you.

---

### Post by Hoaxe on 2007-05-24
wow, linux is so awesome, we really do have it all eh? k i will try this tonight when i get back home after work.

---

### Post by rbringh on 2007-05-24
I had the exact same problem. If your not picky about security this is what I did. Advice from users....

You will have to edit the SMB.conf file. Youre in for some fun if you haven't done this...

Find this statement
security = user

change it to:
security = share

Open a terminal and restart samba.
sudo /etc/init.d/samba restart

The password question from Windows should go away. You may not be able to modify or create any new files. To correct that you need to allow access from the folders properties.

This got me going, 
Good Luck.............

---

### Post by II_V_I on 2007-05-25
Hi guys,

Well ... some progress to report; also still some problems.

First the good news: Elsewhere on this forum I found a fully edited and prepared version of what a working smb.conf file looked like in its entirety. That really helped me because my smb.conf (the one which would not work) had a couple things wrong down in the final section. (I had followed advice from another user, but what worked for him wouldn't work for me.) If you guys are still having trouble, I'll see if I can locate the thread where that working smb.conf was posted. 

So, what's the good news? Well, from my Win2K machine I can now access a shared folder on my Ubuntu machine, and vice versa: I have full FILE / FOLDER sharing--without the annoying and impenetrable "Username & Password" dialog on the Windows side. Haven't tried PRINTER sharing yet. (One step at a time, eh?)

What I still can't get working is VOLUME sharing. This is something Windows normally advises against--though it does permit it. So you can, say, share the entire DVD drive of your computer over a network. Although most people don't do this, it is helpful if you are trying to move information archived on one DVD disc directly to another DVD disc. Since most people don't have two optical drives, this is an easy (albeit S__L__O__W) way to do it, without first copying it all to a HDD, etc., etc. 

In my case, the HDD on which I installed my experimental Ubuntu Fiesty is small, so I'm relying on external storage on a FAT32 volume (external USB drive) as storage for the work I do on Ubuntu, because I want to be able to both access AND edit those files from my own WinXP OR from my wife's Win2K machine--no matter which OS I happen to be running. No matter which OS I'm running, I can now access her shared NTFS folders over the network; but, I can't read from an EXT3 partition directly, either from Win2K or from WinXP; and, althrough I can *read* NTFS volumes directly from Fiesty, I can't **write** to them. 

FAT32 volumes seem to be the only answer at the moment--just as they are on the Mac side--for keeping information available to everyone--either by directly attached USB drives or over a network.

In Feisty, the Administration | Shared Folders process (which installs from the distro ISO) permits users to select entire drives (or entire VOLUMES) as "shared folders". Fiesty seems happy with this. It permits me to browse, find, and select my external USB drive, it lets the operation to go through, and then lists my external USB FAT32 volume in its list of shared folders along with the ones on the local drive. What tells me that this *should* work, is that the icon for my external USB drive (attached to my Fiesty machine) shows up on the network from the Win2K machine's browser! BUT, when I try to open it, I get the same impenetrable "Username & Password" dialog as before. 

If either of you know how to solve this problem, or if hear anything that sounds helpful, post it up. BTW: no firewall on the Win2K machine; and, keep in mind that normal FILE / FOLDER sharing is now working fine.

---

### Post by II_V_I on 2007-05-25
Sorry, one small correction.

I wrongly reported that when I try to access the external USB drive from my Win2K machine over the network that I was getting the "Username & Password" dialog. I'm getting something different. It's a "tilted Switzerland" that simply says:

\\My_Fiesty_MachineName\My_USB_VolumeName is not accessible.
Network access is denied.

---

### Post by II_V_I on 2007-05-25
:D

Solution to volume sharing over the network found! I'm now a much happier camper.

For my situation, at least, the solution involved editing smb.conf, and FORCING new settings for the user and group settings for the external USB Drive (attached to my Ubuntu machine) which I wanted to share over the network. They were already forced to settings suggested by another user on the forum ... and those settings were obviously working for him ... but not for me.

The last section of my smb.conf file now looks like this:

-=-=-=-=-=-=-=-=-=-=-=-=-
[6GB-F]
comment = FAT32 Storage
path = /media/6GB-F
available = yes
browsable = yes
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = My_Ubuntu_UserName
force group = My_Ubuntu_UserName
-=-=-=-=-=-=-=-=-=-=-=-=-

Previously, when I couldn't access the volume over the Windows network, the last two lines looked like this:

-=-=-=-=-=-=-=-=-=-=-=-=-
force user = nobody
force group = nogroup
-=-=-=-=-=-=-=-=-=-=-=-=-

Although those two settings, when tacked to the end of the entries for the shared folders on my local Ubuntu drive, gained me access to those folders over the network through the Win2K machine, those settings did **not** work with the FAT32 volume I wanted to share.

I can't see why it would make a difference, BUT IT DEFINITELY DOES!!! (at least in my situation)

Hope this helps .... ;-)

---

### Post by trinaryouroboros on 2007-06-03
3 years I've been tripping about this Samba problem with a Buslink external USB drive!

...I love you man!!!

:guitar:

---

### Post by Kamakazie! on 2007-06-03
awesome the username stuff works a treat :)

I was having major problems getting it working no matter what i tried. spent ages fiddling with permissions and setting! So simple yet no where i found told me such a thing!

cheers

---

### Post by Roelski on 2007-06-04
same issue here when trying to share a folder over different users.  Will give it a try later tonight.

Thanks already!

Roelski

---

