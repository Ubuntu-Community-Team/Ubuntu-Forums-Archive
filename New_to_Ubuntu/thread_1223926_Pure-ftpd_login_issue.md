---
title: "Pure-ftpd login issue"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by jlklein on 2009-07-26
Hi all,
I recently replaced a pc hooked to my tv with an Ubuntu machine (9.04) and am attempting to transfer some files to it. I installed pure-ftpd with the Synaptic packet manager and started it (pure-ftpd &), however, I am unable to log in from my windows PC. The most detailed return data I got was via FireFTP in passive mode (no security), which returned:

220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
220-You are user number 1 of 50 allowed.
220-Local time is now 18:33. Server port: 21.
220-This is a private system - No anonymous login
220-IPv6 connections are also welcome on this server.
220 You will be disconnected after 15 minutes of inactivity.
       USER (removed)
331 User (removed) OK. Password required
       PASS (password not shown)
530 Login authentication failed
Unable to make a connection. Please try again.

I've also tried in SFTP mode and got:
Fatal: Network error: Connection refused

AuthTLS and AuthSSL modes returned:
500 This security scheme is not implemented

Implicit SSL just didn't connect.


I'm using the username/pw of my Ubuntu login and this is on a home network behind a Linksys WRT54GL router. XP laptop is wireless and the Ubuntu PC is wired. I can ping each machine from the other one without issue and both reach the internet fine. I can also use TightVNC to view/control the Ubuntu PC from the XP laptop after enabling TightVNC server on the Ubuntu PC.

So, while I can hold my own with Windows stuff, I'm way out of shape with Linux stuff, esp command line references. Anyone got any ideas of why I'm being refused login from the XP side to the Ubuntu machine?

Thanks,
Jeff

---

### Post by jonobr on 2009-07-27
Hello


Given it accepts the user and rejects the password (which Im guessing is ok)
Im wondering if you are only allowing anonymous logins?

Instead of using the uname password on your ubuntu try
anonymous and any password 

see if it logs you in

---

### Post by MockY on 2009-07-27
I would opt for SSH if I were you. FTP servers in Windows is easy to deal with (Serv-U is superior) but in Linux it is far from user friendly.
install ssh on the Ubuntu box with
```
sudo apt-get install ssh
```
and you can then connect to it from your Windows box either with Winscp or Putty (if you prefer command line). Connecting from Ubuntu to Ubuntu is even easier via Nautilus (Places - Connect to server - SSH).

---

### Post by jonobr on 2009-07-27
+1 on ssh

Also, FTP is a transparent protocol and can be read for usernames and passwords.
SSH is far more secure

---

### Post by jlklein on 2009-07-27
> **jonobr said:**
> +1 on ssh

Also, FTP is a transparent protocol and can be read for usernames and passwords.
SSH is far more secure

Hi, thanks for the replies. I did get the same recommendation from a co-worker earlier, so now I have ssh installed/started and have installed WinSCP on my XP laptop. 

I've tried logging into both the IP address and machine name (pc-desktop.local), have verified it set to port 22 and SFTP w/allow SCP fallback (seen on Steven Harms' blog tutorial) and still no luck.

I did, however, check the Log File Viewer auth.log and find that I WAS actually getting invalid user errors. So, it appears it's not recognizing either my user name/pw.

From what I've read, I should be able to use the same username/pw as I use to log directly into the physical Ubuntu machine; is this incorrect? If so, how do I set up a username/pw that will be accepted?

Thanks much,
Jeff

---

### Post by MockY on 2009-07-27
Yes, you can use the same credentials for your SSH connection as for physical access to your machine. You can also create a new user and see if that works. If so, then I have no idea to why you can't log in with your main account.
Also, keep in mind that the UN/PW is case sensitive and user names are usually in all lower caps.

---

### Post by jlklein on 2009-07-27
Hmm...kind of a weird unrelated occurrence that may actually shed some light. I do know that I had the right user name and login, as I locked the screen and then re-signed in with the username and login successfully.

However...
Tonight my Ubuntu locked up after watching a video with the black screen with movable white mouse cursor, so I did the Ctrl-Alt-F2 combo which got me to the machine-name:login prompt. 

It wouldn't take my login/password.

Is there something different about the login username/pw I would enter for the desktop login and what Ubuntu would ask for after a Ctrl-Alt-F2 break?

Thanks,
Jeff

---

### Post by jonobr on 2009-07-28
Should be the same?

Are you sure the username and pw are not getting munged up or you have something going on with your keyboard.

---

### Post by jlklein on 2009-07-28
> **jonobr said:**
> Should be the same?

Are you sure the username and pw are not getting munged up or you have something going on with your keyboard.

Yeah, I even locked the screen and unlocked it with the password, so I know that's working right.

Spoke to a friend at work today who gave me some tips to check group memberships and passwords so will check that tomorrow. 

Jeff

---

### Post by jonobr on 2009-07-29
mmmmm maybe, but Im not convinced,

username pw should work....

try the tips though, and if they work, hopefully you can post results here.

---

### Post by jlklein on 2009-07-29
> **MockY said:**
> Yes, you can use the same credentials for your SSH connection as for physical access to your machine. You can also create a new user and see if that works. If so, then I have no idea to why you can't log in with your main account.

Hmm...something occurs to me here as I'm re-reading the various replies:
MockY states, "Yes, you CAN use the same credentials for your SSH...."

Does that mean there should already be a default SSH user enabled with the currently physically logged-in user's name/pw by virtue of turning on SSH or do I have to make an "SSH user" (right term?) but MAY USE the same user/pw as my physical login without confusing Ubuntu?

...My English teacher is probably rolling over in her grave over that last sentence ;)

Thanks,
Jeff

---

### Post by MockY on 2009-07-29
By enabling SSH, all you do is allowing available users to remotely log in to the target computer. Since the default user is the user you created when installing Ubuntu, this exact user can log in to this machine remotely using SSH. There is no need to create additional users.

If both involved machines have SSH installed, you can then connect to it by typing the following in a shell (substituting the placeholder for your own information
```
ssh username@ipnumber
```
If the remote computer has SSH installed, you should be prompted for the password that belongs to the user you provided before the @-sign. Once entered and accepted, your prompt should change and you are now logged into the remote computer. Once you have done that, you can simply type "exit", and now you know that it works just fine.
If this is not the case, you have manually done something to completely screw up the user accounts. But since you can physically log in to your machine using a username and password, this should work just fine using ssh as well.

---

### Post by Isarian on 2011-06-28
> **MockY said:**
> I would opt for SSH if I were you. FTP servers in Windows is easy to deal with (Serv-U is superior) but in Linux it is far from user friendly.
install ssh on the Ubuntu box with
```
sudo apt-get install ssh
```
and you can then connect to it from your Windows box either with Winscp or Putty (if you prefer command line). Connecting from Ubuntu to Ubuntu is even easier via Nautilus (Places - Connect to server - SSH).

If anyone in this thread is still looking, Serv-U just opened up a public beta with Linux support at [www.Serv-U.com](www.Serv-U.com). I was notified via newsletter because my company uses but they have open signups for the beta at that site.

---

