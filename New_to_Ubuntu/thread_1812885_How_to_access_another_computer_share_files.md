---
title: "How to access another computer share files?"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by dixcuxx on 2011-07-26
Within the same network with same router, I have another computer which is running Windows XP professional and I set only specific user can access the file sharing from this computer. Can I somehow type in the user name and password so I can access the files?

For this computer which I just install ubuntu side by side, I have windows xp home, and the only way to access the files in the windows professional computer would be setting up an user account with same user name and password that has access right. Then I can connect and open the files, if I use an user name which professional XP computer doesn't know, then I can just see there are files but I cannot open these files.

---

### Post by dixcuxx on 2011-07-27
May be someone would know about this!?

---

### Post by alphacrucis2 on 2011-07-27
> **dixcuxx said:**
> May be someone would know about this!?

I think Windows may be allowing guest read access. You should  be able to adjust the Windows folder permissions under sharing in Windows Explorer to disable guest access completely.

---

### Post by dixcuxx on 2011-07-27
> **alphacrucis2 said:**
> I think Windows may be allowing guest read access. You should  be able to adjust the Windows folder permissions under sharing in Windows Explorer to disable guest access completely.

I set only specific user can access that folder, I mean using the windows xp way to control which user has the right to access those share folders.

---

### Post by Morbius1 on 2011-07-27
> I have another computer which is running Windows XP professional and I  set only specific user can access the file sharing from this computer.> ...  the only way to access the files in the  windows professional computer would be setting up an user account with  same user name and password that has access right. Then I can connect  and open the files, if I use an user name which professional XP computer  doesn't know, then I can just see there are files but I cannot open  these files.     I'm confused by your post as it seems that WinXP Pro is functioning as designed.

If the share on WinXP is set up to allow only certain users then that user will have to have a local account on the WinXP machine itself. That's the way it works in WinXP. That's the way it works in Linux as well.

---

### Post by dixcuxx on 2011-07-27
> **Morbius1 said:**
> I'm confused by your post as it seems that WinXP Pro is functioning as designed.

If the share on WinXP is set up to allow only certain users then that user will have to have a local account on the WinXP machine itself. That's the way it works in WinXP. That's the way it works in Linux as well.

Yes it works within the network of XP. So the files are shared in a windows XP professional computer, and only one user account can access it. Then in my another computer XP home, I have an account with exact same user name and password then I can access those files in xp professional computer.

Now I have ubuntu computer as well. I can see there are files in the professional XP, but once I try to open the files, I cannot.

---

### Post by Morbius1 on 2011-07-28
>  Now I have ubuntu computer as well. I can see there are files in the  professional XP, but once I try to open the files, I cannot.
And you are using the username and password of the WinXP pro user to access the share, right?

---

### Post by dixcuxx on 2011-07-28
> **Morbius1 said:**
> And you are using the username and password of the WinXP pro user to access the share, right?

NO, because I don't know how to do that with ubuntu.

---

### Post by Morbius1 on 2011-07-28
> I can see there are files in the professional XP, but once I try to open the files, I cannot.
So how did you get this far? If you got to the point that you can see the shares in Nautilus when you try to access it you will be prompted for a user name and password.

---

### Post by dixcuxx on 2011-07-29
> **Morbius1 said:**
> So how did you get this far? If you got to the point that you can see the shares in Nautilus when you try to access it you will be prompted for a user name and password.

I never see it prompted for user name and password in ubuntu after I clicked on the files which I can see. So I can see the files are there, but once I click, error happen.

---

### Post by dixcuxx on 2011-07-29
the error is "failed to mount windows share"

---

### Post by Morbius1 on 2011-07-29
Do you get access if you use this format:
```
sudo mount.cifs //192.168.0.100/share /home/dixcuxx/Videos -o username=andy,password=secret,uid=1000
```Change:
192.168.0.100 to the ip address of the WinXp Pro machine.
"share" to the share name on the WinXP Pro
"andy" to one of the users on WinXP Pro that you have set up to access the shared folder.
"secret" to his password.

EDIT: If successful, to unmount the remote share:
```
 sudo umount /home/dixcuxx/Videos
```

---

### Post by dixcuxx on 2011-07-29
> **Morbius1 said:**
> Do you get access if you use this format:
```
sudo mount.cifs //192.168.0.100/share /home/dixcuxx/Videos -o username=andy,password=secret,uid=1000
```Change:
192.168.0.100 to the ip address of the WinXp Pro machine.
"share" to the share name on the WinXP Pro
"andy" to one of the users on WinXP Pro that you have set up to access the shared folder.
"secret" to his password.

EDIT: If successful, to unmount the remote share:
```
 sudo umount /home/dixcuxx/Videos
```

I get the  "command not found" error when I try your suggestion.

my password includes character like %, can be be the reason?

---

### Post by Morbius1 on 2011-07-29
```
sudo apt-get install cifs-utils
```
Then try the mount command again.

I have no idea at the moment if a % in the password is a problem or not.

---

### Post by dixcuxx on 2011-08-04
I reinstall everything as I discussed in another post. Now I am ready to face this access another computer issue again:) Does anyone have any idea?:popcorn:

---

### Post by Morbius1 on 2011-08-04
I would go to a Windows forum and ask how you can fix the problem exhibited by this remark:
> So the files are shared in a windows XP professional computer, and only  one user account can access it. Then in my another computer XP home, I  have an account with exact same user name and password then I can access  those files in xp professional computer.
There is a design flaw in Windows that goes back more than a decade in which a Windows client automatically passes the users local login name and password when browsing for shares. If the WinXP server has a local user name and password that matches exactly the WinXP clients login username and password then access is automatic and the client is not asked for credentials.

But that is not a requirement. If the client does not have a matching local login username and password then the WinXP server will prompt for credentials and providing the username and password of one of the users on the WinXP server will give you access. It appears from your description that even in an all Windows network the client is not prompted for a username and password. 

If you are attempting to replicate on a Linux system this design flaw by setting up on the client the exact same username and password that exists on the WinXP server in the hopes of getting automatic access it will not work. Linux doesn't automatically pass the client's local login username and password to the server.

---

### Post by dixcuxx on 2011-08-04
> **Morbius1 said:**
> I would go to a Windows forum and ask how you can fix the problem exhibited by this remark:
There is a design flaw in Windows that goes back more than a decade in which a Windows client automatically passes the users local login name and password when browsing for shares. If the WinXP server has a local user name and password that matches exactly the WinXP clients login username and password then access is automatic and the client is not asked for credentials.

But that is not a requirement. If the client does not have a matching local login username and password then the WinXP server will prompt for credentials and providing the username and password of one of the users on the WinXP server will give you access. It appears from your description that even in an all Windows network the client is not prompted for a username and password. 

If you are attempting to replicate on a Linux system this design flaw by setting up on the client the exact same username and password that exists on the WinXP server in the hopes of getting automatic access it will not work. Linux doesn't automatically pass the client's local login username and password to the server.

Alright then what can I do?

---

### Post by Morbius1 on 2011-08-04
You need to find out why your WinXP server is not asking your WinXP client for a username and password. If you fix it between WinXP's you will likely fix it for WinXP - Linux.

---

### Post by dixcuxx on 2011-08-04
> **Morbius1 said:**
> You need to find out why your WinXP server is not asking your WinXP client for a username and password. If you fix it between WinXP's you will likely fix it for WinXP - Linux.

My XP client is a XP home, and I said somewhere said XP home would not have the ability to ask for a user name and a password...the server which shares the files is a professional XP.

---

### Post by dixcuxx on 2011-08-04
Is that possible that I don't use the windows sharing to share files in my own network? Another software does that better?

---

### Post by Morbius1 on 2011-08-04
> You need to find out why your WinXP server is not asking your WinXP  client for a username and password. If you fix it between WinXP's you  will likely fix it for WinXP - Linux.     
> **dixcuxx said:**
> My XP client is a XP home, and I said somewhere said XP home would not have the ability to ask for a user name and a password...the server which shares the files is a professional XP.
You need to find out why your WinXP Pro is not asking your WinXP Home client for a username and password. If you fix it between WinXP's you  will likely fix it for WinXP - Linux.

---

### Post by dixcuxx on 2011-08-04
> **Morbius1 said:**
> You need to find out why your WinXP Pro is not asking your WinXP Home client for a username and password. If you fix it between WinXP's you  will likely fix it for WinXP - Linux.

It is something about partition access right...so complicated

---

### Post by dixcuxx on 2011-08-04
I am surprise that no one here know why in windows xp client no login and password prompt come up.

---

### Post by Morbius1 on 2011-08-04
> **dixcuxx said:**
> I am surprise that no one here know why in windows xp client no login and password prompt come up.
Perhaps because this is a Linux Forum.

I personally don't think the problem is with the Linux client or the WinXP Home client. The WinXP server requires credentials for the clients to access it's shares. When the client tries to access it's shares the server should send back a request for those credentials. That does not appear to be happening to either the XP client or the Linux client. I have never seen that happen. 

That's why I suggested you try a Windows forum - keep Linux out of the question - and ask why the XP client doesn't get a prompt for credentials from the XP server.

---

### Post by dixcuxx on 2011-08-08
> **Morbius1 said:**
> Perhaps because this is a Linux Forum.

I personally don't think the problem is with the Linux client or the WinXP Home client. The WinXP server requires credentials for the clients to access it's shares. When the client tries to access it's shares the server should send back a request for those credentials. That does not appear to be happening to either the XP client or the Linux client. I have never seen that happen. 

That's why I suggested you try a Windows forum - keep Linux out of the question - and ask why the XP client doesn't get a prompt for credentials from the XP server.

Windows is something much easier than Linux, and if someone doesn't even knows how to use Windows, why use Linux? It is like you don't know how to drive a normal car but you buy a Ferrari and then crash.

---

