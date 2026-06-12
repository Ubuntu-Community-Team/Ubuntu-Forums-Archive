---
title: "SSH and changing resolution"
date: 2007-09-18
forum: Networking &amp; Wireless
---

### Post by ziaziu on 2007-09-18
I hope somebody has done this before...

My laptop can handle 1024x768 resolution and is se to that currently.  I am trying to connect to a server that runs a software package that I need for work.  The command I use is:

ssh -Y [email]username@server.addr[/email]ess

Unfortunately the resolution that is 'sent' to me is (i am pretty sure) 800x600.  Because of this, I can't see some of options that are present in some windows.

My question is:  can I force to have the server send me a fixed resolution to my laptop?  Or is this not possible?

Thanks in advance

---

### Post by multi on 2007-09-19
What software package are you connecting to? I suspect the resolution is being forced from the serverside.

---

### Post by ziaziu on 2007-09-19
It's StarCD, which has a horrible GUI...

---

### Post by multi on 2007-09-19
Here's someone with a the same problem. Turns out the only option is to use a screen that supports a higher resolution. 

source: [http://www.cfd-online.com/Forum/starcd_archive_2001.cgi/read/859](http://www.cfd-online.com/Forum/starcd_archive_2001.cgi/read/859)

Ooh and I think the resolution the server is sending to you is 1280x1024 because if it was 800x600 you would be able to see the complete GUI on your 1024x768 screen.

---

### Post by ziaziu on 2007-09-19
Many thanks,

After trailing through some man's and the StarCD user guide I kind of figured that it would be a dead end...But your post sealed it's fate - Need to buy a new monitor!

Many thanks! :KS

---

### Post by ziaziu on 2007-10-14
Sorted out the resolution problem in a backwards way - I set up a 'virtual resolution', which wasn't as easy as it seems!  There is virtually no easy and straightforward tutorial on how to set this up on UBUNTU.  Hence, through trial and error I got it working and it's all documented in [[COLOR="Red"]this tutorial[/COLOR]]("http://ubuntuforums.org/showthread.php?t=562202")

Hope this helps for others!

---

