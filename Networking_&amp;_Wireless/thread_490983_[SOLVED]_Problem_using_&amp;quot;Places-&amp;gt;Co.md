---
title: "[SOLVED] Problem using &amp;quot;Places-&amp;gt;Connect to Server...&amp;quot;"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by lucky.13 on 2007-07-03
Hi,

I want to map a SSH server as a folder on my desktop, but with no success.
I can connect to the server via terminal and the ssh command.
I can also connect to it via gFTP using SSH2.

But, when I try to use Places->Connect to Server... it doesn't work.
I get a small window that says "Opening <servername>" and then nothing happens.

This problem is on a Dell Latitude d820 laptop at work, I have connected to the server from another computer at home this way and it was no problem. I also believe I was able to use Connect to Server... on the laptop when I was using the Ubuntu Feisty live CD.

Anyone have any suggestions?

I am using Ubuntu Feisty Fawn 64 bit.

On a side note, I've set up a Connect to Server... connection to a FTP server I also use. No problem at all.

Ok, thanks in advance :)

---

### Post by lucky.13 on 2007-07-03
Resolved using the method described in this thread: [http://ubuntuforums.org/showpost.php?p=2862609&postcount=8](http://ubuntuforums.org/showpost.php?p=2862609&postcount=8)

System > Administration > Network > Network Settings > General tab > uncheck 'Automatic service discovery'

---

