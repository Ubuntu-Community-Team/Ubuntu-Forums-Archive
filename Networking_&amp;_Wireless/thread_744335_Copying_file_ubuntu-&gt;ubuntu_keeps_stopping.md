---
title: "Copying file ubuntu-&gt;ubuntu keeps stopping"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by Jethro_uk on 2008-04-03
Have 2 ubuntu 7.10 machines. Both connect flawlessly to internet (one wireless, one not)

have installed networking components for file sharing on one, and can connect and browse sucessfully from the other (I used "add server" from "PLaces" menu)

However, trying to copy a 4.4Gb file from the "server" to the otehr machine (from the other machine, so it's a "pull) keeps failing after a few seconds. No error message. The  "copying files" window just stays there, and the time starts increasing. I have to use PM to kill nautilus to get it to go.

Since my entire aim of using Linux is to put the "server" in the loft and use it as a 24/7 media server, this could be a problem.

Could anyone suggest anything please ?

I've looked in the logfiles, and nothing immediate jumps out

---

### Post by Eiríkr on 2008-04-03
Any idea how you're sharing?  What advice to give you varies widely depending on whether you're sharing over sftp, nfs, or Samba.  (Incidentally, if Samba is the issue, the default log is not the syslog, but rather /var/log/samba/log.smbd.)

Cheers,

Eiríkr

---

### Post by Jethro_uk on 2008-04-03
being a  newbie I thought creating a unix share would do it.

However I appear to have worked around by using gnome-commander and creating a windows share ?
Why does G-C look for samba shares by defaul ?

---

### Post by Jethro_uk on 2008-04-03
spoke too soon ! got to 98 Mb then "timeout reached".
wtf is going on ?

---

### Post by Eiríkr on 2008-04-03
Windows sharing is based on the Server Message Block or SMB protocol, developed by IBM back in the 80s.  Microsoft picked it up for their own purposes around 1990-92 or so (more in [the Wikipedia article](http://en.wikipedia.org/wiki/Server_Message_Block)).  So Windows sharing in Linux terms is very much Samba sharing.  

Now that we've got it roughly figured out that you're using Samba, there are many different things that might be acting up.  Tracking down your specific problem will probably take several hours, and mucking about with the /etc/samba/smb.conf files on your two machines (if you want two-way sharing).  This is very complex, because Samba is huge and complicated, much like Windows.  :(  But hey, if you're sharing with Windows, you need to get the fugly on, or it won't work.  :)  In your case, you're just doing basic Lin -> Lin sharing, so you don't specifically need Samba.  

For simplest sharing, I'd suggest you install the ssh package on both machines.  Then, just open your Nautilus file browser, click the location bar (hit Ctrl+L or click View -> Location Bar if it's hidden), and type:
```
sftp://IP.ADD.RE.SS
```
Replace the caps with the IP address of the other machine.  You'll see the usual login prompt for username and password, and then you're in.  No muss, no fuss, faster sharing, and no configuration needed.  :D

Cheers,

Eiríkr

---

### Post by Jethro_uk on 2008-04-04
Thanks Erik, makes more sense now.

I thought by using the "Connect to server" button on "Places" from the main menu I was creating an SSH connection ? I'll do some more experimentation tonight (I'm at work at present).

When I first started messing with Ubuntu, I had a couple of files I wanted to transfer from my "evaluation" copy which was on my old machine, and my "proper" copy which was on my new machine. I was messing around then with nautilus and SSH, and it didn't work properly then. In the end I used a memory stick :(

---

### Post by Jethro_uk on 2008-04-04
Hi there,

did as asked, and exactly the same happened. The transfer hung after 12 Mb ...
 Can anyone suggest something ... this is a bit of a showstopper

---

### Post by andguent on 2008-04-04
I'm always suspicious of wireless whenever that is involved. Are you able to move the wireless computer to a place where you can hard wire it to the network and try your copy tests again?

Also, one nice way to test if the networking is working is to simply ping the other computer, but with the -f switch, or 'flood'. It sends 1000+ pings per second, and if you get a bunch of .............'s on the screen, each of those are network failures. 

One or two failures per 10 seconds is resonable. Anything more than one or two failures and you are dealing with a different issue. In that case it isn't a samba/ssh/sftp problem, it is a network cable, switch, or wireless problem. Let the ping -f IP.ADD.RE.SS run for at least as long as the file transfers would work.

---

### Post by Jethro_uk on 2008-04-04
Thanks ... will try that immediately

For diagnostic purposes I installed SSH on the other server, tried connecting to that from the host server and tried copying the files the other way (FROM host TO target on the HOST, as opposed to FROM host TO target on the target). The result was similar (stopped after 6Mb) however I left it while having dinner, and came back to a "protocol error" message ... so some clue there.

I appreciate your wireless wariness, however the same machine can connect to the internet and happily torrent down a 650 Mb file with no problems ...although the wireless isn't *perfect* as it does drop out after 18-24 hours for no apparent reason. However since the torrent (gnome torrent) client did this when wired, I'm not sure what to think ......

---

### Post by Jethro_uk on 2008-04-04
```
PING 192.168.1.102 (192.168.1.102) 56(84) bytes of data.
ping: cannot flood; minimal interval, allowed for user, is 200ms
```


mean anything, anyone ?

---

### Post by Jethro_uk on 2008-04-04
I have just tried look in \var\log\samba, but nothing there. I then tried using "secpanel" which happily connected, but went to "stalled" after a few meg. Up till that point I was getting 200Kb/s, so I don't think there's much of a problem with the quality of the link. ....

---

### Post by The Cog on 2008-04-04
> **Jethro_uk said:**
> ```
PING 192.168.1.102 (192.168.1.102) 56(84) bytes of data.
ping: cannot flood; minimal interval, allowed for user, is 200ms
```


mean anything, anyone ?

Yeah - you need to have root privs to do that. Try putting **sudo** in front.

---

### Post by Jethro_uk on 2008-04-04
Thanks for that. Here's the results .... surely 1% loss isn't too bad for a wireless link ?

```
192.168.1.102 ping statistics ---
51350 packets transmitted, 50335 received, 1% packet loss, time 423424ms
rtt min/avg/max/mdev = 5.256/13.070/516.028/45.955 ms, pipe 44, ipg/ewma 8.246/7.951 ms

```

---

### Post by Jethro_uk on 2008-04-04
More info ...

the machine I am trying to copy TO is a dual-boot XP box, so I booted XP, installed WinSCP, and tried that. It connected fine, started the transfer (at 600 KB/s) and after about 20Mb popped up a message saying it hadn't had a response for 15 seconds, at which point the transfer stopped.

This is looking like something to do with Ubuntu ... can anyone help, please ?

---

### Post by The Cog on 2008-04-04
I agree that wireless is  probably still a likely suspect. I wonder if it might be dodgy drivers.  Is there any way you can try it wired instead?

---

### Post by andguent on 2008-04-04
> **Jethro_uk said:**
> Thanks for that. Here's the results .... surely 1% loss isn't too bad for a wireless link ?

```
192.168.1.102 ping statistics ---
51350 packets transmitted, 50335 received, 1% packet loss, time 423424ms
rtt min/avg/max/mdev = 5.256/13.070/516.028/45.955 ms, pipe 44, ipg/ewma 8.246/7.951 ms

```

Actually, that might not be that great. If possible, let that same ping flood run for 20-30 minutes and then see if it still is at 1%.

@ TheCog & Wifi: Agreed, please repeat all of these tests on a wired connection. If it still occurs, use a crossover cable between the computers to truly rule out all other equipment like your router.

---

### Post by Jethro_uk on 2008-04-11
turned out the ***ing file was corrupt !!!!!

however all this has told me I just cannot trust wireless for a PC which is going to be fairly inaccessible .... so I'm resigned to running cables to the loft.

---

