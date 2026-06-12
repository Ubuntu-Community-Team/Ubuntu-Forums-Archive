---
title: "Empathy &quot;People nearby&quot; account"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by J V on 2010-04-19
What does this do? Search for others in local network ala smb?

---

### Post by BugBuster on 2010-04-19
The "people nearby" feature uses the avahi-daemon and the Bonjour protocol to find users on the local network and setup chat between them.

For example if you have two pc's on a lan and they both have avahi-daemon running.
Then on pc1 if you setup a bonjour account using pidgin/empathy, say user1@hostname1 and the other pc as [email]user2@hostname2..then[/email] you can chat locally without need for an internet connection. That is how I have used it. Basically its very simple and effective way of doing intranet chat.

Thats my couple of cents..thanks.

---

### Post by J V on 2010-04-19
Setup an account? Is it ok if I just have it enabled?

---

### Post by LowSky on 2010-04-19
it not a really an account, bugbuster was using normal IM protocol.

Basically just create a name and it should work from there, as long as two or more computers on the same network are using the same application it will work. You do need someone to talk to, LOL

Its fine to have it just running its not taking up any network or computer space really. Its basically AIM or MSN on a local network

hopefully that makes better sense of it

---

### Post by J V on 2010-04-19
Thanks :)

Any way to use it externally? File transfer on mainstream IM services is slow and they get all your data...

---

### Post by LowSky on 2010-04-19
Maybe using a VPN client

But a better option is using torrents or a FTP server

---

### Post by J V on 2010-04-19
How do you IM via FTP?

---

### Post by LowSky on 2010-04-19
> **J V said:**
> How do you IM via FTP?

LOL my bad, sorry you don't. I meant to say set up a FTP web server and just give the IP address (via IM if you like, LOL) to whomever needs the file.

If I were you use BitTorrent (or Transmission, Ubuntu's default)to send the files. It a much better approach. And wont require you to open ports on your network

It will create a seed file, which you will need to email or IM to a friend and then they can download the app from you.

---

### Post by J V on 2010-04-19
I didn't know you could torrent without a tracker... Nice!

Are you sure you don't need to open ports? On either computer?

---

### Post by LowSky on 2010-04-19
nope you shouldn't

---

### Post by J V on 2010-04-19
Thanks :) [SOLVED]

---

### Post by holden448mex on 2010-07-05
Hello, Lowsky and everyone 

I am completely stunned, how does Empathy find people nearby?? 

This is something I have never seen in Windows so far.

My two computers connect to a switch, my ISP provides me with two ip addresses so I don't need a router or a LAN to access Internet, only switch and modem.

The connection information for the two Ubuntu computers is COMPLETELY DIFFERENT, no equal default gateway, no private ip address, we only share the same subnet mask, so how does Empathy find the other computer so well??!!

---

