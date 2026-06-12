---
title: "FTP. FileZilla. Friend's house 10 miles away. Possible?"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by Roasted on 2008-06-15
My buddy and I are constantly transferring stuff back and forth, whether it's pictures, music, stuff for college, etc... but he lives 10 miles away and jumpdrives often aren't the best option.

I figured it'd be neat for him and I to set up an FTP setup. Is there anyway we can do that with being 10 miles apart?

It'd just be easier for me to drop 900 vacation pictures on a folder in que and have him go home, hit download, and bam... he downloads the pictures I just sent him without the need for external hdd's of any sort. 

Is this possible? I opened FileZilla, but oddly enough I have never touched FTP despite my experience with computers. I'm sort of clueless...

---

### Post by unicorn_2003_1 on 2008-06-15
Install **GProFTPD**, a GUI frontend WITH the FTP server. It's available in the Ubuntu repository, so just straight forward click through. Then set it up (done in GUI), make a user account for your "buddy", tune up some security settings, and you're done.

Can't believe I just installed this server to answer your question. But yeah, worth it. Good luck.

---

### Post by Roasted on 2008-06-15
What XP based FTP client would you recommend for him to use? He has Ubuntu, however, it doesn't recognize his wireless, so that partition is just kind of sitting idle right now... leaving XP to be his main.

P.S. - Although I appreciate your help, I'm still confused. As I said, I've never used FTP before. -ever-

Tune this up, little of that, check this box over here... what? :(

---

### Post by dmizer on 2008-06-15
there is a good ftp server howto linked in my sig.  it's a bit of work, but i did end up with a working ftp server after i was finished with the howto.

here is a good windows ftp client: [http://filezilla-project.org/](http://filezilla-project.org/)

---

### Post by unicorn_2003_1 on 2008-06-15
Dude, FTP is not some crazily confusing stuff, and plus you got the GUI, just look at it. 

Filezilla would be a good client for him on xp

---

### Post by Roasted on 2008-06-15
> **unicorn_2003_1 said:**
> Dude, FTP is not some crazily confusing stuff, and plus you got the GUI, just look at it. 

Filezilla would be a good client for him on xp

I am looking at it. But what is required to get this set up? I set up an account name for my buddy, okay, check. Password for him? Got it. 

But a few questions remain. The default directory seems to be under /var... which is in root. Do I have to move the FTP files to that dir to transfer them? Or is it safe to change it to /home/jason/music if I want to give him access to all of my music?

Also - How does his FTP machine even connect to mine? I see no way for them connecting based off of the information I've read about and been given here.

---

### Post by ddixonr on 2008-06-15
I have gproftpd set up myself. It really is pretty simple once you have it installed. Type your public ip address into the server box. Then give your friend a call, tell him to type it into a web browser preceded by [ftp://,](ftp://,) or filezilla, and away you go.

---

### Post by Roasted on 2008-06-15
> **ddixonr said:**
> I have gproftpd set up myself. It really is pretty simple once you have it installed. Type your public ip address into the server box. Then give your friend a call, tell him to type it into a web browser preceded by [ftp://,](ftp://,) or filezilla, and away you go.

Isn't an internal IP address needed? I have 6 computers on my LAN here... I thought you'd need an internal as well for the sake of knowing which computer it routes to.

---

### Post by bukwirm on 2008-06-15
You'll need to setup your router to forward whatever port your FTP server uses to the computer running your FTP server (look for an option called "Port Forwarding" on the router config page). Then give your friend your external IP address.

---

### Post by dmizer on 2008-06-15
> **Roasted said:**
> I am looking at it. But what is required to get this set up? I set up an account name for my buddy, okay, check. Password for him? Got it. 

But a few questions remain. The default directory seems to be under /var... which is in root. Do I have to move the FTP files to that dir to transfer them? Or is it safe to change it to /home/jason/music if I want to give him access to all of my music?

Also - How does his FTP machine even connect to mine? I see no way for them connecting based off of the information I've read about and been given here.

look at this howto for how to setup your ftp server: [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588) it DOES include information on how to change the directory where files are shared to/from, as well as how to provide for the correct permissions so that you can read and write at your user level.

security wise, you're best off keeping your files and your ftp directory separate.  that way, your friend (or someone else) can't accidentally delete all your music.

here's some good directions on how to configure your router to forward ports: [http://portforward.com/routers.htm](http://portforward.com/routers.htm)

---

### Post by Roasted on 2008-06-15
Okay. I bounced back to using FileZilla just to keep it consistent, since I'm using FileZilla on my XP laptop to test this. Plus, call me crazy, but it seems much smoother to tinker with and make changes. But whatever.

Anyway, I set up FileZilla to use a range of 20 ports, then I logged into my router and forwarded those 20. However, the "test" for those ports still failed. It said the PORT command was tainted by my router or firewall. No firewall here.. just using a router.

I tried to connect from my laptop to the desktop anyway, and it failed.

Maybe I'm an idiot. So be it. I know FTP is simple to set up according to what I've been told, and that's all well and good. But to be point blank, I would like to get this set up. So any constructive help that can be thrown my way, I'd greatly appreciate. 

Thanks!

---

### Post by dmizer on 2008-06-15
filezilla's ftp server is for windows only.  if you want an ftp server in ubuntu, you will have to use something like proftpd.  if you set up your ubuntu computer with proftpd, your friend will be able to use filezilla in order to connect to it.

---

### Post by kevdog on 2008-06-16
Probably knew someone was going to say this, however Id definitely go for ssh, winscp for file transfers anyday over ftp, filezilla.  If you need windows only, do the cygwin/openssh server along with the winscp client.  FTP might seem at first easier (ok maybe it is), but gives you little security benefit.

---

### Post by Roasted on 2008-06-16
> **dmizer said:**
> filezilla's ftp server is for windows only.  if you want an ftp server in ubuntu, you will have to use something like proftpd.  if you set up your ubuntu computer with proftpd, your friend will be able to use filezilla in order to connect to it.

Good tip.

But I wonder why it's giving me trouble when I run the test to scan the ports I forwarded...

---

### Post by dmizer on 2008-06-17
> **Roasted said:**
> Good tip.

But I wonder why it's giving me trouble when I run the test to scan the ports I forwarded...

try looking here: [http://www.proftpd.org/localsite/Userguide/linked/x862.html](http://www.proftpd.org/localsite/Userguide/linked/x862.html)

---

