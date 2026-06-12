---
title: "In Need of a HowTo"
date: 2006-09-18
forum: Networking &amp; Wireless
---

### Post by moore.bryan on 2006-09-18
[I]i've scoured our pages here and out in the big bad net, but with little to no luck.  i'm looking for a straight-forward howto about connecting to my ubuntu machine via my work windows machine.  some specs:
```
ubuntu machine: dapper 6.06, running openbox, cable internet via comcast
windows machine: 6 year-old gateway laptop, running windows xp, sp2, t3 line
```
i've read suggestions about freenx and using gnome's remote desktop, but there's no step-by-step that i found to checklist as i go through.  i also read something about if i have an isp-issued dns to use freedns or something.  help!  can anyone point me in the right direction?
thanks, in advance.
[/I]

---

### Post by nullmind on 2006-09-18
Did you try Samba?

---

### Post by moore.bryan on 2006-09-18
*i read through (and re-read through) the samba directions, but they weren't very clear to me... maybe i was looking at the wrong one.  is there a good guide?*

---

### Post by Iowan on 2006-09-18
[http://www.ubuntuforums.org/showthread.php?t=202605]("http://www.ubuntuforums.org/showthread.php?t=202605") Here's **_A_** guide.  Correct me if I'm misunderstanding, but I suspect your difficulty is more with getting from work to home than accessing the files.

---

### Post by moore.bryan on 2006-09-18
> **Iowan said:**
> [http://www.ubuntuforums.org/showthread.php?t=202605]("http://www.ubuntuforums.org/showthread.php?t=202605") Here's **_A_** guide.  Correct me if I'm misunderstanding, but I suspect your difficulty is more with getting from work to home than accessing the files.
*i guess... i want to, basically, use my home pc (ubuntu) as server of which files i can access at work (xp).  i've read a lot about samba and freenx, but neither one seems clear.  as i read through it goes "do this, this, then this, and voila" but none of the "this's" make sense.*

---

### Post by tbonius on 2006-09-18
If you want to use your home Linux computer as a "File Server" that you can "openly" access with Windows .. then good luck.  The most common way to access files across a network with Windows is via SMB.  SMB allows you to connect to "shares" on a remote computer and view (and even change) files in the "shares".

I think you need to figure out what exactly you want to do.. the methodology of it first.

There a re a few common ways to connect to remote computers and access files.

NFS - Network File System.  
SMB - Server Message Block/NetBIOS
FTP/SFTP - File Transfer Protocol/Secure File Trabsfer Protocol

Most ISPs will block NFS (portmap) and SMB (NetBIOS) ports.. this of course is for security purposes.  If they did not then it would be a free for all.  Some ISPs choose to leave SMB and NFS ports open.. but only WITHIN their network.. so maybe one ComCast user in Seattle could access another Comcast user's "shares" in Tacoma.. but maybe not in Boston.

It sounds like all you want to do is access files.  If that is the case.. then check into SSH/SFTP.  This is a fairly secure method of remotely connecting to your Linux computer to gain access to a shell or to transfer files.  

If you are looking for more of a remote desktop option.. then maybe VNC is for you.  This might not let you "directly" access the files on your work computer .. but you can connect remotely to the desktop of your Linux computer and access files there.  

All of these methods require opening and maybe even forwarding ports to your Linux machine.. and with a little securing services.. you can be up in no time.

That is.. assuming that work even allows the types of service traffic you need in order to gain access to your computer at home.

T

---

### Post by nullmind on 2006-09-19
If you are interested in using FTP proftpd is a good solution (or at least works well for me)

I'm on Comcast in Salem, Oregon and have no trouble accessing my SMB shares outside my network. Comcast doesn't seem to block any of my ports, including port 80 which remains open.

I've read a lot about Comcast blocking ports, and always find it weird that the ports are never blocked for me. I'm not saying I don't believe anyone, I'm just pointing out that it's never been blocked for me.

Cheers,
Kris

---

### Post by moore.bryan on 2006-09-19
*thanks t and kris... last night i figured i'd try freenx.  got it setup and running on the ubuntu machine at home.  when i tried to login here at work this morning, the nxwindows client couldn't do it.  i'm behind a very protective firewall and need authentication in and out.  i have that, but there's no where in the nxclient config to input a username and password for proxy... any ideas?*

---

### Post by moore.bryan on 2006-09-19
[I]UPDATE
i was able to "alter" my work's proxy config to allow my ubuntu machine's ip without authentication.  now i get the ssh error my connection is refused.  wtf?
[/I]

---

### Post by nullmind on 2006-09-19
I don't know much about Freenx, I have it installed on this machine at home and my friend connects from a Windows machine off-site. He says it randomly does weird things, even though I have the ports forwarded and all.

---

### Post by moore.bryan on 2006-09-19
*i've received a few suggestions about this and it looks like openssh on ubuntu and winscp is the way to go for me... do you guys know any good howto's on them?*

---

### Post by tbonius on 2006-09-19
I dont think it really requires any how-to's.  Install open-ssh server:

sudo apt-get install openssh-server

Once its done.. make sure port 22 is open and forwarded on your router/firewall at home so that you do not get "connection refused" when trying to connect.

Download Putty for SSH and WinSCP for SCP/SFTP connections.

[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

[http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)

Connect to Public IP address of Firewall/Router at home.

T

---

### Post by moore.bryan on 2006-09-20
[I]all right, here goes:
i can winscp AND putty into ubuntu, but freenx won't go.  i figured out it was the "i had 2.0 installed and 1.5 works better" issue, so i downgraded.  now, freenx-client connects from my xp machine, but abruptly closes without issuing and error statements... more ideas?
[/I]

---

### Post by moore.bryan on 2006-09-20
*one of my main uses for this is to have access to media and business files on my home pc at work; meaning, will i be able to play music/watch videos/edit files from work through winscp/putty/freenx?*

---

### Post by crazymonkey on 2006-09-20
[NXServer tutorial]("http://ubuntuforums.org/showthread.php?p=1190037#post1190037") (Not FreeNX, NXServer, the free edition from NoMAchine)

[Samba tutorial]("http://www.ubuntuforums.org/showthread.php?t=202605")

I used those two tutorial and I got everything up and running easily. I use the free version of NXServer, more stable than FreeNX.

---

