---
title: "Server"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by PaddyMullaney on 2010-06-01
Hello

I currently run a small windows work group (10 users), and have got to the point where I think I need to consider switching to to centrally managed network.

I have not used Ubuntu before, and have used windows quite a lot (though not as a network manger, more usually DBA, and back in NT4 days as support user).

The cost of MS windows puts me off, so I am looking at Ubuntu. 
When I last used linux, I found it quite tricky.

What I am essentially looking for are starter guides or advice regarding the server edition, and whether people are happily using it in production? Any comments are welcome.

Paddy

---

### Post by Temposs on 2010-06-01
If you find using the command line tricky, you might try just installing the desktop version and using it as a server. It's quite simple to do that, and it would be a good way to transition away from Windows. You would be able to install all of the server-related software from the desktop edition.

---

### Post by Neezer on 2010-06-01
> **PaddyMullaney said:**
> Hello

I currently run a small windows work group (10 users), and have got to the point where I think I need to consider switching to to centrally managed network.

I have not used Ubuntu before, and have used windows quite a lot (though not as a network manger, more usually DBA, and back in NT4 days as support user).

The cost of MS windows puts me off, so I am looking at Ubuntu. 
When I last used linux, I found it quite tricky.

What I am essentially looking for are starter guides or advice regarding the server edition, and whether people are happily using it in production? Any comments are welcome.

Paddy

I have used Ubuntu Server in the past and it worked ok. I upgraded to a RAID card to run RAID 1 on the server and 9.10 server edition didn't recognize the RAID card. It was a big pain in the rear so I went to 9.10 desktop edition which recognized the raid card off the bat and just installed the LAMP stack etc.

That being said, I am now running ClearOS on my server at home. picked up the RAID card right away, and has a very nice interface that is accessable from the internet.

Right now I have it running a webpage, SSH server, SFTP, Media Server (Mediatomb), and a few others. It is working great right now and its been running for over a month now. 

I experimented with using it as a gateway, but I was having problems getting my wireless router to work properly with it.

Anyways, enough with the babble. Here is the website for it if you want to check it out.

[http://www.clearfoundation.com/](http://www.clearfoundation.com/)

good luck. hope this helped

---

### Post by PaddyMullaney on 2010-06-03
Thanks, I will look into both those suggestions.

Paddy

---

### Post by mastablasta on 2010-06-03
I would start here: [http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)
 
With ubuntu pocket guide just to familiarize wiht the system if you never used it before. A lot of commands are similar to DOS/win commands but a lot are very different and ti also works in a differnt way. as someone noted it would be best (for start) to install desktop and then jsut add more server features to it.
 
for server edition i think it's mostly command line oriented. but you can again install desktop there as well (if you are more of a GUI person).

---

