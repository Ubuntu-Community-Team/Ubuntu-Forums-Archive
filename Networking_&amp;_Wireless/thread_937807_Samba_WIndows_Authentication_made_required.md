---
title: "Samba WIndows Authentication made required"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by timZZ on 2008-10-04
Hi,

[At work]
when a user on a windows client makes the first connection to the linux box (fedora core 6) from an XP professional machine.  The user is asked for a username and password.

[At home]
My windows XP Professional client can easily access the share on my Ubuntu 8 Hardy but the server does not request any authentication and the user is allowed full access.

Is there away to ask the client (windows XP Professional) to authenticate before asking the shares on the (Ubuntu 8 Hardy) server?

Here is the Samba config. (smb.conf)

[music]
path = /home/user1/Music
available = yes
valid users = user1
read only = no
guest ok = no
browsable = yes
public = yes
writable = yes

For a test I made a user1 and I am allowing user one to access there Music folder.

Problem is any of the XP clients on the machine can access this folder and do what they want.

If you need more of the samba config please let me know.

---

### Post by timZZ on 2008-10-04
Can anyone help? I am curious as nobody has ever replied to my post even once since the entire time I have been using this site.

I am willing to explain, word things differently.  But I am very confused to why none not even one reply to any of the questions I have ever posted on this site.

---

### Post by putz3000 on 2008-10-04
Well in my case I am able to force a login/password but I am unable to get the server to accept authentication.  I said "guest ok = no" but I also used "force user = <name of user> and "force group = <name of grop>".  If I make the guest ok = yes then I can just connect right into the share (not what I want to do).  My guess is you are going to have to put some sort of no guest cammand into your smb.conf file.  Unfortantly I am pretty new to samba and since I am unable to get my own working fully, I am affraid I am unable to help you in a specific way.

---

