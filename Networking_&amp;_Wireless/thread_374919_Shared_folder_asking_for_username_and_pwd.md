---
title: "Shared folder asking for username and pwd"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by richard.georgiou on 2007-03-03
Good morning Ubuntu genius'

I'm reasonably new to all this Linux stuff and have just wiped out my Windows 2003 file and web server and replaced it with a Ubuntu 6.10 installation.

I've set it all up as a web server using XAMPP and everything is excellent and working very quickly. My problem comes when trying to set the server up as a file server.

I've basically got a second 250GB HDD  which is installed and working mounted in /mnt/files, I've installed the samba package and shared is as not read only (writable). I've changed the workgroup to rnetwork which is the same as my Windows PC. My user name on the windows PC and on the Ubuntu is richard and they have the same password.

When I try to map network drive on the Windows XP PC to the share on my Ubuntu box (\\richardls\files) I'm asked for a username and password, I typed in richard as the username and the password but the username and password box just comes back again. ( I assume this means incorrect usernamd or password).

I'm stuck and need some help please..! Any ideas?

Thanks for your time
Richard Georgiou

---

### Post by scxtt on 2007-03-03
on ubuntu, do:

[indent]smbpasswd -a <username to connect with>[/indent]

then try again (restart samba service, just incase) :)

note: you might need to preface smbpasswd w/ sudo, can't remember off the top of my head

---

### Post by richard.georgiou on 2007-03-03
Hello Scxtt,

Just a quick note to say thank you for posting so promptly and fixing my problem. This is why I'm moving to Linux from Windows. The support for Linux is just amazing!

Thanks again.
Richard

---

### Post by Khaled Khalil on 2007-03-03
thanks for me too scxtt

---

### Post by scxtt on 2007-03-03
you're both welcome - i struggled w/ that one too - it's one of those things that you wouldn't really think you need to do, but after it's done does make some sense

:)

---

### Post by Twopin on 2007-03-04
Hey thanks alot. Helped me too. I read over a few guides and did what they said to no prevail when it was this simple.

---

