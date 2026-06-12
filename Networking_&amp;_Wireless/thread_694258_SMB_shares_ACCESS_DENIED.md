---
title: "SMB shares ACCESS DENIED?"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by Scott8855 on 2008-02-11
I'm trying to access a share on my windows machine from gutsy.  I am able to connect to the share either from the network browser or smbclient, but it says access denied when it try to open a folder.  In smbclient I put in the username and password for the admin account and still get the error, in the network browser I have no way to authenticate. 

What am I doing wrong here?  For security reasons I want to have to put in the admin username and password to access the windows shares.  As it sits now I can mount the share, but not access all the folders just some.  

Thanks, Scott

---

### Post by linuxisfree on 2008-02-12
> **Scott8855 said:**
> I'm trying to access a share on my windows machine from gutsy. I am able to connect to the share either from the network browser or smbclient, but it says access denied when it try to open a folder. In smbclient I put in the username and password for the admin account and still get the error, in the network browser I have no way to authenticate. 
 
What am I doing wrong here? For security reasons I want to have to put in the admin username and password to access the windows shares. As it sits now I can mount the share, but not access all the folders just some. 
 
Thanks, Scott
 
Hey Scott, I think this might help: [_[COLOR=#bd5900]http://ubuntuforums.org/showthread.p...=samba+windows[/COLOR]_]("http://ubuntuforums.org/showthread.p...=samba+windows")
 
(I HOPE!)

---

### Post by swerdna on 2008-02-12
A few thoughts:

Check the share is set to allow network users to access and modify
Check the workgroup name is same on both machines
You authenticate from Linux usually with the username and password of the owner of the folder in windows
Turn off third party firewalls on windows and try again, sometimes will inhibit

Swerdna

---

### Post by Scott8855 on 2008-02-12
Sorry the link didn't go to any threads, I have searched but was not able to find this exact problem.  I'm even able to access the shares without using a user name or password, but with the same results, I can not access all the folders.

I am on the same workgroup
I have disabled any firewalls
I tried authenticating with the admin on the windows box

I tried this from another windows box rather then gutsy, and get the same results, I can access the share with no password or user, but can not open all folders, so its not a gutsy thing, im a bit confused, guess i need to go back over some basics again.

---

### Post by swerdna on 2008-02-12
> **Scott8855 said:**
> Sorry the link didn't go to any threads, I have searched but was not able to find this exact problem.  I'm even able to access the shares without using a user name or password, but with the same results, I can not access all the folders.

I am on the same workgroup
I have disabled any firewalls
I tried authenticating with the admin on the windows box

I tried this from another windows box rather then gutsy, and get the same results, I can access the share with no password or user, but can not open all folders, so its not a gutsy thing, im a bit confused, guess i need to go back over some basics again.
Look carefully in windows at the permissions on the folders that you cannot access

---

### Post by Scott8855 on 2008-02-12
> **swerdna said:**
> Look carefully in windows at the permissions on the folders that you cannot access

Well, I'm sharing the whole C drive, I disabled the default shares e.g. C$ ADMIN$ ect.  If i shared the entire C drive I would expect to be able to access everything.  Also I would expect to be asked for a username and password but I am not.

Scott

---

### Post by BLTicklemonster on 2008-02-12
Try the link in my sig, see if it helps any?

---

### Post by arell12 on 2008-02-12
BL, I read your article on the home networking solution and I am sure that it works great, but do you have any information about doing this from a Windows Domain with Domain controllers and authenticating through Active Directory?

---

### Post by BLTicklemonster on 2008-02-12
No, but try searching in google by putting what you want then put 

site:ubuntuforums.org 

behind it.

Like

smb windows domain active directory site:ubuntuforums.org

And see if any of these help you:

[http://www.google.com/search?q=smb+windows+domain+active+directory+site%3Aubuntuforums.org&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=smb+windows+domain+active+directory+site%3Aubuntuforums.org&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)


... maybe.

---

### Post by tom93 on 2008-03-21
> **BLTicklemonster said:**
> Try the link in my sig, see if it helps any?
That worked for me !
I hadn't added and enabled the samba user.

---

### Post by jimv on 2008-03-21
Try this:

In Windoze:

Open any folder
Go to the Tools menu and click Folder Options
Scroll to the bottom of the list
Uncheck "Use Simple File Sharing"
Click Apply and Ok

Set up the share again, then try connecting in from Ubuntu.

And while I'm thinking about it, get Properties on one of the folders that you can't access from the Ubuntu machine and look at the "Security" tab.  Is 'administrator' or 'administrators' listed as having access to that folder?

---

