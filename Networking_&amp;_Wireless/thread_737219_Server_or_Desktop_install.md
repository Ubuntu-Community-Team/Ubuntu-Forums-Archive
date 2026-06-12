---
title: "Server or Desktop install?"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by shane2peru on 2008-03-27
Ok, I'm rather ignorant to all of this.  I recently found out about server installs, and am interested in learning a little more.  First off, I run 3 Ubuntu computers all connected to my LAN.  One is wireless and two are wired.  Someone was telling me they run a server and it allows access to all users (or something of that effect).  So I started thinking, maybe I should investigate this server stuff.  I have all computers networked, and can share some files, although this has taken some extra effort, and recently I have tried to share printers too.  My ideal setup would be to allow users to share data and folders very easily, and even to keep all Pictures and some other files so anyone can access them.  All users are trusted, and it isn't a problem for me to have a rather open network setup, so long as I'm protected from the hackers outside (from the internet).  I do not have one computer to dedicate to a server, so my server (probably my computer) would also double as a desktop computer.  So,

1.  Would I be better off setting up a server for this style of setup?

2.  Would a server make my setup easier, or more complex?

3.  Is setting up a server less secure than setting up everyone networked?

4.  Can I easily accomplish all of this without the use/need of a server?  (Please post some simple instructions).

Any help or info would be greatly appreciated.  I'm just a normal user, not a tech, not a programmer, I do have a great interest in computing, and enjoy learning.  Thank you for your help.  Perhaps someone could clarify if a server would be of help or not.  Thanks!

Shane

---

### Post by sowelie on 2008-03-27
Well, if you're talking about a home environment, a server is almost never necessary. However in a work environment it is definitely useful to have a server for centrally located files / printers etc.  The server setup is no more difficult than setting up file sharing / printers on a desktop install.  I have never used ubuntu server, but I'm assuming the only difference is by default the GUI is disabled.  So you just have to set everything up on the command line, which is easier and more straightforward anyway, although you'll need direction.  It is no less secure, as long as your network is behind a firewall.  The server doesn't expose anything unless you intentionally expose it through your firewall.  I browsed the ubuntu documentation and quickly found this section which should be a good starting point for you:

[https://help.ubuntu.com/7.10/server/C/]("https://help.ubuntu.com/7.10/server/C/")

---

### Post by BDNiner on 2008-03-27
For simple file and printer sharing you don't need a server. Since you don't have a dedicated machine for the server then I would not turn your computer into a server. They can be but are not meant for everyday personnal computer use so it would be a waste of time.

---

### Post by kerry_s on 2008-03-27
i don't think you need a server, i think you would be better off with a network storage device instead.
something like this(taken from the top of first google)
[http://www.pcworld.com/article/130793-1/article](http://www.pcworld.com/article/130793-1/article)

---

### Post by shane2peru on 2008-03-27
> **sowelie said:**
> Well, if you're talking about a home environment, a server is almost never necessary. However in a work environment it is definitely useful to have a server for centrally located files / printers etc.  The server setup is no more difficult than setting up file sharing / printers on a desktop install.  I have never used ubuntu server, but I'm assuming the only difference is by default the GUI is disabled.  So you just have to set everything up on the command line, which is easier and more straightforward anyway, although you'll need direction.  It is no less secure, as long as your network is behind a firewall.  The server doesn't expose anything unless you intentionally expose it through your firewall.  I browsed the ubuntu documentation and quickly found this section which should be a good starting point for you:

[https://help.ubuntu.com/7.10/server/C/]("https://help.ubuntu.com/7.10/server/C/")
From this it seems easier to setup a server to share everything I want to share.  I do have a homenetwork, however it is kind of like a home office, because we have a lot of work that is done on/in our home with computer.  (Perhaps I should have clarified that before).  

> **BDNiner said:**
> For simple file and printer sharing you don't need a server. Since you don't have a dedicated machine for the server then I would not turn your computer into a server. They can be but are not meant for everyday personnal computer use so it would be a waste of time.
My computer is left on most of the time, however would turning it into a server slow it down?  Perhaps you could explain a little more on how this would be a waste of time.  Would it require more of my computer?  I'm running a 64bit with 1.5GB of ram.  Overall it has some decent specs.  Intel Pentium D processor.  
> **kerry_s said:**
> i don't think you need a server, i think you would be better off with a network storage device instead.
something like this(taken from the top of first google)
[http://www.pcworld.com/article/130793-1/article](http://www.pcworld.com/article/130793-1/article)

Thanks, but I don't think this is really feasible for where we live.  It would be a great idea, however we live in Peru, and in a small town at that, adding hardware is more expensive than what I can get in the USA, and generally a real pain to get my hands on.  I will keep this in mind though as it could be something for future use for us.

Wow, seems to be mostly negative for the server, does anyone have any positives on setting up a home server?  What would be the benefits of doing this?  Or isn't there any?  Thanks for the very quick and helpful responses.

Shane

---

### Post by BDNiner on 2008-03-27
No, it will not be slowed down considerably. Your computer would make a great server by the specs alone. It is common practice to keep servers as standalone machines because it is easier to fix problems without adding in a human element. That way you know everything that is installed on the server at all times. Once a server is up and running there is little reason to log into the machine unless something stops working. By looking at your specs. if you really want a server and don't have an extra computer you could look into vmware or virtual box. We do use virtual machines at work for our DNS servers.

---

### Post by shane2peru on 2008-03-27
> **BDNiner said:**
> No, it will not be slowed down considerably. Your computer would make a great server by the specs alone. It is common practice to keep servers as standalone machines because it is easier to fix problems without adding in a human element. That way you know everything that is installed on the server at all times. Once a server is up and running there is little reason to log into the machine unless something stops working. By looking at your specs. if you really want a server and don't have an extra computer you could look into vmware or virtual box. We do use virtual machines at work for our DNS servers.

By the looks of things, a server and Desktop installation would be more complex than it is worth.  However, I'm not really having the luck of sharing my printers and folders in an open and easy way with different user names.  That is why I was thinking possibly setting up a server would simplify things, however that too is looking complex!  I appreciate the help and info.  Let me change the thread just a bit, and ask, 

1.  How can I simply setup a way to share folders (without all the permissions problems (different user names) and printers across my home network with all Linux computers?  

There seems to be a wealth of information on getting Linux-Windows talking and working, but not Linux to Linux.  Perhaps this is such a simple process that everyone but me knows how to do that.  Any simplified instructions and help would be appreciated!  Thanks!

Shane

---

### Post by BDNiner on 2008-03-27
You can right click on any folder and select "share folder...". you can then decide the parameters for your share. the most basic way is either windows share or samba. You must then right click the folder again and go to permissions and give the users the correct permissions to access the folder. 

Then go to the other computers on your network and go to places->connect to server and put in the IP address of the machine that has the shares and you are done. you should be able to view and edit the files on your "server" computer according to the permissions you set.

---

### Post by shane2peru on 2008-03-27
> **BDNiner said:**
> You can right click on any folder and select "share folder...". you can then decide the parameters for your share. the most basic way is either windows share or samba. You must then right click the folder again and go to permissions and give the users the correct permissions to access the folder. 

Then go to the other computers on your network and go to places->connect to server and put in the IP address of the machine that has the shares and you are done. you should be able to view and edit the files on your "server" computer according to the permissions you set.

Thanks for this info.  I did the following and set up the entire user folder to be shared and made it so that it is in a group at allows everyone in that group to read and write to that folder, then shared the folder (I used NFS, not the samba thing, as it is my understanding that samba is more for windows users).  Now when I go to places and connect to server, I get the following options: SSH, FTP, Public FTP, Windows Share, WebDAV, Secure Web DAV, Custom.  I assume the SSH would be the one I would want to use?  Does that all seem fine what I did?  it was the only way for me to work around the permissions for other users.  Now I can limit users by not including them in that particular group.  Does this all sound fine as far as security is concerned?  Thanks for the help!

Shane

---

### Post by BDNiner on 2008-03-28
Yes you can use SSH, it is definately more secure, but since all your computers are "trusted" then you don't have to use SSH. I would use SSH if i was connecting to my home computer from outside the network. I use "windows share" on my network but i have 3 ubuntu computers and 1 windows computer. But i don't have multiple users so I have no idea how to help you with that problem. I would look into creating a new group to control the access to the shares, but i don't know too much about it so don't take my advice until you communicate with another user here or research the issue.

---

### Post by shane2peru on 2008-03-28
> **BDNiner said:**
> Yes you can use SSH, it is definately more secure, but since all your computers are "trusted" then you don't have to use SSH. I would use SSH if i was connecting to my home computer from outside the network. I use "windows share" on my network but i have 3 ubuntu computers and 1 windows computer. But i don't have multiple users so I have no idea how to help you with that problem. I would look into creating a new group to control the access to the shares, but i don't know too much about it so don't take my advice until you communicate with another user here or research the issue.

BDNiner,

Thank you for your help.  I think I will stick to SSH as it seems to work.  I use that for the command line to update the other computers too, but it is very nice knowing how to be able to do the same thing graphically.  As for the group, that is exactly what I did.  Seems to work, and then I can keep some people out of that group eliminating any kind of 'untrusted' access.  Like my kids account. :)  That seems to be the best rout for me to take.  Thanks again!

Shane

---

