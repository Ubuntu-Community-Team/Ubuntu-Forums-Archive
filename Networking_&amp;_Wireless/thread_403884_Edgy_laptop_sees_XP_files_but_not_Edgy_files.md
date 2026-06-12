---
title: "Edgy laptop sees XP files but not Edgy files"
date: 2007-04-07
forum: Networking &amp; Wireless
---

### Post by SteveHoffmanUK on 2007-04-07
Dell Latitude Edgy connected to wireless home network with two other machines: Win XP and Edgy desktops. Wireless works fine. Edgy laptop ¨sees¨ both desktop machines OK, but when I try to access the files on the two desktops from the laptop, I can read all the XP files, but there are no files showing for the Edgy desktop.

What would cause this? Both Edgys have ext3 file systems. I could understand that there might be a problem for Edgy to read XP files, but why a problem reading Edgy files on another machine?

---

### Post by dfm21 on 2007-04-07
**Client**
Try```
sudo mkdir /media/files
sudo mount -t nfs name-of-the-server-where-files-are-stored:/path/to/your/files /media/files
```

**Server**
Do you share your folders on the machine you try to access (System > Administration > Shared Folders)?
Did you install the **nfs-kernel-server**? Try:```
ls /etc/init.d/ | grep nfs-kernel-server
```It should print nfs-kernel-server.

Check your **/etc/exports**```
cat /etc/exports
```.
You probably want every machine in your LAN access the shares, so you need to add a line like this (with your IP address range):
```
/       10.1.2.0/255.255.255.0(rw,sync)
```
This grants all machines with an IP 10.1.2.X (netmask 255.255.255.0) read and write access to "/". I think the sync means that changes are written instantly...
Be sure to read the [SettingUpNFSHowto]("https://help.ubuntu.com/community/SettingUpNFSHowTo#head-ac7dfba15ed58c9d4cdb3417a2ab2f2433d444f0") at [help.ubuntu.com]("https://help.ubuntu.com/community/SettingUpNFSHowTo#head-ac7dfba15ed58c9d4cdb3417a2ab2f2433d444f0")!

---

### Post by SteveHoffmanUK on 2007-04-08
dfm21: thanks very much for your reply. I am not very experienced with networking on Ubuntu, so I am not clear about some of your comments. 

You wrote about clients and servers, but I don't really have a client/server setup (at least I don't **think** I do. I have two desktops, one running XP, one running Edgy, and I have one laptop running Edgy. These all use a wireless broadband modem to connect with each other and with the Internet. Is the broadband modem the server? I'm confused and not sure :confused: 

You wrote:
```
sudo mkdir /media/files
sudo mount -t nfs name-of-the-server-where-files-are-stored:/path/to/your/files /media/files
``` 
Sorry, but what is nfs? (You can see how little I know!)

You wrote:
> Do you share your folders on the machine you try to access (System > Administration > Shared Folders)?
Yes (I think). When I do that on my Edgy desktop, it shows my Home folder as shared.

You wrote:
> Did you install the nfs-kernel-server? Try:
Code:

ls /etc/init.d/ | grep nfs-kernel-server

It should print nfs-kernel-server.


When I do that, nothing prints out.

You wrote:
> Check your /etc/exports
Code:

cat /etc/exports



I get "No such directory" message.

I think I'll stop there. Does this shed any light on my situation (other than showing how little I know, of course!!):) 

Thanks again for trying to help.

---

### Post by dfm21 on 2007-04-11
Hi again!

Sorry for taking so long to write back, but I had some mail problems and therefore was not notified of your reply.

I hope I got this right:
You have a working network connection between your n**otebook (NB), desktop 1 (D1) and desktop 2 (D2)**.
Your problem is that NB shows Windows shares (aka. SMB shares) of both D1 and D2, but after booting Edgy on D1/D2 you can not see their ext3 file systems from NB.
I assume the following IP Addresses:
D1: 192.168.0.1
D2: 192.168.0.2
NB: 192.168.0.10

You have to do the following to share folders of D1 and see them on NB:
**Open a Terminal on D1 and type:**
```
sudo apt-get install portmap nfs-kernel-server
sudo gedit /etc/exports
```
and in gedit add the following line to /etc/exports:
```
/home 192.168.0.10(rw,sync)
```
Now restart the NFS server with ```
sudo /etc/init.d/nfs-kernel-server restart
```
You have instructed your server (D1 in this case) to share /home with the PC that has 192.168.0.10 as its IP address (NB).
**on NB:**
Now you need to make your client (NB) get the files from the server.
To do that you need a point where YOU know the server's files will be. This is also called a "mount point" and is usually created under /media/, thus you type to a terminal on NB:
```
sudo mkdir /media/d1-files
sudo mount -t nfs 192.168.0.1:/home /media/d1-files
```

A "ls /media/d1-files" executed on NB should print the same as a "ls /home" on D1.

The way I presented you is one of many. We used the NFS server to make a folder available on the net and used "mount" to mount a remote file system.

I hope this helps.

---

### Post by SteveHoffmanUK on 2007-04-11
dfm21: thanks very much for your patience and for trying to help me through this.

Before I try anything, I need to correct a couple of your assumptions. They may not be important corrections, but I think I should make them;

You wrote:
> I hope I got this right:
You have a working network connection between your notebook (NB), desktop 1 (D1) and desktop 2 (D2).
Correct. They connect to each other and to the Internet via an ADSL router.

> Your problem is that NB shows Windows shares (aka. SMB shares) of both D1 and D2, but after booting Edgy on D1/D2 you can not see their ext3 file systems from NB.
Not quite right. My problem is that NB shows Windows shares (aka. SMB shares) of D2, but after booting Edgy on D1, I cannot see its ext3 file systems from NB. D1 runs Edgy only; D2 runs WindowsXP only. (Maybe this isn't important.) 

Then you wrote:
> I assume the following IP Addresses:
D1: 192.168.0.1
D2: 192.168.0.2
NB: 192.168.0.10

Question: Why do you assume this? How are the IP Addresses assigned to these three machines and how do I confirm whether or not you are correct in your assumption? 

I think I need to know this first before I put something in etc/exports that is based on your assumptions, do I not?

I have now read the Wikipedia entry for NFS, so I think I understand the client/server aspects of NFS, and how the sharing is done.

Thanks again for your help.

---

### Post by dfm21 on 2007-04-11
So you have Edgy on NB running and can not see the files on D1?
By what means can you "see" the SMB shares on D2? If you run Edgy with a default installation Nautilus should be your browser.
> Question: Why do you assume this? How are the IP Addresses assigned to these three machines and how do I confirm whether or not you are correct in your assumption?

I assumed these IP addresses so I could give you a specific line for /etc/exports , i.e. "/home 192.168.0.10(rw,sync)". This line tells the NFS server that /home should be shared with the machine that has the address 192.168.0.10. I picked this example at random and the only one who knows which IP addresses are assigned to each machine is you - or your router if it has DHCP enabled and thus assigns IP addresses automatically.

Maybe this was not the best approach...
You should be able to share folders very easily by going to System -> Administration -> Shared Folders. Then create a new share, select "smb" and click OK.
I am on a Windows box right now, so I do not know the exact terms, but they should be recognizable. ;)

If you do not succeed with this approach, then I will need some more information:
1. By which means do you (try to) "see" shares of D1/D2, i.e. which browser do you use?
2. What are the real names of your PCs? Can you ping them by name?
3. How did you try to share the folders of D2 in the first place?

I look forward to the day when this works and you can help other people to set up shares on a LAN. :)
You are welcome.

---

### Post by SteveHoffmanUK on 2007-04-12
dfm21, thanks again for helping me understand. I think I'm making some progress, but first, to answer your questions:

> So you have Edgy on NB running and can not see the files on D1?
Correct.

> By what means can you "see" the SMB shares on D2? If you run Edgy with a default installation Nautilus should be your browser.
In my desktop (D1) GUI, I click Places | Network Servers | Windows Network | MSHome and there appear two icons, one for D2 and one for D1; no sign of NB. Yes, I assume I am using the default file browser for Edgy, which is Nautilus.

> This line tells the NFS server that /home should be shared with the machine that has the address 192.168.0.10. I picked this example at random and the only one who knows which IP addresses are assigned to each machine is you - or your router if it has DHCP enabled and thus assigns IP addresses automatically.

OK, I logged into my router (Netgear Super ADSL Wireless Router DG834GT, IP address 192.168.0.1) and under 'Attached Devices' I find this table:
```
1  	192.168.0.2  	D2  	00:80:C8:CE:EA:3E
2 	192.168.0.3 	D1 	00:80:C8:00:1C:56
3 	192.168.0.4 	UNKNOWN 	00:11:50:90:55:3C
```
(I have changed the real names to "D1" and "D2" to avoid confusion.)
So, now I know the IP addresses of my three machines, assuming that 'UNKNOWN' must be my NB. Why is it "unknown", I wonder? I gave the NB a unique name when I installed Edgy on it.

> Maybe this was not the best approach...
You should be able to share folders very easily by going to System -> Administration -> Shared Folders. Then create a new share, select "smb" and click OK.
I am on a Windows box right now, so I do not know the exact terms, but they should be recognizable. 

BINGO! Yep, worked straight away. I defined my Home folder as shared and now I can see D1 and all my files from NB. 
Mystery solved - thanks very much for your patience and help.=P~ 

Well, the one mystery remains: why does my NB have a name that is "unknown" to my router? It should be "steve-laptop", which is the name I gave it when I installed Edgy. Is there some way I can check its name on NB?

ON EDIT: Answered my own question: the reason is was 'unknown' was that I hadn't installed any file sharing software on NB. Once I did that, then the router shows it as 'LAPTOP' and not 'UKNOWN'. Now I can "see" all machines on the network from all other machines. Magic!!

Thanks again. Absolutely brilliant.

---

### Post by dfm21 on 2007-04-12
I am happy to hear that everything works!
> the reason is was 'unknown' was that I hadn't installed any file sharing software on NB.
Yes. Your router probably looks for the "Windows Names" of your PCs to identify them. After installing file sharing software on your notebook it sent a broadcast message to it's neighbors (D1, D2 and your router) - "telling everyone" its NetBIOS name. (You do not need this information necessarily, but I thought you might find it interesting anyway.)

If you have only three PCs on your LAN, you might consider using static IP addresses. Your PCs always have the same IP address which should speed up booting the clients quite a bit.
Another advantage is that you can use the [COLOR="DarkGreen"]/etc/hosts[/COLOR] file to bind IP addresses to human readable names (for faster access).

This is my [COLOR="DarkGreen"]/etc/hosts[/COLOR]
```
127.0.0.1 localhost
127.0.1.1 dfm1
10.1.2.33 router
10.1.2.1 whisper

```
So if I want to see the shares of whisper I just press <ALT>+<F2> (the run dialog), type [COLOR="DarkGreen"]smb://whisper[/COLOR] and up pops nautilus with a list of whisper's shares -- no waiting for the other network servers in the window of the same name.
I also can check if whisper is only by running [COLOR="DarkGreen"]ping whisper[/COLOR] and so on....

The hosts file exists on Windows machines too (C:\WINDOWS\SYSTEM32\DRIVERS\ETC\HOSTS).

Keep the spirit up! :guitar:

PS: Please mark this thread as solved! Click [edit] on your first post then [Go Advanced] then check "Check box if your thread **IS** resolved.". Thanks!

---

### Post by SteveHoffmanUK on 2007-04-12
dfm21:

Thanks for the additional explanations - just a bit more of the mysteries of Ubuntu solved (long way to go, though!).

I have logged into my ADSL router and can see how to do the static IP address assignment: seems to be something called "allow trusted sites": you have to key in the MAC address for each machine and its name, then it will only allow those on the list access to the wireless LAN: a bit of additional security as well, although I'm sure that the WEP key is good enough for me.

Thanks also for the tip on marking a thread solved - I didn't know about that.

---

### Post by dfm21 on 2007-04-13
fine.
I consider my work done here. ;)
Here in Germany you need to encrypt our WLANs or you are punished if someone else does illegal things using your connection, so I use WEP too. But you should be aware that WEP (even at the highest level) is crackable in several minutes - so it's enough to protect you from the consequences of certain laws, but really does not make your network secure.

so long

---

### Post by SteveHoffmanUK on 2007-04-13
Yes, I have read elsewhere that WEP isn't terribly secure. As one writer put it, "It's about as secure as my granny's false teeth". 

The reason I feel it's OK for me is my particular neighbourhood, where the houses are quite far apart, my 160 year old house has very thick walls and the neighbours aren't likely to be very sophisticated hackers. Yeh, OK, someone could park outside, I suppose, and hack into my WLAN, but our Neighbourhood Watch ladies would be rustling their curtains and ringing the police. :)

---

