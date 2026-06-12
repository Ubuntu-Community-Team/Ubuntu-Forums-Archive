---
title: "Web VNC Client?"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by Muffy on 2008-07-24
Is there an online or flash VNC client around so I can connect to my Ubuntu home desktop from work, without having to install a VNC client (as the work PCs won't allow it)? Thanks.

---

### Post by superprash2003 on 2008-07-25
i guess this is what you need [http://prash-babu.blogspot.com/2008/06/how-to-access-your-ubuntu-machine-from.html](http://prash-babu.blogspot.com/2008/06/how-to-access-your-ubuntu-machine-from.html)

---

### Post by NUboon2Age on 2010-06-21
> **superprash2003 said:**
> i guess this is what you need [http://prash-babu.blogspot.com/2008/06/how-to-access-your-ubuntu-machine-from.html](http://prash-babu.blogspot.com/2008/06/how-to-access-your-ubuntu-machine-from.html)

[How to access your Ubuntu Machine From Anywhere in the World Using Your Web Browser]("http://www.prash-babu.com/2008/06/how-to-access-your-ubuntu-machine-from.html")
[How To Remote Control Your Ubuntu Machine From The Internet Using A Software Client]("http://www.prash-babu.com/2008/06/how-to-remote-control-your-ubuntu.html")

---

### Post by Ubuntiac on 2010-06-29
Mind bogglingly awesome. Now I can actually leave my laptop at home when I travel and access my full power desktop box. Thanks for posting that!

I wonder how well this would work if you were accessing your computer by a much smaller screen, eg on an android phone... after all, the client seems to just be java...

---

### Post by arsya on 2010-07-16
I found and tested [flashlight-vnc]("http://www.wizhelp.com/flashlight-vnc/") and [noVNC]("http://kanaka.github.com/noVNC/") on google chrome browser. flashlight-vnc uses flash, while noVNC uses HTML5. I prefer to use noVNC, because I have problem sending ctrl-commands from flashlight-vnc.

If you need some more information on setting and running noVNC, please take a lot at my [blog]("http://murzal-arsya.blogspot.com/2010/07/novnc-html5-vnc-client.html").

I am really impressed with the developer of noVNC. Such a great work.

---

### Post by gradinaruvasile on 2010-07-16
Ok, this is not in a browser, but have you considered using TeamViewer?
It is extremely simple to use and it works great over firewalls. It is also more secure than VNC and it can be used without actually installing it (you need wine for this mode in Ubuntu but it works perfectly well).
In Windows (or through Wine in Linux), just start the installer and select "run" (no administrator rights required and nothing is installed).
Make sure you specified a fixed password on your Ubuntu box (an remember its numerical connection ID).

BTW, Ubuntu has a built-in VNC server/client. - Edit: sorry my bad, you dont need this.

---

### Post by YesWeCan on 2010-07-16
[QUOTE=arsya]I found and tested [flashlight-vnc]("http://www.wizhelp.com/flashlight-vnc/") and [noVNC]("http://kanaka.github.com/noVNC/") on google chrome browser. flashlight-vnc uses flash, while noVNC uses HTML5. I prefer to use noVNC, because I have problem sending ctrl-commands from flashlight-vnc.[/QUOTE]
Hey I just tried noVNC - pretty awesome. Slower than Vinagre client using Chrome but highly versatile. Instructions are, well, sigh. The launch.sh needs to be executed from the parent directory or it appears to work but gives ambiguous error 404. Grrr. Ie: 'utils/launch.sh --vnc hostname:vncport'

The encrytpion tick box doesn't seem to work for me. What does this do anyhow? But I'd be content to access using https if I can figure this out. Any tips?

---

