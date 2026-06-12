---
title: "FTP between Ubuntu and XP via Internet - What's the best way?"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by NEUR0M4NCER on 2009-02-19
A friend and I are working on a video project and need to keep up to date with edits - what would be the best way to set up a secure FTP through the Internet, bearing in mind he's still with XP, no matter what I say ;)

We thought about using a P2P app, but it seems a little slow for what we need, the files will be a couple of Gig...

---

### Post by theozzlives on 2009-02-19
On the Ubuntu end, I like sFTPpro, XP comes with FTP at the command prompt.

---

### Post by igknighted on 2009-02-19
> **NEUR0M4NCER said:**
> A friend and I are working on a video project and need to keep up to date with edits - what would be the best way to set up a secure FTP through the Internet, bearing in mind he's still with XP, no matter what I say ;)

We thought about using a P2P app, but it seems a little slow for what we need, the files will be a couple of Gig...

Install vsftpd (Very Secure File Transfer Protocol Daemon), and make sure the needed ports are open/forwarded to you on any firewall/router you have between you and the internet.  Then start the vsftpd service, and place the files you wish to share in /var/ftp/ and create a user for your friend to login as.

---

### Post by NEUR0M4NCER on 2009-02-19
Thanks for the reply. I had a look at sFTPpro, looks a bit... complex. I've already got gFTP installed, so that should handle that...

I guess i'm asking for a bit of hand holding, 'cause whilst I can FTP to and from my XBOX, I can't figure out how to get to the remote XP computer. And then, how would I go about setting up shared folders - I already have some stuff shared via SMB for the XBOX - would it be the same way as that?

Thanks!

---

### Post by NEUR0M4NCER on 2009-02-19
Thanks igknighted - Is there a way of sharing folders other than /var/ftp/ - some of these files are pretty big, and I was hoping to just leave them where they are, rather than move them around every time we intend to do a catch-up.

---

### Post by igknighted on 2009-02-19
> **NEUR0M4NCER said:**
> Thanks for the reply. I had a look at sFTPpro, looks a bit... complex. I've already got gFTP installed, so that should handle that...

I guess i'm asking for a bit of hand holding, 'cause whilst I can FTP to and from my XBOX, I can't figure out how to get to the remote XP computer. And then, how would I go about setting up shared folders - I already have some stuff shared via SMB for the XBOX - would it be the same way as that?

Thanks!

We would need to know a bit about your setup.

Is your computer connected directly to the internet?  It doesn't sound like it, it sounds as if there is a local network.  This is an obstacle, because at some point there must then be a router between you and the internet (assuming your friend is not on your local network).  You will need access to this router to change settings, do you have this access?  Unfortunately, every router is different in what settings you need to change.  If you know the type of router you are behind, google the name of the router and port forwarding and see what turns up.

Next you will need to know the IP of your router to the outside world.  This is pretty easy, just google search "what is my ip" or something similar, and any one of the results should tell you.  This is what your friend would type in as the address ([ftp://###.###.###.###](ftp://###.###.###.###), not [ftp://ftp.website.com](ftp://ftp.website.com)).

Finally, you really can't use Samba (SMB) because it is only designed for local networks.  You could set up a VPN (virtual private network) to get access, but this is getting rather complicated.

---

### Post by igknighted on 2009-02-19
> **NEUR0M4NCER said:**
> Thanks igknighted - Is there a way of sharing folders other than /var/ftp/ - some of these files are pretty big, and I was hoping to just leave them where they are, rather than move them around every time we intend to do a catch-up.

Yes, you can change this in a config file when you get it installed and working.

---

### Post by NEUR0M4NCER on 2009-02-19
My setup's like this:
```

Internet > Router > Desktop
                  > XBOX

```
Nothing special. I have web-based admin access to the router, and have already set up port-forwarding for another app, so that shouldn't be too hard. No, my friend isn't on the home network - his setup is basic 'Cable Modem > Desktop'. We both run our computers 24/7, and would like to be able to access the files when needed... I don't mind putting a bit of work in, if VPN is going to be the better solution.

Thanks.

---

### Post by NEUR0M4NCER on 2009-02-19
I had a look at OpenVPN - also pretty complex. I was hoping there might be a simpler solution, before I decide to wade into the sea of commands (both *nix ans MS)...

---

