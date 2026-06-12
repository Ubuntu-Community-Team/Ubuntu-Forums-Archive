---
title: "Sharing problems: Edgy client -&gt;XP server"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by gaalderman on 2007-03-17
Hi folks.  I'm learning Linux and I'd appreciate any guidance you can give me with this problem.  I've been diligently RTFM'ing, but I can't see what I'm doing wrong.

I just set up an Edgy Eft desktop at home.  The install went smoothly, it seems to like my hardware, and I got it talking and sharing a folder so that my Windows XP Pro box can read and write to a share on the Edgy Box.  Now, I want to do the same thing in reverse, Edgy reading/writing to a drive on the XP machine.

I used the sample smb.conf posted in this forum here:
[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

My only changes were to set netbios name = <MY UBUNTU HOST>, 
workgroup = <MY WORKGROUP NAME>, and to set
wins support = no
because I don't have WINS on my WLAN.

And, of course, I added the shares I want.  I set perms on the shared folder, then ran

sudo smbpasswd -L -a <user>
sudo smbpasswd -L -e <user>

for all the XP users I wanted to allow on the Ubuntu box (for ease of use, usernames are the same between the two systems)

Like I said, XP can see, read, and write to this share, and I have a drive mapped.  

But now I try to do it the other way.  I set up a Windows XP share.  On the Edgy box, I go to Places->Connect to Server...  I choose "Windows share" in the 'Service Type' box,  then type in the name of the XP server, the share name, and a user name.  The share now appears on my Edgy desktop.  I open it, and it asks me to authenticate.  It shows WORKGROUP in the domain.  I'm confused at that:  didn't I specify the workgroup name in the smb.conf?  Why isn't that showing up here?  My workgroup is not named 'Workgroup'.  I type my password, and I see an error message:  "The folder contents could not be displayed.  Sorry, couldn't display all the contents of <share name>".

I've tried several things: changed the Domain name in the authentication popup box to my workgroup name, changed it to the name of the XP server, left it blank.  Results are the same.  

I realize this is a noob question, but I'm still stumped, and I'm plowing through the Samba literature as best I can.  What am I doing wrong?

---

### Post by gaalderman on 2007-03-18
Here's the solution, for anybody who reads this thread who is looking for a solution, and for any Linux aficionados looking to get their gloat on (JK).  The problem was on the XP box, which is why the Samba documentation wasn't helping me.

Evidently Norton Antivirus dinks around with some registry settings used by the XP filesharing subsystem. The information in this Microsoft KB article has a quick and easy change to a registry setting that fixes the problem:

[http://support.microsoft.com/kb/177078](http://support.microsoft.com/kb/177078)

What tipped me off is another box on my network, a 2000 Pro machine in my kids' playroom, was giving me these error messages when I tried to hit the XP share:  "Not enough server storage is available to process this command."  I should have tried that earlier, oh well.

Anyhow, that KB article fixes it right up.

---

