---
title: "Root login help needed"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by The Eight-Bit Link on 2009-11-29
How do you login as root? moreover, what's the password? My flavor is xubuntu 9.10.

---

### Post by HereInOz on 2009-11-29
Typically, Ubuntu is installed with the root account disabled, for security reasons.  If you want to perform administrative tasks, then the user which you set up during the install will have administrative priviledges, by putting in that user's password for things which require it.  (Updates, etc).

To get root priviledges in the terminal, type sudo [command] and then [Enter] and you will be asked for a password.  This, again is the password of the user with admin priviledges.

To become root in the terminal, type sudo su, and then put in your password.

<snip>

Hope this helps.

---

### Post by Cuco3 on 2009-11-29
I don't think anyone can answer that question for you on these forums; it goes against the Ubuntu Security Model to log in as Root.

You'll have to do a google search for your answer.

---

### Post by HereInOz on 2009-11-29
Oh, also, if you want to be able to log in as root from the login screen, then you need to tick "Allow administrator login" in the Security tab of the Login window preferences (System > Administration > Login window).

My recommendation is that if you enable the root account for a temporary reason, you should disable it after.  The reason is that if anyone wants to do a brute force crack of a Linux box, the first username they are going to try is root.  That is one big reason why it is disabled.

---

### Post by Cuco3 on 2009-11-29
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

>  				 				**Forum policy on log-in-as-root tutorials** 			
 			 			 		   		 		 		**Policy**
Tutorials explaining how to enable the root account for a graphical login or autologin will not be supported on the forums and will be moved to the Jail. Although we believe people should have the freedom to run their computers however they want, we also believe in supporting Ubuntu's security model. You can find or post information elsewhere on the internet regarding graphical Ubuntu root logins; such tutorials do not have to be hosted on the Ubuntu Forums.

So go ahead and make sure to follow the tutorial before this thread gets deleted.

---

### Post by aysiu on 2009-11-29
> **Cuco3 said:**
> [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)



So go ahead and make sure to follow the tutorial before this thread gets deleted.
That link also explains how to do everything you *think* you need a root login for but don't actually.

---

