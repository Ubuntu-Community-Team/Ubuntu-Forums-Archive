---
title: "SMB Shares"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by XBMC old School on 2011-01-25
How do i keep my shares enabled while my computer is in sleep/logoff/window lockout?

---

### Post by XBMC old School on 2011-01-26
How do i keep my shares enabled while my computer is in sleep/logoff/window lockout?

---

### Post by lukeiamyourfather on 2011-01-26
As long as the computer is running then the Samber server should be running and the shares should be accessible. If the computer goes to sleep then the shares will not be accessible and there's no way around that other than preventing the computer from going into sleep mode. The computer must actually be running and on for the Samba server to work (or any other server for that matter).

---

### Post by Elfy on 2011-01-26
Please do not post duplicates - closed.

---

### Post by cariboo on 2011-01-26
You may want to see if your network adapter supports wake on lan, that way if the system is sleeping a magic packet will wake it up.

---

### Post by Elfy on 2011-01-26
Re-opened - closed and merged at the same time it seems.

---

### Post by XBMC old School on 2011-01-26
> **lukeiamyourfather said:**
> As long as the computer is running then the Samber server should be running and the shares should be accessible. If the computer goes to sleep then the shares will not be accessible and there's no way around that other than preventing the computer from going into sleep mode. The computer must actually be running and on for the Samba server to work (or any other server for that matter).

I have a server at work that is logged out all the time and network shares and services are always running.

---

### Post by lukeiamyourfather on 2011-01-27
> **XBMC old School said:**
> I have a server at work that is logged out all the time and network shares and services are always running.

Okay. So then there's no problem and everything is working? :-k

---

### Post by Morbius1 on 2011-01-27
Am I the only person who interprets this line:
> How do i keep my shares enabled while my computer is in sleep/logoff/window lockout?
As this:
> How do i keep my [COLOR=Blue]remote[/COLOR] shares [COLOR=Blue]mounted[/COLOR] while my computer is in sleep/logoff/window lockout?

I don't have any idea at the moment - just wondering if I'm reading this incorrectly.

---

### Post by lukeiamyourfather on 2011-01-27
> **Morbius1 said:**
> Am I the only person who interprets this line:

As this:


I don't have any idea at the moment - just wondering if I'm reading this incorrectly.

Good point, but mounts should work fine too regardless of whether the user is logged in or not. The original poster is too vague for anybody to help. Here's a shot in the dark, if shares are mounted by command line instead of the fstab then they might go away when logging out. In that case put your mounts in the fstab (/etc/fstab) and they will always be there automatically when the system boots.

---

### Post by Morbius1 on 2011-01-27
> but mounts should work fine too regardless of whether the user is logged in or not.Ah, but you are assuming he's mounted them using a "sudo mount" or in fstab. 

If he's mounting them through Nautilus or "Connect to server" then it's using gvfs-mount smb: - that means userspace and that means he'll definitely loose the mount when he logs off. 

The solution as you pointed out is to put the mount in fstab since root never logs out until the machine is shut down or use something like Gigolo.

---

### Post by XBMC old School on 2011-01-27
Hey guys(people),

Sorry for being vague. Morbius1 is right. How do i keep my [COLOR=Blue]remote[/COLOR] shares [COLOR=Blue]mounted[/COLOR] while my computer is in sleep/logoff/window lockout? Luke is also right I used Fstab. [COLOR=Blue][COLOR=Red]My shares are on a separate drive than my Ubuntu install. I haven't updated my signature to include my setup yet[/COLOR].[/COLOR] How do I fix my shares? [COLOR=Red]When i leave my pc i used the Lock-out function, should i use the sleep function instead and have a password on it.[/COLOR]

As you can tell from my first post, I am a fairly green noob.  I want to become proficient with ubuntu. but because I am green instructions can't have omissions in it. 

Thanx for you time .

---

### Post by capscrew on 2011-01-27
> **XBMC old School said:**
> How do i keep my [COLOR=Blue]remote[/COLOR] shares [COLOR=Blue]mounted[/COLOR] while my computer is in sleep/logoff/window lockout? ...

I think the operative word(s) here is *"sleep/logoff/window lockout?" *.  If the host is in sleep mode then the host is offline (not accessible).  If the user is just logged off and NM is  handling the interfaces config, then the tick box for "all users" must be selected.  Window Lockout; who knows, but if the host is "up" then the interface should be live and the Samba daemon should be listening.  Or have I misunderstood something?

FYI: I have shares not mounted by **fstab** that are always up and the host is not logged into.  What might be helpful is to define which is the client and which is the server.  Not the box but rather the daemon.

---

### Post by XBMC old School on 2011-01-31
So i fixed my shares issue by setting my screensaver to password on eturn. Feel dumb. But my shares work for my windows laptop ok (w/ password) but my XBMC'd ATV hands on it. Can i remove the password protection on the Ubuntu(SMB) shares. I went to my "Personal File Sharing" and get package not installed. I tried to install and packeage failed.

[IMG]file:///home/damon/Desktop/1.png[/IMG][IMG]file:///home/damon/Desktop/1.png[/IMG]

---

### Post by Morbius1 on 2011-02-01
I'm not entirely sure I followed your last post but ...
> Can i remove the password protection on the Ubuntu(SMB) shares.Yes you can but we don't know what samba method you used to share the folder. Just go back to whatever method you used to initially create it and enable guest access.
> I went to my "Personal File Sharing" and get package not installed. "Personal File Sharing" is not Samba. It sets up a baby apache file server and uses avahi to broadcast it's share. It only allows you to share one folder however, the "Public" folder in your home directory.

---

