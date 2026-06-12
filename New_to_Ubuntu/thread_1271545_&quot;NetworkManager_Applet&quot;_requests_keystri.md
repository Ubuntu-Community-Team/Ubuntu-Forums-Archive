---
title: "&quot;NetworkManager Applet&quot; requests keystring access loop"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by EliYui on 2009-09-21
I am running Ubuntu 8.10.  In order to access my schools VPN server, I needed to install "vpnc" and "network-manager-vpnc" packages.  I encountered the following problem after installing both packages...

NOTE:  Initially when I first installed the packages I was not asked for my user password to allow the "Synaptic Package Manager" to make changes.  I have since tried to reinstall both packages but still encounter the same problem when  I first start up my computer.  


Whenever I login to my computer, a prompt appears asking me to allow access for the "NetworkManager Applet" (/usr/bin/nm-applet).  When I try to enter my user password, the same prompt appears again and again.  There is a Deny option but I have to click it two times before the prompt goes away.  After I deny the prompt two times, I am prompted to enter my WPA keystring to access my wireless network.  I enter my WPA password for my wireless network and the computer then goes through the process of connecting to the network.  Meanwhile, the orginal "NetworkManager Applet" prompt then appears and asks for premission to change the keystring to save the WPA password I just entered.  I encounter the same problem as before.  The prompt continues to loop until I click the Deny button twice.  

I have also tried to use the root user password in the "NetworkManager Applet" prompt, but encounter the same looping issue that I have when I try my user password.

---

### Post by Chronon on 2009-09-21
I believe you are being asked for a keyring password.  This may or may not be the same as your user or root passwords (if that's even enabled).  On my desktop system I use a different keyring password from my login passwords.

---

### Post by EliYui on 2009-09-21
I haven't stepup a keystring password.  How would I go about doing that and does it have a default password?

---

### Post by Chronon on 2009-09-21
I'm not aware of any default.  The fact that it's asking for a password seems to indicate that you entered a password to store some log in info previously.  I would imagine that there's a way to reset it. . .

Try this: [http://ubuntuforums.org/showthread.php?p=2302037](http://ubuntuforums.org/showthread.php?p=2302037)

---

### Post by mcduck on 2009-09-21
The keyring password is set to same as your login password during the install. As long as both passwords are the same (and you use normal login instead of automatic) the keyring will be unlocked automatically for you.

If you then change your login password you need to change the keyring password yourself. (They are not tied to each other since some people prefer using different passwords for both). And if you enable automatic login you need to either unlock the keyring manually or remove it's password completely.

Here's how to change/remove the keyring password:

1.Open the keyring manager (Applications/Accessories/Passwords and Encryption Keys)

2. Go to Passwords-tab (or if you really are still running 8.10 like your profile says, go to Preferences and *then* the Passwords-tab)

3. Right-click the "Passwords:login"-keyring & select "Change Password"

Now you can change the keyring password. If you use normal login set the password to same as your login password to unlock the keyring automatically. If you use automatic login leave the new password fields empty to remove the keyring password.

(and no, i definitely wouldn't suggest dong what the thread posted above suggests. Deleting the keyring won't really solve the problem and you'd loose all data stored in the keyring, like your network and encryption keys..)

---

### Post by EliYui on 2009-09-21
Thanks, that seems to have taken care of the problem.  

I had also had changed my login password the same time I was installing that program.  When I used my old login password, it let login to the key-string prompt successfully.

---

### Post by CaptainMark on 2009-09-21
i had this problem before, i think its caused by the keyring password being created by someone other than the system admin user.

---

### Post by mcduck on 2009-09-22
> **CaptainMark said:**
> i had this problem before, i think its caused by the keyring password being created by someone other than the system admin user.

That's not possible. Every user has their own keyring, and thus also their own keyring password.

---

