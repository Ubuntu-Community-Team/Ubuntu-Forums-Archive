---
title: "Home Server? I think I know what I want and..."
date: 2010-05-03
forum: New to Ubuntu
---

### Post by Ranger198 on 2010-05-03
Ok,

I've been using Ubuntu desktop off and on for the last year or so while reading everything I can to self educate on Linux.  I think I'm near the point of describing myself as "knows just enough to get himself in trouble".  This is my first time posting to a forum to seek wisdom!

Situation is that I have numerous family members located all over the world at any given point, sometimes in places that restrict content.

Endstate that I'm shooting for is the following:

A home server,non-public, configured to work through a commercial, domestic ISP, that does the following:

Photo Management - ideally with F-spot

Secure video messaging/conferencing/chat - ideally with empathy

Stream video content from the server (home movies) - which I think I accomplish via html and a plugin.

VPN connection to allow  one of my family members overseas to connect to a US television networks web page and view streaming content that would otherwise be blocked. 

Given/ despite all this, I'm thinking what I probably need to do is use an Ubuntu desktop edition and then restrict user permissions on a virtual/remote desktop?  In other words, essentially let them access the "server" as if they were working on their personal computer?

Most of my family is non-tech savvy so I need to make building a common repository of family pictures, videos, and hopefully US level internet access as easy and secure as possible.  Oh yeah, they're all using Macs or Windows PCs.

Like I said, I'm pretty new to Linux and know just enough of a little here and there to be dangerous to myself and others!  

Looking for thoughts/ guidance / sanity check on how to go about this.  I'm also VERY open to "I think what you really meant to say was..."

Thanks

---

### Post by bdentremont on 2010-05-03
Ranger198:
Welcome to the Ubuntu forums!  I'll give you what answer I can and hopefully others will give some advise on this as well.

I jumped into running a home server a few years ago which hosts my web site [www.dentremont.us](www.dentremont.us).  I also use this to store personal files and run web applications that I and my family use.  I now also use Ubuntu desktop edition as a OS on my laptop and primary computer.  My server is an old laptop with a broken monitor which I run headless (no monitor or keyboard).  I've installed Ubuntu server edition (no X11) on this. My goals were a little different than yours, but I'll tell you where I'd go with your objectives given my limited experience.

VPN (web access from foreign countries):
Getting Linux setup with SSH accessible from the outside world may prove a viable substitute for full VPN if you are just trying to redirect the origin of your user's web access and secure file transfers home.  Via port forwarding you can use your SSH connection as a SOCKS proxy for your web browser.  I.e., after issuing "ssh -D 9000 www.dentremont.us" on a Mac or Linux system, I can set Firefox to connect via SOCKS proxy on port 9000.  Putty can be used to execute the same from Windows.  Setting up a Firefox profile with the proxy enabled on the client system, you could get an encrypted connection that appears to originate from your server's location with a couple clicks of the mouse (one for the SSH connection, one for the browser).  In other words, the connection is encrypted back to the server and the website that my computer is communicating with sees the connection as having originated at the server.  This may be all you need.  SSH also serves as an encrypted file transfer protocol.  From Win, Mac, or Linux, your users could use Filezilla to store and manipulate files securely on your server via SSH.

Photo management:
You can setup the photo management as a web service.  Setting up an Ubuntu LAMP server (Linux, Apache, MySQL, PHP) you could then run a PHP web application like Gallery ([http://gallery.menalto.com/](http://gallery.menalto.com/)) and restrict the visibility of photos only to those with an account.  If you want the content and authentication of the connection encrypted, restrict it to https connections in Apache and configure your server with a free certificate from CAcert.com or a self signed certificate.  Each of your users will have to manually install the root certificate associated with that, but after that your site will be accessible like any other https website.  The whole thing is easier said than done, but doable and very satisfying to tinker with.

Video streaming:
I've not done this, but getting the LAMP configuration up and running would be a necessary start.  Keep in mind that most home connections, at least in the U.S. are highly asymmetrical and support much higher download than upload.  You may have difficulty streaming video from your house.  

Chat/Voice/Conferencing:
I and my family use Skype and I'd suggest Skype or one of the more open alternatives rather than anything setup from home.  Skype is already encrypted and I don't see any advantage to getting the home server involved, particularly given the potential connection asymmetry problem mentioned above which could present problems relaying videos.

In short, if I were you, I'd aim at getting a LAMP server setup with SSH and make sure that SSH, HTTP, and (optionally) HTTPS were accessible through your firewall. From there, you should have a lot of options for each of your particular goals.  If you are in the "know enough to be dangerous" phase, I suspect that will take you a bit of time and entail some reasonable education in the workings of Linux, networking, and encryption to get that far.

Good luck!

---

### Post by Ranger198 on 2010-05-04
Thanks alot!  I think that may be exactly "what I meant to say".

I'll give it a shot and some tinkering and come back if I get stuck!

Thanks again.

---

