---
title: "start torrent download via ssh"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by sistoviejo on 2007-12-06
How do I do this?
I've  tried btdownloadcurses and btdownloadheadless but the process gets killed when I close the ssh client.
I also tried running with an & at the end so it runs it the background, but that doesn't help either.
It seems the job is atached to my current session so when I logout the process gets killed.
Is there a way to keep the download running after I close the session?
thanks!

---

### Post by Original Brownster on 2007-12-06
Hi, 
Check out the tool called 'screen' it allows to connect to a session and disconnect and leave it running, I haven't used it but I would imagine you can connect to the server via ssh then start 'screen'.

HTH

---

### Post by sistoviejo on 2007-12-07
That's just what I needed! thanks! :KS :KS :KS

It comes with default installation of Ubuntu. 

Here's a tutorial in spanish: [http://jacobo.tarrio.org/ex/screen/](http://jacobo.tarrio.org/ex/screen/)
Here's one in english: [http://www.kuro5hin.org/story/2004/3/9/16838/14935](http://www.kuro5hin.org/story/2004/3/9/16838/14935)

---

