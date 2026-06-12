---
title: "Using ftp to download source code for program won't work"
date: 2017-05-15
forum: Networking &amp; Wireless
---

### Post by John_Patrick_Mason on 2017-05-15
I'd like to download the source code for the diction program using ftp as illustrated on page 346 of [this]("http://linuxcommand.org/tlcl.php") book.

Here's the terminal's output:

```

Connected to ftp.gnu.org.
220 GNU FTP server ready.
Name (ftp.gnu.org:mason): anonymous
230-Due to U.S. Export Regulations, all cryptographic software on this
230-site is subject to the following legal notice:
230-
230-    This site includes publicly available encryption source code
230-    which, together with object code resulting from the compiling of
230-    publicly available source code, may be exported from the United
230-    States under License Exception "TSU" pursuant to 15 C.F.R. Section
230-    740.13(e).
230-
230-This legal notice applies to cryptographic software only. Please see
230-the Bureau of Industry and Security (www.bxa.doc.gov) for more
230-information about current U.S. regulations.
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> cd gnu/diction
250 Directory successfully changed.
ftp> ls
200 EPRT command successful. Consider using EPSV.
425 Failed to establish connection.
ftp> exit
221 Goodbye.

```

---

### Post by oldos2er on 2017-05-15
You can just get it from [https://ftp.gnu.org/gnu/diction/](https://ftp.gnu.org/gnu/diction/)

---

### Post by John_Patrick_Mason on 2017-05-15
OK, but is there a way I can do it through ftp? I don't have much experience with file transfer protoco (ftp), and would like to learn.

---

### Post by bab1 on 2017-05-15
You lost network connectivity  See the line with this: Failed to establish connection.

I have the book and the instructions work.  I could get to the **gnu/diction** directory.   I would try it again.  In the end you can always use a Firefox or Chrome to visit the same site with [http://ftp.gnu.org](http://ftp.gnu.org) [/B]or you can go directly to it with [http://ftp.gnu.org/gnu/diction/](http://ftp.gnu.org/gnu/diction/)

---

### Post by John_Patrick_Mason on 2017-05-15
[QUOTE=bab1]You lost network connectivity  See the line with this: Failed to establish connection.[/QUOTE]

But I have a Firefox window open with a tab with YouTube open. I don't get it. Could it be a firewall/router misconfiguration?

---

### Post by oldos2er on 2017-05-16
You lost the connection with the ftp server, not your internet connection.

---

### Post by steeldriver on 2017-05-16
Try entering passive mode before issuing the ls command:

```

230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> cd gnu/diction
250 Directory successfully changed.
ftp> **passive**
ftp> ls

```

---

### Post by John_Patrick_Mason on 2017-05-16
The passive command worked. Thanks. Any idea why active FTP wouldn't work?

---

### Post by steeldriver on 2017-05-16
Honestly, I'm hazy on the details myself - this seems to be a good explanation:

[What is the difference between active and passive FTP?](http://stackoverflow.com/a/1699163/4440445)

HTH

---

### Post by John_Patrick_Mason on 2017-05-16
> **steeldriver said:**
> Honestly, I'm hazy on the details myself - this seems to be a good explanation:

[What is the difference between active and passive FTP?]("http://stackoverflow.com/a/1699163/4440445")

HTH

Thanks! I read the link your provided. It was probably the firewall. I now consider this thread to be officially solved.

---

### Post by oldos2er on 2017-05-16
Please use Thread Tools at the top of the page to mark the thread 'Solved,' thanks.

---

