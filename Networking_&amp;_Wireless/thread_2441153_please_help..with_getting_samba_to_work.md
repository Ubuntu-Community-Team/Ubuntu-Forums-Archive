---
title: "please help..with getting samba to work"
date: 2020-04-20
forum: Networking &amp; Wireless
---

### Post by kgrind1-sd on 2020-04-20
I have been having the worst time trying to get samba to work for file sharing from my window env to ubuntu. If anyone can help walk me through it that would be great. Thank you

---

### Post by TheFu on 2020-04-20
Common question in these forums: 

[https://ubuntuforums.org/showthread.php?t=2434383](https://ubuntuforums.org/showthread.php?t=2434383)  Windows connects to Ubuntu.

[https://ubuntuforums.org/showthread.php?t=2435292&p=13925468#post13925468](https://ubuntuforums.org/showthread.php?t=2435292&p=13925468#post13925468) Ubuntu connects to Windows.

These both assume Win10 and a recent, supported Ubuntu. Answers are different if different versions are being used.

---

### Post by kgrind1-sd on 2020-04-21
I realized my problem is i cannot edit the smb.conf file. It either shows up blank after typing 

"sudo nano /ect/samba/smb.conf"
or
"sudo vi /ect/samba/samba.conf"
or any of the other means of opening the open the file through the terminal.

When i navigate to the file through the desktop i find that the file is read only.

How can i fix this?

---

### Post by QIII on 2020-04-22
That should be "etc".  In the early Unix days it was literally "et cetera" -- the place where things got put when nobody could agree to where to put them.  Now you might think of it as "everything to configure".

Are you sure you want to modify smb.conf?  What did you "realize" you needed to modify?

---

### Post by kgrind1-sd on 2020-04-22
I'm setting up retropie on ubuntu 18.04. But I have been running into problems with setting up file sharing from my window 10 machine to my Ubuntu machine via samba. Probably just minor user errors like ect vs etc

---

### Post by TheFu on 2020-04-22
> **kgrind1-sd said:**
> I'm setting up retropie on ubuntu 18.04. But I have been running into problems with setting up file sharing from my window 10 machine to my Ubuntu machine via samba. Probably just minor user errors like ect vs etc

Ok.  Brand new.  Got it.  #1 - please learn to use "tab completion" or you will hate Unix.  Find a video on youtube.  Tab completion means never having the wrong file, the wrong option for most commands and it stops us from actually having to type so much.

For example, if I wanted to edit the smb.conf file (assuming I was using samba here), then the actual keys I'd touch are ....
```
sud{tab}e{tab} /e{tab}/sam{tab}/s{tab} {enter}
```

which results in **sudoedit /etc/samba/smb.conf**

Why sudoedit?  Because it is safer than other options and lets you choose which editor you'd like to use. Just set the EDITOR environment variable to any editor you prefer.  If you don't have any experience with vi or vim, probably best to avoid that for now.  Learning vi/vim takes real effort. It is an editor unlike any other you've likely seen.  OTOH, it is the editor that is available on pretty much every OS made. I've never seen nano on a router, but I have seen vi on them.  vim is my "go to" editor almost always.  If you plan to do much raspberry pi stuff, you'll want to learn vim enough to get around. If you plan to be a Unix programmer, then you'll want to learn vim because it is the most powerful and efficient editors made.

BTW, using sudo with GUI programs is usually dangerous. Best not to do that until you full understand file and directory permissions. It is possible with Ubuntu to use a GUI editor w/ sudo and never be able to log into an account again, for example. Recently saw something about Canonical changing the default behavior for sudo to prevent that, but don't know if that is true or just a rumor. We can hope 20.04 does something about it, but since 2006, they haven't.

Also, if you don't have samba installed already, the /etc/samba/ directory won't exist.  Don't be surprised in the future when certain instructions, unrelated to samba, suggest to edit a file that you don't have on the system.  Sometimes, administrators need to create the file they need, so you'll want to be very certain that dyslexia doesn't have you going after the wrong name.  I have dyslexia and sometimes get letters reversed.  Usually I'll check inputs going backwards after I think they are perfect going forwards.  Whatever works for you.

Everyone knows this, but computers do what we tell them to do, not what we wish for them to do. It needs to be exactly correct. Unix assumes you are brilliant and does what you tell it, even when it is completely wrong or dumb.  It is very possible to tell a Unix system to wipe itself and it will. Often it won't ask for confirmation because it assumes you know what you are doing.

Anyways, is samba working?

---

### Post by kgrind1-sd on 2020-04-22
thank you

---

### Post by kgrind1-sd on 2020-04-22
Sooo...
Samba is installed 
smb.conf has been edited to include

"
[Retropie]
 comment = retropie files
 path = /Home/RetroPie
 read only = no
 writable = yes
 browseable = yes
 force user = nobody
 force group = no group
"
via leafpad

When I to access the folder from win10 (\\retropie-ub.local)=(\\hostname.local). My folder RetroPie does show up, but upon trying to access to it I get a network error. 
" Windows cannot access \\retropie-ub.local\Retropie
Check the spelling of the name. Otherwise, there might be a problem with your network."

---

### Post by TheFu on 2020-04-22
/Home/RetroPie looks incorrect.  probably want:  "/home/retropie", though I wouldn't share a directory that's in a HOME like that.  I'd use the [homes] special Samba section which allows connections to any userids HOME directory.  On Unix systems, "HOME" is a special place for each user.

BTW, Unix is case sensitive for all files and directories.  Actually, only MS-Windows and PC/MS-DOS are NOT case-sensitive.

"no group" probably shouldn't have any space. Or just delete that line.  I don't allow unauthenticated samba connections. By using "force user = nobody", you are trying to NOT allow any user access to the /home/retropie except using the Unix username "nobody", which may prevent all access. The file and directory permissions on the raspberry pi would determine what access nobody has. I wouldn't be surprised if access is blocked, but IDK. Don't have a retropi here so I cannot check the permissions.

I don't have Win10, so there could be other issues.

---

### Post by kgrind1-sd on 2020-04-22
I changed: 
/Home/RetroPie to /home/retropie

Removed:
force user = nobody
 force group = no group

added:
guest ok = yes

Not worried about using [homes] as there is and will only be one user anyways.
Its working. it doesn't take me straight to the folder i want to work with, but navigating there is only a click away so its fine. 

Thank you very much

---

### Post by TheFu on 2020-04-22
Change the /home/retropie to the directory you want.  Watch the case.
Restart the samba daemon.

Help the rest of the community by marking this thread as SOLVED - "Thread Tools" button top-right.  People helping won't waste their time and people looking for answers will find it faster.

---

