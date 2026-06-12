---
title: "Need HELP on sharing b/t Ubuntu and XP"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by prismhdd on 2008-03-04
I'm a new ubuntu user and need a help in networking b/t Ubuntu and XP.

I have 1 Desktop with Ubuntu 7.10 (Gutsy), and 3 other PCs with XP. I installed samba and was successful with sharing Ubuntu folders FROM XPs. However, for some reasons, I can't connect TO XPs FROM Ubuntu even though all the XP computers are shown in Places>Network panel. When I double-click a computer, it says "The Folder Contents Could Not Be Displayed"

I did network settings and shared folders....
I tried to turn off firewalls on XPs but it didn't work as well. (same message)
I set up the smb.conf file and smbpasswd as posted.

followings are my smb.conf changes from original conf file :

workgroup = myworkgroup
sercurity = user
browseable = yes
writable = yes

I spent all day searching for this answer but couldn't find it...:confused:
I hope you guys can tell me what I am missing.

Thank you in advance.:)

---

### Post by Eiríkr on 2008-03-05
In Nautilus (your file browser in Ubuntu), click Go -> Network.  You should see something called Windows Network.  Double-click this and you should see the name of your workgroup.  Double-click this and you should see your XP boxes.  

Now, when you try to open one of the XP shares, do you get any sort of login dialog?  If so, be sure to enter *NOT* the username and password you used for the smbpasswd command, but rather the same username and password you'd use when logging in to that XP machine.  If you've set up your XP user account to have no password, you're going to need to change some permission settings on the shares from within Windows (c.f. [post=4454301]this post[/post] and others in the thread).  

HTH,

Eiríkr

---

### Post by prismhdd on 2008-03-05
I don't get any login page when I double-click XP boxes....that's the where message "The folder contents could not be displayed" pops up.

---

### Post by Eiríkr on 2008-03-05
Is there any chance your Windows "Guest" account has been disabled?  Looking closely at the Computer Management -> System Tools -> Shared Folders -> Sessions display, I note that my Xubuntu box apparently negotiates a Guest connection to my Windows box in order to display the list of shares available.  If this "Guest" account is disabled, it appears that GUI-based share display won't work (though [font=courier]smbclient -L WINBOX_NAME[/font] still works).  

Cheers,

Eiríkr

---

### Post by prismhdd on 2008-03-05
I get it!!! when I tried to mount WIN BOX using smbclient, it says NT_STATUS_ACCESS_DENIED...

I tried to connect to XP box which doesn't have any password, and it worked
but when I try to connect the XP with password I can't, and it doesn't even ask me a userid or password for XP box....

Can anyone help me on this??

---

### Post by Eiríkr on 2008-03-06
> **prismhdd said:**
> I get it!!! when I tried to mount WIN BOX using smbclient, it says NT_STATUS_ACCESS_DENIED...

... sounds like we might be getting somewhere.  :)

> **prismhdd said:**
> I tried to connect to XP box which doesn't have any password, and it worked

How did you try to connect?  Via smbclient, or via Nautilus?  What, exactly, did you do to connect?  Where there any messages or dialogs that appeared, and what did they say?  I'm vastly interested in this due to a recent thread where the poster simply *couldn't* log into an XP share where the username has no password.  Try as I might, I couldn't get it to work either.  

> **prismhdd said:**
> but when I try to connect the XP with password I can't, and it doesn't even ask me a userid or password for XP box....

If I understand you correctly, there are two XP boxes described above, XP1 has a username *without* a password, and XP2 has a username *with* a password.  Both XP1 and XP2 are sharing folders.  Is this correct?  Can you access the XP1 share from XP2, and XP2 from XP1?  Do you get any login prompts then?  Are all the usernames on XP1, 2, 3, and Ubuntu the same, or different?  If you're the only user in this setup, it's easiest if all usernames are the same on all systems.  

Here's a suggestion for the failed Ubuntu -> XP2 connection.  Within Windows on XP2, open Explorer, find the folder being shared, right-click it, select Properties, select the Sharing tab, click the Permissions button, select the username you tried to connect with, and see what permissions that user has to the share.  Make sure the user has at least "read" permissions, then try to connect again.   Let us know what you find.

Cheers,

Eiríkr

---

