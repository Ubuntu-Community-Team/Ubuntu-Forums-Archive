---
title: "Samba WAS working"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by jcfuller on 2007-06-18
I had samba working on an Ubuntu Feisty 64 bit box along with 2 other Ubuntu 32 bit's and Debian 32 on a fourth.

Power failure and now I can't access the 64bit box from the W2k machine( or any other Windows machines). No problem from the other Linux Machines. I made some changes to get a program running and I must have screwed up something

The Name that shows up on the Windows Machines is:

JAMESC2D-DESKTOPjamesc2d-desktop server (Samba, Ubuntu)

Seems the description and the name have somehow been concatanated??

James

---

### Post by scrooge_74 on 2007-06-18
Check in the smb.conf file the detail for naming the machine.  Did you try reseting samba server or restarting that PC?

---

### Post by jcfuller on 2007-06-18
> **scrooge_74 said:**
> Check in the smb.conf file the detail for naming the machine.  Did you try reseting samba server or restarting that PC?

I dont see anything in the smb.conf files about names just the server string = %h server (Samba, Ubuntu)

I shut down all machines and the router.

James

---

### Post by p_quarles on 2007-06-18
I think that in order for Samba to show up on a Windows machine you have to have the "workgroup" value set. Look for that in smb.conf. My wild guess is that you can fix the server/username mixup there. 

That said, I got Samba working about two weeks ago, so I'm far from an expert.

---

### Post by jcfuller on 2007-06-19
> **p_quarles said:**
> I think that in order for Samba to show up on a Windows machine you have to have the "workgroup" value set. Look for that in smb.conf. My wild guess is that you can fix the server/username mixup there. 

That said, I got Samba working about two weeks ago, so I'm far from an expert.

It does show up but I get an error message when trying to access it. It appears the name is incorrect but I don't know how to correct it on the Ubuntu side.

James

---

### Post by p_quarles on 2007-06-19
> **jcfuller said:**
> It does show up but I get an error message when trying to access it. It appears the name is incorrect but I don't know how to correct it on the Ubuntu side.

James
Well, like I said, I'm far from being a fount of wisdom on Samba, but if you want to post your smb.conf text here I'll take a look and see if I can help.

---

### Post by jcfuller on 2007-06-19
Found it and am not sure why it was working before.

I did not have a netbios name in my smb.conf file. I thought this was for wins only?

Stopped samba added a netbios name before the server string and restarted samba and all is well
must be what the %h is in the server string???

James

---

### Post by p_quarles on 2007-06-19
I think the netbios ID is how Linux identifies the server, so without one it might have had trouble identifying itself. Still, not sure why you could mount from Linux but not from Windows. 

Glad you got it working.

---

### Post by nashjc on 2007-06-21
I noticed a slightly different problem with Feisty -- may even be a bug -- in that I wanted to have user level access to my home directory on a "server" (actually a home based machine) from the equivalent on my laptop when I plug into my local network at home. I thought I would (possibly foolishly) try to use NFS since my Samba is set up as SHARE. Went to the Admin Functions / Shared Folders  on the "server" and added an NFS share for /home/me. 

Then no Samba!

When I looked in /etc/samba, the smb.conf had been changed to just a moment before. And the parameters for browseable etc. had been changed from yes to no. 

Nasty nasty nasty. And no warning. Getting too much like M$ Windoze for my tastes. I suspect a bug, but am not a networking type.

JN

---

### Post by p_quarles on 2007-06-21
I'm not the networking type either (just barely setup my first ever, and expect to be working the bugs out for some time), but: I think Samba and NFS are incompatible. I mean, I think an advanced user (not me) could probably get them working together, but the short term solution is to use Samba alone. 

In any case, machines running Linux are completely capable of accessing SMB shares, so you don't really need an NFS share.

---

