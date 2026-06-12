---
title: "Authentication Required"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by 2madmax on 2008-03-21
I am trying to set up a Ubuntu file server for the lack of a better word.
My Windows Vista Home Premium sees and can access the Ubuntu box just fine,
but my Ubuntu Box CAN NOT access my Windows Box. It can see it, but that is it.

When I try to access it, Ubuntu askes for my user name and password which I set up in samba,
Domain is WORKGROUP but no matter what I do, it will not access the Windows Box.

The Dialog box I get says"Authentication Required"

I have installed and reinstalled three times, and I still can not get it work right.
Please HELP!

Thank You!
Dave:)

---

### Post by Eiríkr on 2008-03-21
The username and password you need to use to access your Windows box are the username and password you use to log in to your Windows box.  **Not** your Samba username and password.

Cheers,

Eiríkr

---

### Post by 2madmax on 2008-03-24
What if they are the same, and I am still having the same problem?
Does my SAMBA user name and password need to be different from my Windows
user name and password?

As I have said, I have tried everything I know about.

Also, why don't I have to "login" from my windows box to access my Ubuntu box
but I have to login from my ubuntu box to access my windows box anyway?

I know I am new at this and there is much I don't know about, but I still need help with
this one.

Thanks again
Dave

---

### Post by Eiríkr on 2008-03-25
If you've set up your Samba username and password to match your Ubuntu login username and password and your Windows login username and password, then that's fine, no problems with that aspect.  Your Samba username and password can be anything you want.  It's just important to understand that what you configure in Samba has *zero* bearing on what you need when trying to access your Windows box.  

When accessing a share from within Windows, the OS saves your authentication (username and password) and automatically enters it forever afterwards.  This is convenient on the one hand, but also potentially a security problem, and can be a problem if the Samba authentication ever changes -- Windows is too stupid to tell the user that the login doesn't work and then ask for a new one, it just fails.  Anyway, Windows has saved your authentication info, so that's why you don't see the prompt anymore when you try to access your Ubuntu box from Windows.  

On the Windows side, are you sure you've enabled sharing?  In XP, you can share a folder by right-clicking it, selecting Sharing and Security, and then clicking the "Share this folder" radio button.  Don't forget to also click the Permissions button so you can see what usernames can access the share, and what permissions they have ("read", "change" which is Windowsese for "write", and "full control" which I think includes deletion).  If you haven't set up any shares, there's nothing on your Windows machine to access, which might be why your connection attempts are failing out.  

HTH,

Eiríkr

---

