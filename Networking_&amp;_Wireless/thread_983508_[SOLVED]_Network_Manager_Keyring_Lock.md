---
title: "[SOLVED] Network Manager Keyring Lock"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by mothraman on 2008-11-15
I see other posts on this, but htey don't seem to apply to my situation.

My wireless adapter was working fine since I installed Intrepid a week ago.  I could see, but not access, files on an XP machinre and a Vista machine on the same network. So, I tried un-commenting security=user in smb.conf and adding a user with password to smbuser.

Also, the windows machines could not see my ubuntu machine. So, I applied sharing and installed the packages it wanted to install, then rebooted.

On reboot, my password was not accepted (only one I've had, and yes caplock was off).  I restarted in recover mode and reset the password to what it had been, and rebooted. 

Now, I get the message that "Network Manager Applet wants access to the default keyring but it is locked."  I had never seen that before.  I entered my wireless security key, but it would not take it.

Applications/Accessories/Passwords and Encryption Keys  shows "Automatically unlocked when user logs in."


Any ideas why this is happening and how I can fix it?

---

### Post by mothraman on 2008-11-16
I can't answer why this all happened.  In other threads, I found reference to deleting files in "~/.gnome2/keyrings/". I could never find that.

However, I found that "Applications/Accessories/Passwords and Encryption Keys" yields a dialog. Click on Edit/Preferences, highlight the key that is displayed, and click remove keyring.  

You are then asked for the wireless security key. I did not enter a password, and ignored the security warnings, and it connected.

---

### Post by udoko on 2008-11-16
Very good. That is what I was looking for. Now my Wubi starts up just like Vista. Don't need any logins and passwords. This computer is in my garage for my own use only. Nobody else has any use for it.
Thanks
Udoko

---

### Post by Insane_Homer on 2008-11-16
[http://ubuntuforums.org/showthread.php?t=964255](http://ubuntuforums.org/showthread.php?t=964255)

worked for me

---

### Post by likebikes on 2008-11-16
Hi
did you manage to sort out access to your samba shares from Vista?

if not then add this line to your smb.conf

client ntlmv2 auth = yes

I had similar problems and found this solution on the forum. I don't understand the technicalities but it works!!!!

cheers

---

### Post by mothraman on 2008-11-16
Vista and XP machines can now both see and access files on the Ubuntu machine.  I right clicked on my home folder in file browser, then sharing, and clicked share this file.  

Ubuntu can access files on the XP machine but not the Vista machine. The XP machine can access Vista.

Mostly solved, still working on it.

---

### Post by mothraman on 2008-11-16
add this line to your smb.conf:
client ntlmv2 auth = yes


That appears to have worked!  Thank you. Now I have to go see why.

I spoke too soon.  I had have to enter the location in file browser "smb//computer/folder" and enter user and password in order to see the shares.

That took me a while, because I clicked on the computer name and it showed nothing--so I thought I had other problems.

Now, my problem is that I can't print.  I can add the printer on the vista machine to my ubuntu machine my specifying the workgroup/computer/printer in the dialog, selecting set authentication details now, giving user/password, and clicking verify.  When I try to print a test page all looks well, the printer makes noises, but nothing comes out. The queue shows "remote downlevel document" printing--but I have to unplug the printer to get rid of it and I get nothing printing.

Next stop: HP page for a better driver.

---

