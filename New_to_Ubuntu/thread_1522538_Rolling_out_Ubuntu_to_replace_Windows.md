---
title: "Rolling out Ubuntu to replace Windows"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by fatladiespart2 on 2010-07-02
Hi 

I'm a bit of a newbie with Ubuntu so still on a leaning curve.  I've been tasked to rollout Ubuntu to replace our Windows boxes but am having a few difficulties.  Any help provided would be greatly appreciated ;-)

1. I've created 1 Ubuntu box which I will be cloning (to all the same spec PC's).  I have setup an admin account and installed programs that we are using at the moment.  The problem I have is that when I setup a new user (i.e. the person who's going to use the PC), the programs are not shared.  If you setup a new user on windows it shares all the installed programs.  I am having to re-install the programs on the new user.  Not a problem if you was only doing a couple of machines, 15 is a different story. Any advise?

2. I have an ATI dual screen card which is running on an ATI driver.  Problem is that when you restart the PC, it hangs.  If you set screensaver to some 3D one's, the PC doesn't come up with the login window. Do I use an open source driver instead of the ATI driver? 

Thanks in advance

---

### Post by alphacrucis2 on 2010-07-02
> **fatladiespart2 said:**
> Hi 

I'm a bit of a newbie with Ubuntu so still on a leaning curve.  I've been tasked to rollout Ubuntu to replace our Windows boxes but am having a few difficulties.  Any help provided would be greatly appreciated ;-)

1. I've created 1 Ubuntu box which I will be cloning (to all the same spec PC's).  I have setup an admin account and installed programs that we are using at the moment.  The problem I have is that when I setup a new user (i.e. the person who's going to use the PC), the programs are not shared.  If you setup a new user on windows it shares all the installed programs.  I am having to re-install the programs on the new user.  Not a problem if you was only doing a couple of machines, 15 is a different story. Any advise?

2. I have an ATI dual screen card which is running on an ATI driver.  Problem is that when you restart the PC, it hangs.  If you set screensaver to some 3D one's, the PC doesn't come up with the login window. Do I use an open source driver instead of the ATI driver? 

Thanks in advance

Maybe [Clonezilla]("http://clonezilla.org/") would help.

---

### Post by warfacegod on 2010-07-02
Issue .01 For the new user, Right click the Apps./Places/System (aka Menu bar)> select Edit Menus> look in there for the installed apps. They're probably just not checked for the new user.

Also, be certain you know what kind of user account would be appropriate for the people that will using these computers. Administrator, Desktop user, etc. I assume they are employees?

---

### Post by warfacegod on 2010-07-02
Issue .02 The ATi drivers still leave much to be desired. Using the "Recommended" driver in Hardware Drivers is almost certainly your best bet.

---

### Post by fatladiespart2 on 2010-07-02
> **alphacrucis2 said:**
> Maybe [Clonezilla]("http://clonezilla.org/") would help.

Thats what I'm using to clone the drives once I have it all setup.  I'm making sure it all works before cloning.  

Thanks

---

### Post by fatladiespart2 on 2010-07-02
> **warfacegod said:**
> Issue .01 For the new user, Right click the Apps./Places/System (aka Menu bar)> select Edit Menus> look in there for the installed apps. They're probably just not checked for the new user.

Also, be certain you know what kind of user account would be appropriate for the people that will using these computers. Administrator, Desktop user, etc. I assume they are employees?

Thanks for the advise, The icons are there, just not working.  For example, I have installed VitualBox and loaded Windows 7 on it.  When I create the new user (admin user) the VirtualBox is there but no Windows 7 on it.  Anther example is that we use Citrix client to log into our mail, again unable to open mail without having to re-install Citrix on the new user.  Some programs do work like Adobe Reader, Putty, FileZilla etc.  Not sure if it's something to do with where the programs are installed.

---

### Post by Mark Phelps on 2010-07-02
> **fatladiespart2 said:**
> Hi 

I'm a bit of a newbie with Ubuntu so still on a leaning curve.  I've been tasked to rollout Ubuntu to replace our Windows boxes but am having a few difficulties.  Any help provided would be greatly appreciated ;-)

Please don't take this as a personal criticism -- but this is going to be a nightmare for you!!

Being a Systems Admin for a collection of Linux boxes is no easier than being a Systems Admin for a collection of Wintel boxes -- and with Virtualization + Win7 + Citrix, that makes the job a lot harder.

I'm guessing that this is a company "management" decision, right?

Best thing for you and your company would be to hire on a seasoned Linux Administrator person for a few weeks -- to get the machine installed, setup, configured, and to get the Win7/Virtualization + Citrix stuff working.

Again, I'm not criticizing you personally, but unless you get some "professional help" here, you're going to be spending ALL your time on this forum for the next several weeks -- and most probably catching all kinds of grief when one thing after another doesn't work.

---

### Post by zer010 on 2010-07-02
Would  using Remastersys help? Making a Livecd of what has been installed on the 1st computer. It might not work with VB or Citrix, but thought I'd throw it out there just in case. :)

---

### Post by JKyleOKC on 2010-07-02
> **fatladiespart2 said:**
> For example, I have installed VitualBox and loaded Windows 7 on it.  When I create the new user (admin user) the VirtualBox is there but no Windows 7 on it.While I find VirtualBox to be the best virtualization program I've used, it does have one "feature" that is probably what's causing you this problem: all of its virtual machines and drives are (by default) stored in the /home/user directory of the user who created them! Thus they are private to that user and no other user can use them.

It's possible to copy them over to another user's home directory; they are in the hidden directory .VirtualBox (note the capitalization). This eliminates the need to re-install, but there's still a problem that the virtual machines' drives cannot be shared with other users. Simply moving them to some system-wide directory doesn't really help, since only one instance at a time of VirtualBox is allowed access to each virtual drive. The second and subsequent attempts to open a "shared" machine or drive fails.

Virtualization on a server can solve the sharing problem, but it's not as simple as using VBox. As Mark Phelps noted, you have a difficult few weeks (if not months) ahead unless you get professional help to set things up...

---

### Post by l-x-l on 2010-07-02
> **JKyleOKC said:**
> While I find VirtualBox to be the best virtualization program I've used, it does have one "feature" that is probably what's causing you this problem: all of its virtual machines and drives are (by default) stored in the /home/user directory of the user who created them! Thus they are private to that user and no other user can use them.

It's possible to copy them over to another user's home directory; they are in the hidden directory .VirtualBox (note the capitalization). This eliminates the need to re-install, but there's still a problem that the virtual machines' drives cannot be shared with other users. Simply moving them to some system-wide directory doesn't really help, since only one instance at a time of VirtualBox is allowed access to each virtual drive. The second and subsequent attempts to open a "shared" machine or drive fails.

Virtualization on a server can solve the sharing problem, but it's not as simple as using VBox. As Mark Phelps noted, you have a difficult few weeks (if not months) ahead unless you get professional help to set things up...

I got around the problem by creating a folder in / strictly for storing the .vdi's. Then secured it using chown & chmod. So now me & the wife could both load virtual XP.

---

