---
title: "reverse SSH and VNC in a windows batch file"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by DFreeze on 2007-06-04
I’m trying to grasp the concepts of SSH and VNC so helping my mom would result in less visits for trivial issues. So far I can SSH from WinXP on my local LAN and do a VNC session over that tunnel.

I’ve read about the concept of reverse VNC, which makes router configurations unnecessary (she would initiate the connection). Also there’s some info to be found about reverse SSH. Now on to the main question:

Can someone help me make a single click batch file that would reverse-SSH to my server (with the right passwords set) and after that open the viewer in listening mode. She shouldn’t be exposed to configuration windows of PuTTY and the like. I’d have to spend the next 15 minutes calming her down on the phone and explaining that it’s all not as difficult as it looks. 

It ‘ll be something in the lines of:

```

C:\SSH\plink –R5000:127.0.0.1:5000 my.ip.com
vncviewer -listen

```

Maybe something like that allready exists, but I couldn’t find it on the forums or Google. If you’ve seen it though, please provide a link.

It’s OK if I have to go there once to set it all up (ports, IP addresses, passwords and the like), but after that all she should be seeing is a single icon on the desktop which would initiate the link. It would be nice if the connection would be terminated if she would close some window (if a window pops up in the first place).

---

### Post by DFreeze on 2007-06-08
anyone?

---

### Post by Mr. C. on 2007-06-08
You want the Single Click application at:

[http://www.uvnc.com/addons/index.html](http://www.uvnc.com/addons/index.html)

This will allow you to create an application that she can double click.  You run your VNC viewer in Listen mode, your mom double-clicks the application, and you accept the connection.

MrC

---

### Post by DFreeze on 2007-06-08
Yeah, I've seen that app. Pretty awesome! Only thing is: the encryption that it provides, only works for Windows. Could that app also work when I create a reverse SSH tunnel from her system first? I can configure uVNC SingleClick to point to my server, so I could also tell it to do that through the SSH tunnel, right?

Anyone done that before? Any suggestions on how such a batch file should look?

---

### Post by Mr. C. on 2007-06-08
Right.

So here is what I used to do.

I had my family download Tunnelier (an SSH client), and I sent them a Tunnelier configuration profile I had configured for them.  They would double click the profile and start the connection.  The reverse tunnel was already configured, so I would just use my VNC viewer to connect to my localhost at the configured port.

MrC

---

### Post by DFreeze on 2007-06-12
Would that also work with public/private key configurations, or only with passphrases?

---

### Post by Mr. C. on 2007-06-12
Passphrases are used to decrypt your local private key.  Tunnelier works with OpenSSH key formats.

---

### Post by dbott67 on 2007-06-12
Not to sidetrack your thread so far (because the Tunnelier config profile seems like it's fairly easy to implement), but I've written a [reverse-VNC HOWTO]("http://ubuntuforums.org/showthread.php?t=299489") (check my signature for the link) that I use for similar situations.  Mind you, it's not encrypted, however, the developer of x11vnc (Karl Runge) added a link to his site that covers it nicely in post #20:

[http://www.karlrunge.com/x11vnc/#faq-singleclick](http://www.karlrunge.com/x11vnc/#faq-singleclick)

Karl has all sorts of info on the site for implementing encryption in a reverse-conection (look for the '-ssl' option and STUNNEL for encryption).

As for me, I host an UltraVNC 'single-click' executable (for Windows) on my website and I just get users to download & run the program.  For me, adding an encrypted tunnel adds a layer of complexity that might otherwise turn a 5-minute job into a painful exercise when dealing with inexperienced users *(although after reading what MrC does with Tunnelier, it does seem quite straight-forward)*.

**@MrC:** How does the performance of running VNC through Tunnelier compare to an unencrypted session?  Before I switched to NX Machine for remote desktop, I used to tunnel VNC over SSH and it was painfully slow (10 Mb synchronous fibre to 5Mbps down/1 Mbps up DSL circuit).

Thanks,
Dave

---

### Post by DFreeze on 2007-06-12
> **dbott67 said:**
> Not to sidetrack your thread so far (because the Tunnelier config profile seems like it's fairly easy to implement), but I've written a [reverse-VNC HOWTO]("http://ubuntuforums.org/showthread.php?t=299489") (check my signature for the link) that I use for similar situations.  Mind you, it's not encrypted, however, the developer of x11vnc (Karl Runge) added a link to his site that covers it nicely in post #20:
[...]

Thanks Dave, I found your thread already. Very detailed and helpful. Maybe unencrypted is sufficient. I won't do online banking over VNC, and who'd be interested in my momma's wallpaper ;-)

But this is more of an experiment to get my head around SSH, so I'd like to get it going anyway. Even if I won't use it in the end for remote assistance. When the SSH part works, I'll use your tutorial for the VNC part.

---

### Post by Mr. C. on 2007-06-12
> **dbott67 said:**
> 
**@MrC:** How does the performance of running VNC through Tunnelier compare to an unencrypted session?  Before I switched to NX Machine for remote desktop, I used to tunnel VNC over SSH and it was painfully slow (10 Mb synchronous fibre to 5Mbps down/1 Mbps up DSL circuit).

Thanks,
Dave

I find for simple remote management, either is fine.  The limiting factor is typically not the encryption, but the local broadband I'm connected to.  The network path's average latency / packet reliability is as critica as, and can have a more detrimental impact to, the max marketing spec of the pipe.

MrC

---

