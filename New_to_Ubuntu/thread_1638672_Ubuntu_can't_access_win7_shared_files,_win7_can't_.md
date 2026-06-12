---
title: "Ubuntu can't access win7 shared files, win7 can't see ubuntu shared files"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by ntrgc89 on 2010-12-05
I've been banging my head on this problem for the past few hours and the only head way I could make was getting Ubuntu to see "Workgroup," but then being unable to access it (failed to retrieve share list from server)

I have samba installed, and I've attached the smb.conf file.

I've checked the firewall, it's off.

Typing the ip address of the win7 machine from ubuntu gives me a login prompt that never accepts the password I give it.

And typing findsmb returns the following

```

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.0.104   LINUX         +[	WORKGROUP     ]

```

Which puzzles me, since it should return UBUNTU for netbois name since that's how the smb.conf is set-up, right?

Are there any ports I need to open on my router or something??? What do I have to do to get win7 to see (and be able to write to) the files on Ubuntu?? I don't care so much about the other way around, but I figure it might be useful for diagnostic purposes to set that up anyway.

Any help is greaty appreciated!!

---

### Post by HermanAB on 2010-12-06
Howdy,

The only way to debug SMB problems is with the command line program smbclient.  

See this:
[http://www.aeronetworks.ca/howtos/samba-debug-howto.html](http://www.aeronetworks.ca/howtos/samba-debug-howto.html)

---

### Post by ntrgc89 on 2010-12-06
Thanks for replying,  but I'm still not getting it. What's all this talk about users and permissions and belonging to groups? What groups am I in? What groups is windows in, if that question makes any sense? What groups do I need to be in???

Please help!

---

### Post by ntrgc89 on 2010-12-07
Bump

---

### Post by ntrgc89 on 2010-12-07
So I reinstalled windows (might seem a bit drastic but it's something I've been meaning to do for a while).

It now sees the LINUX computer (not sure why though, it should be called UBUNTU), but no matter what combination of username/password I give it it won't let me on. Is it a domain issue? Which domain should I be on?

Thanks!

---

### Post by gordintoronto on 2010-12-07
When you set up the share in Ubuntu, did you check "guest access" and "allow others to create and delete files..."?

You can go back and do it now.

---

### Post by TroN-0074 on 2010-12-07
This is what I do, I use ubuntu with gnome as desktop manager. Select a folder you want to share right click and go to its properties, select the share tab and tick share this foldel, then tick the other two little boxes where it say to allow other to create and delet files, and also where it says to allow guest accest to it.
you can now have access to that folder from the other computer clicking the network icon. If you want to access your windows computer's files select what folders you want to share and change the permissions needed. 
As I said I use gnome and I have no idea on how to do it under KDE or whatever else is out there. Good luck to you.

---

### Post by ntrgc89 on 2010-12-07
The "guest access" checkbox is grey, but I believe I added those options to the smb.conf file.

I think the domain is the issue. What domain should the login to the linux machine be?

---

### Post by ntrgc89 on 2010-12-07
Wow, I finally got it to work! For a second I couldn't even see the linux machine, but I restarted samba and saw it again. Then I went to System > Administration > Samba, then went to Preferences > Server Settings, then over to the security tab, and changed the authentication mode from 'user' to 'share'. Then I went back to the windows machine, double-clicked on the "linux" icon in network, and it showed me the shared files without any user/pass prompt.

I still can't connect to windows from ubuntu (I get the same "failed to retrieve share list from server"), but this wasn't my ultimate goal so I'm not too upset :)

Hopefully this story helps someone else in need!

---

### Post by gordintoronto on 2010-12-08
Interesting. I'm using Ubuntu 10.10, and there is no System/Administration/Samba menu entry. I have a share which works nicely, access shares on other machines, and use a network printer.

---

### Post by Jerry N on 2010-12-08
> **ntrgc89 said:**
> 
I still can't connect to windows from ubuntu (I get the same "failed to retrieve share list from server"), but this wasn't my ultimate goal so I'm not too upset :)

I have had that same message on a couple of Ubuntu 10.04 installs so I tried replacing Ubuntu 10.04 with LinuxMint 9 (same as Ubu 10.04, right?) and it found the Windows shares right away.  

Jerry

---

