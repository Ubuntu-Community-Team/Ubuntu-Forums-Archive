---
title: "Allow samba access by default"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by rkakkar on 2009-12-22
Hi,

I want all users on my lan to have access to my shared folders via samba without any form of authentication. How can I do this in KDE? I have tried some settings (see screenshot - allow all unspecified users), but it still tell the windows machines that they don't have access when they try to access my machine through the ip address. Any ideas?

---

### Post by HereInOz on 2009-12-22
I am assuming that you have installed all the necessary samba software.  

After that, the first thing you need to check is that the firewall is either disabled, or it is set to allow port 135 - 139 and port 445 inbound from your network.  These are the Samba ports.

Not sure if this works in KDE< but if you can, install system-config-samba, and that will give you a gui to set up the samba shares.  The thing in the screen shot may well do the same thing.  This utility allows you to set the access restrictions to "everyone" and that ought to do the job.

See how you go.  Remember, you need to make sure that you set the share as Writeable, Visible, and accessible to Everyone.

---

### Post by rkakkar on 2009-12-22
> **HereInOz said:**
> I am assuming that you have installed all the necessary samba software.  

After that, the first thing you need to check is that the firewall is either disabled, or it is set to allow port 135 - 139 and port 445 inbound from your network.  These are the Samba ports.

Not sure if this works in KDE< but if you can, install system-config-samba, and that will give you a gui to set up the samba shares.  The thing in the screen shot may well do the same thing.  This utility allows you to set the access restrictions to "everyone" and that ought to do the job.

See how you go.  Remember, you need to make sure that you set the share as Writeable, Visible, and accessible to Everyone.



god! there are so many settings here .. i can't figure out which one to set! i wish it was like gnome's samba sharing wherein i just had to check 'allow guest access' and my work was done :(

---

### Post by rkakkar on 2009-12-22
a big -ve for KDE's usability :(

---

### Post by Roasted on 2009-12-29
Why not just create an actual user that everybody shares, allow that user to have valid access to your samba share, and when you log in from the windows computers, check save password.

I have -never- had good luck with the samba guest user account, both on gnome and kde (gnome user for 5 years, kde user for 2 months). It just never worked for me. Instead, I created actual users (much more secure) but I also wanted my "guest" access who has limited usability over the shares - so I added a generic "user" account that I treat as my guest account - similar to work on our domain where we have 1 generic account the tech dept uses for testing, etc.

What program is that in your screen shot??

---

### Post by rkakkar on 2009-12-31
> **Roasted said:**
> Why not just create an actual user that everybody shares, allow that user to have valid access to your samba share, and when you log in from the windows computers, check save password.

I have -never- had good luck with the samba guest user account, both on gnome and kde (gnome user for 5 years, kde user for 2 months). It just never worked for me. Instead, I created actual users (much more secure) but I also wanted my "guest" access who has limited usability over the shares - so I added a generic "user" account that I treat as my guest account - similar to work on our domain where we have 1 generic account the tech dept uses for testing, etc.

What program is that in your screen shot??


how do i create this user??

the program is system-config-samba i think...

---

### Post by Roasted on 2010-01-01
> **rkakkar said:**
> how do i create this user??

the program is system-config-samba i think...

In system-config-samba

Preferences - Users - Add User. The user you add must already exist on the Linux system itself.

Or via terminal:

sudo smbpasswd -a *name-of-user*

---

### Post by rkakkar on 2010-01-04
> **Roasted said:**
> In system-config-samba

Preferences - Users - Add User. The user you add must already exist on the Linux system itself.

Or via terminal:

sudo smbpasswd -a *name-of-user*

that's the thing .. i want people to access without a user account.. its possible within gnome .. was wondering how to do the same in kubuntu

---

### Post by Roasted on 2010-01-04
> **rkakkar said:**
> that's the thing .. i want people to access without a user account.. its possible within gnome .. was wondering how to do the same in kubuntu

You must have had some sort of setting in Gnome to allow that.

I say that because I've used Gnome and Samba for about 5 years, and I've never had that working. I'm also currently running Kubuntu and Samba, and also don't have it working like that.

I always -always- found it easier to just create a generic user. 

Example

User
Passwd

That's my generic user.

---

