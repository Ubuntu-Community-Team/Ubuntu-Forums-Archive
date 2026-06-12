---
title: "Can't connect to  Windows Home Server ( WHS ) wirelessly"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by MPacheco on 2011-06-10
Hello All,

Trying to make the jump from MS to Ubuntu, but could use some help.

I've installed Ubuntu 11.04 on a laptop and can connect to our Win Home Server 2003 via ethernet cable, but can't get the connection back when I switch to wireless.  On a Win7 laptop, it doesn't make a distinction between wired or wireless when connecting to our server, but clearly Ubuntu does.

When I do try to connect via wireless, I get the msg: Could not open location 'smb://server/users/'

Any guesses on how to connect wirelessly to WHS?  Any guidance is greatly appreciated.  Thanks, in advance.

- MP

---

### Post by papibe on 2011-06-10
Are you using the same network config on both connections? That is, the same DNS server (probably your router).

Could you ping the server while using the wireless connection? 

Have you tried reaching the server using its LAN ip? (like something similar to smb://192.168.1.64/users/)

Regards.

---

### Post by MPacheco on 2011-06-10
Issue Update

I was able to connect wirelessly to the server and gain access to the  'user' files going through Places/Connect to Server, changing the  Service Type to Windows Share and then entering the server's IP address  (192.168...) as you suggested, but that only gives me access to the user files, not the  Music, Photo, Video, and other directories at the same level as Users.

My goal is to create shortcuts in the Places drop down menu to the various directories on the server, but before I can do that, I have to have access to those directories.

Any thoughts/suggestions?

Nice photo, BTW; beautiful coat.  My dog doesn't hang his coat up as it's all over the living room floor  all the time!

---

### Post by MPacheco on 2011-06-10
Getting Closer...

I was able to connect to all the directories as when I tried going to Places/Connect to Server again, the system did not ask for a userid-password and did not send me directly to Users, so I have access to all files.

What I cannot seem to do is make a permanent link so I don't have to "Connect to Server" each time I want to access the server.  How do I make this connection automatically reconnect the next time I want to access the server?

As always, I appreciate any advice.

-MP

---

### Post by papibe on 2011-06-10
> **MPacheco said:**
> but that only gives me access to the user files, not the  Music, Photo, Video, and other directories at the same level as Users.
Can you see those folder from Windows? I guess so. How are you authenticating from Ubuntu to your WHS? Do you have the same user and password on your Windows Client than in your Ubuntu?

> **MPacheco said:**
> Nice photo, BTW; beautiful coat.  My dog doesn't hang his coat up as it's all over the living room floor  all the time!
Thanks!, I try to brush him as often as I can (twice a week maybe). I have a secret weapon though: The [Furminator]("http://www.furminator.com/") (every other month).

Regards.

---

### Post by Morbius1 on 2011-06-10
> What I cannot seem to do is make a permanent link so I don't have to "Connect to Server" each time I want to access the server.How have you been trying to do it so far?

Did you bookmark it: Connect to the server using "Connect to Server" then  > Bookmarks > Add bookmark.

---

### Post by MPacheco on 2011-06-10
I was trying to make an icon with a link to the server show in the Places file, but couldn't make that happen, so I tried the bookmarking as you suggested and that's a good work around.

Thanks!

---

