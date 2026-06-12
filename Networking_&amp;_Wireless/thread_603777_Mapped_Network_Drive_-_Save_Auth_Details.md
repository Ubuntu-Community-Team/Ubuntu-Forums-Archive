---
title: "Mapped Network Drive - Save Auth Details?"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by Nightwalker07 on 2007-11-05
I have a Ubuntu 7.04 system (running as my MythTV media-center). I connect to the media folder (/var/lib/mythtv) from my windows system, I setup a samba share and made it a Mapped Network Drive on the XP system. All works well and permissisons are fine.

But my problem is... my XP system might remember the username & password details to connect to the share for a few hours maybe, sometimes less, im not sure what the period is, but its as if it looses it's authentication information and when I click on the mapped network drive it asks me to enter in my password again to access the share. I would like to stop it doing this. There is no usual 'Save Password' tick box on the auth window, but when I made the Mapped Network Drive originally I told it to access the drive using specific auth details and told it to remember them, like I say it works fine for a good while but then asks me for the password later on.

The reason this is a concern for me is because I've got synchronization software setup on my XP system that automatically sync's media from my XP system to my media center.

Thanks for your time and help.

---

### Post by Nightwalker07 on 2007-12-13
Anyone? I could really do with fixing this problem.

---

### Post by ctyc on 2007-12-13
I have the same issue on some of the windows boxen on my network and I still have no resolution.
I have concluded that windows just sucks since linux boxen on the same lan are able to use /etc/fstab to connect/save credentials just fine.

---

### Post by Nightwalker07 on 2007-12-13
Oh right? Thats strange, I was thinking it wasnt an issue with Windows, I thought it might have been with Linux, because I told windows to remember the credentials I gave it and from my experience I thought it was pretty good at doing that, I thought it was perhaps the Linux box that was forcing a re-check of the auth details after a certain period of time. Maybe not, anyone know?

---

### Post by jetsam on 2007-12-13
This is how I have samba set up to be transparent to the XP users that access it with user level security:

In the globals section of my smb.conf:
```
username map = /etc/samba/smbusers
null passwords = Yes
```

Then I have a file /etc/samba/smbusers:
```
#Unix_name = "Windows name with spaces"
bob = "Bob User"
sam = "Sam User"
```

Then you need to make sure that user bob and user sam have been set up right on the server:
```
sudo adduser bob
sudo smbpasswd -a bob
```

You only need the username map if you have Windows usernames with spaces in them.  You only need "null passwords = Yes" if your Windows users use blank passwords when they log on.  The password in the smbpasswd step should be the same as the windows password, and can be blank.  If you make these changes, you'll need to restart samba after you make them.  

I think what happens is that Windows first tries it's own username/password when it logs into a samba share.  Only if that doesn't work does it then ask for login credentials.

I think a setup like that will work in your situation.  I'm not sure why Windows is losing its saved login credentials; there may be an easier way to address the issue more directly.

---

### Post by HwyXingFrog on 2008-01-16
Thanks a bunch jetsam.

Your solution worked for me and your explanation for why makes sense.  This problem was really bugging me for a while ](*,)

I just had to add the null passwords line and add a user to my ubuntu smb server and it works awesome now.

No more does my brother need to ask me to type in the password every time he logs in.

---

