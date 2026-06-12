---
title: "What is the &quot;best&quot; file sharing method within Ubuntu/Windows networks?"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by Roasted on 2008-12-01
I currently have Samba set up. I was doing some reading on NFS, Samba, etc, and I've read some mixed opinions.

I keep hearing that Samba is hard to set up... which kind of shocks me. I thought Samba was easy to set up. I just had to see a "base model" smb.conf file in order to get an idea of what I had to do. I also read about Samba's speed issues, yet I can push 10 gig from a Vista laptop wirelessly to my Ubuntu machine through Samba with very little effort.

But anyway, due to NFS's raved "easy setup" I'm curious to try it out. I understand that NFS doesn't support Windows platforms, though. I also read that the new NFS (in testing) does.

Can anybody just shed some light here? I'm just trying to tinker around and get an idea of what's best to use here.

---

### Post by dollylamb on 2008-12-01
im using samba. Its good & easy to use, atleast for me. read more here: [http://lists.samba.org/archive/samba/2002-May/044543.html](http://lists.samba.org/archive/samba/2002-May/044543.html)

---

### Post by Roasted on 2008-12-01
The one post on that link says...

```
I think it is very simple. If you use Windows in your network you HAVE
to use Samba. If all the computers in the network understand NFS you
SHOULD NOT use Samba.


```

...why is that, exactly?

---

### Post by Iowan on 2008-12-01
Your Samba experience is... well, better than some.  Samba may not be to blame for some of the problems encountered, but it DOES seem (at least to some of us) to be getting harder to make it work.  I have a Samba server on my network, just because there is a Windows machine that *might* need to use it (but hasn't yet).  I haven't tried NFS, but had an SSHFS "share" set up (for awhile, anyway). You might check [SSHFS]("https://help.ubuntu.com/community/SSHFS") as an alternative.

---

### Post by dollylamb on 2008-12-01
yes, i'd heard that too. I think, because NFS is already implemented on linux/unix system which has the same security system implementation. So that why we don't need another less secure (SAMBA) system. Corrrect me if i'm wrong.

---

### Post by Roasted on 2008-12-01
> **dollylamb said:**
> yes, i'd heard that too. I think, because NFS is already implemented on linux/unix system which has the same security system implementation. So that why we don't need another less secure (SAMBA) system. Corrrect me if i'm wrong.

Yeah, however, if NFS can't handle Windows... what good is it for somebody like me with multiple platforms? 

What I basically need is for XP/Vista computers to have the ability to start - run - \\myubuntucomputer\usershare and be able to write/read/modify documents there... Because I will use "SyncToy" on these Windows computers to enable easy backups of their My Documents folder.

I also need each share to have certain restrictions. Meaning, I don't want Bob to be able to log into Fred's account.

Can SSHFS handle this?

---

### Post by vandorjw on 2008-12-01
Here is my samba experience.

1) Install Ubuntu 8.10 fresh.
2) Plug into the network.
3) Right click on a folder, and click share.
   i) a pop-up comes up, telling me that I need to install two programs to share files, I click ok, let them download and install.
   ii) Files are now shared.


Leaving everything at default, and not messing with anything, samba works great.

on the network at my house, there are 4 Vista comps and 2 win XP's
and 1 Ubuntu. (me)

Everyone can access everyone's shared folders, and initial set up was about 1 hour.

---

### Post by Roasted on 2008-12-01
I edited samba a little bit... I just added 4 instances of shares here.

On my "network drive" for Samba storage, I created 4 directories named accordingly to what user they belonged to. Then I assigned permissions to them.

Then in Samba, I simply added 4 instances of the following and named them accordingly to what user they belong to.
Here is my section.

[jason]
path = /home/jason
writeable = yes
browseable = yes
valid users = jason

I just changed the path and valid user section for what user it belongs to. For the other users, their share is under /media/storage. For me, I keep mine assigned to Home. Why? Because I have more stuff on my desktop (500gb drive) than what my laptop can hold. But I'm often out in the garage and I wanna jam to some tunes. What do I do? I have a mapped network drive to my share. I double click it, open my music folder, and play music FROM my desktop wirelessly out to my laptop in the garage.

Then when you go to start - run on a Windows computer, a login box is displayed. Each user has their own password (assigned by sudo smbpasswd -a 'name') and they log in here and can check "remember password."

I have my smb.conf backed up on a flash drive. When I do a reinstall, it takes all about 2 minutes to get Samba running again. It takes more time to create folders and assign permissions than it does to paste the smb.conf over and reboot Samba. 


But, despite how easy things were for me in Samba, I still had to question whether or not there was an "easier" way... hence my interest in other alternatives.

---

### Post by Roasted on 2008-12-02
Samba looks a whole lot easier now.

I just found this config utility and tested it out. It works great.

[http://ubuntuforums.org/showpost.php?p=5499721&postcount=9](http://ubuntuforums.org/showpost.php?p=5499721&postcount=9)

Check the post. It's explained there a little bit. Good stuff!

EDIT - I gotta admit, this simple gui utility makes things a whole lot easier. I'm setting up a computer for a friend of the family as I type this, and I had all of their old documents on my Ubuntu computer that I am typing from. Well, it would take time to transfer all of her documents from my desktop to my samba share in order for it to be on the network. So what did I do? Opened up the GUI utility, added a new share, and directed it right to /home/jason/Desktop/SueBackup. BAM. All her stuff there. Copy/Paste... done.

I liked Samba before, but something so simple like this is really impressive. I'd like to hear what others have to say about it.

But, I still have to wonder... I haven't had a second Ubuntu machine around to test Samba in between two Ubuntu machines... but how well does Samba work with two Linux machines talking to each other instead of Linux to Windows? I'm installing XP/Intrepid dual boot on a spare computer behind me as I type this, but I won't be back to work on this computer until tomorrow evening... so if somebody could tack on their experience with using Samba between two Linux computers, that'd be great. Thanks all!

---

### Post by Roasted on 2008-12-03
All right, all right...I had my joy of the Samba GUI. Now I'm tempted to try NFS...

I keep reading here that people are saying NFS doesn't work with Windows. Yet I google and I find people who have it working.

I have some blunt questions here.

How can I get NFS working on both my Ubuntu machines and Windows machines?
Does NFS have a gui to configure?
Do speeds in both Windows + Linux environments rival that of Samba?

---

### Post by twiz86 on 2008-12-03
Took me 5 minutes to setup my whole home network with samba. two ubuntu laptops, 1 vista laptop. they all share just fine and the printer is hosted on one of my ubuntu laptops.

sudo apt-get samba

right click on a folder, share. bam yur done.

if you are running a firewall on your comp you need to turn it off or make an exception for your network computers.

Samba sucked until i turned off my firewall hehe.):P

---

### Post by dollylamb on 2008-12-03
Roasted,

I'm pretty sure that you can use NFS on both Unix/Linux & Windows, to do so you need to download a package called: SFU (Services for Unix) from Microsoft site. The download link can be found [here]("http://www.microsoft.com/downloads/details.aspx?FamilyID=896C9688-601B-44F1-81A4-02878FF11778&displaylang=en").

_A GUI tool to manage NFS? try Webmin. I never use webmin to manage NFS but i saw it in webmin's support modules.

---

### Post by Roasted on 2008-12-03
Can somebody post their NFS config file? I'm trying to read how-to guides so I can get familiar with it. And pretty much every how-to guide has told me so little about this thing it's unreal.

I'd like to see a base model of the NFS config file to see what I should be looking at... if possible.

EDIT - and also, I have to wonder... I'm reading that this nfs config file only requires 1 line per share that I use. Okay, fine. But what host name does it use? I don't want this to be IP based. I want my setup to be computer name based. I want to be able to \\ubuntucomputer\user's-share @ start-run and log into that share.

Can the shares be password protected?
Can I keep Bob from getting into Fred's NFS share?

---

