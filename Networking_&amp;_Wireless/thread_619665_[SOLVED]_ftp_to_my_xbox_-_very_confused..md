---
title: "[SOLVED] ftp to my xbox - very confused."
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by Ripfox on 2007-11-21
Hello I would like to learn about ftp-ing. I recently moded my xbox successfully and now I want to learn how to ftp files to it with Ubuntu. Any help and explanation about ftp is appreciated. Thanks and glad to go back to complete noob-dom. :)

---

### Post by davidgarcin on 2007-11-21
Little confused at how you can be a noob with 699 posts......

At any rate.  I'm assuming you have some variety of linux on your xbox?  If so, there should be an FTP client already installed on it.  Read the manual on specific commands, but generally it's just: "ftp yourServer" and then "get yourFile"

However, you do need to set up an FTP server on your Ubuntu machine - try this how-to:
[https://help.ubuntu.com/7.10/server/C/ftp-server.html](https://help.ubuntu.com/7.10/server/C/ftp-server.html)

There is plenty of documentation available.  Google is your friend :-).

Hope that helps.
-Dave

---

### Post by Ripfox on 2007-11-21
Yes well anyone with an ounce of sense will tell ya, you are always a noob at something! :)

Yep. I used and use google. I just wanted to know what the best ftp thingy was for Ubuntu...turns out Filezilla was ported and is in the repos, and it was pretty easy to figure out. Thanks for the reply, I will post back on my adventure!

Peace

Rip

---

### Post by davidgarcin on 2007-11-22
Yeah, Filezilla is quite good, but I'm fairly sure that only the client has been ported.  You still need an FTP server running on your comp.

Are you running Ubuntu on your xbox, out of curiosity?  Or some other distro?

---

### Post by Ripfox on 2007-11-25
I'm running xbmc as an app on top of unleashed x. I just downloaded Filezilla from the repos and it worked out of the box...like a charm.

---

### Post by davidgarcin on 2007-11-25
cool, glad it worked out.

---

