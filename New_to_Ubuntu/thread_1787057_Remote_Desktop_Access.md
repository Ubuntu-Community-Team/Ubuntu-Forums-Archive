---
title: "Remote Desktop Access"
date: 2011-06-20
forum: New to Ubuntu
---

### Post by KyleRickards on 2011-06-20
Hi all

Is there an easy guide anywhere (like Dummies level!) to get me working with remote access between two ubuntu machines? I would like to be able to connect to my other half's machine, over the internet to fix problems, much like I used to using MSN Messenger when we both had windows.  I have googled repeatedly but cannot understand a simple way of doing it or how to set up VNC :(

Also, we tried Empathy - my 'Share My Desktop' is greyed out but when she clicks my name, it's an option but clicking it gives the message that I have rejected it, when I didn't even get asked.

Thanks in advance
Kyle

---

### Post by bodhi.zazen on 2011-06-20
VNC is extremely insecure and the most common crack we see on these forms.

The "proper" way to remote manage a server / desktop is with ssh (comman line only).

You can forward graphical applications with ssh -X

If you must use VNC, tunnel it over ssh or use FreeNX.

You have to forward ports from your router.

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

If you tunnel over ssh, use keys and disable passwords. If you tunnel over ssh, then you only need to forward port 22.

Other then that, find a tutorial, and tell us what step you do not understand.

---

### Post by KyleRickards on 2011-06-20
Thanks - I looked at that guide and don't understand it? Green network?

Sorry :(

---

### Post by _0R10N on 2011-06-20
All ubuntu installations are bundled with Vinagre, a client for viewing remote desktops via vnc protocol. So, if you want to access a remote desktop, a server, you must install a VNC server application on that PC. I used vnc4server for quite long, but a while ago I discovered that x11vnc is a way better.

Here I leave some good links to use as a howto:

[http://www.karlrunge.com/x11vnc/]("http://www.karlrunge.com/x11vnc/")

[http://ubuntuforums.org/showthread.php?t=45565]("http://ubuntuforums.org/showthread.php?t=45565")

---

### Post by KyleRickards on 2011-06-20
Thanks, I will give that a go.

Kyle

---

### Post by bodhi.zazen on 2011-06-20
> **KyleRickards said:**
> Thanks - I looked at that guide and don't understand it? Green network?

Sorry :(

What part do you not understand ?

Otherwise it is almost impossible to help you.

[http://portforward.com/help/portforwarding.htm](http://portforward.com/help/portforwarding.htm)

---

### Post by nymusicman on 2011-07-24
May I suggest for the extremely friendly that you use teamviewer. It's so simple and great, I don't even have to explain it.

---

### Post by HermanAB on 2011-07-24
Please read Bhodi's post again.  DON'T use VNC.  You'll be sorry if you do.

---

### Post by sadaruwan12 on 2011-07-24
Yeah, If you don't understand how to do SSH the bodhi has toled you and you don't mind much about security use teamviewer.

It's simple just download and install in both or all the PC's and you're good to go.

---

### Post by bodhi.zazen on 2011-07-24
> **nymusicman said:**
> May I suggest for the extremely friendly that you use teamviewer. It's so simple and great, I don't even have to explain it.

Just know that "easy" and "secure" are often at odds.

If you must use VNC, please tunnel it over ssh (secure but slow) or use FreeNX (secure and fast).

Yes, I understand there is a bit of a learning curve, but, as noted VNC is not the best option over the internet (it is "OK" on a private LAN).

---

### Post by nymusicman on 2011-08-14
I do understand that usually easy and secure are at odds. I was not aware that teamviewer was based on the vnc protocol otherwise I would have never used it myself. I do like that the software always changes the way you log into the other machine and that you don't have to send usernames or passwords over the LAN/internet, whatever your using.

For security and on my own server, I do use the proprietary Nomachine's NX (mostly because FreeNX last time I checked was not compatible with the portable version I use on my flash drive). So I do recommend that for security. But, I have a few people (using both windows and linux) who once in a blue moon I have to remote connect to their computers. Typically they do not know how to send me their IP Address and it's too "confusing" for them to figure it out. They are already logged on to their computers so no password is send from me to their computer and in these situations, I find teamviewers logon the best. They can tell me what is on their screen, I put in that temporary password and I'm in. Do the job, I'm out. All clients and servers are shutdown and the single is closed. Nothing open in the background. No messing around with opening ports. It's done. And we are both just as secure as before we started. That's why I recommend teamviewer at all.

I would really like to know if Teamviewer has any major flaws so I know to stop using it. This could just be marketing but from their website:
	
> Encryption

TeamViewer includes full encryption, based on RSA private-/public key exchange and AES (256 Bit) session encoding. This technology is based on the same standards as https/SSL and is considered completely safe by today's standards.

The key exchange also guarantees a full client-to-client data protection. This means that even our routing servers will not be able to read the data stream.

Just opening vnc's ports on my mother's computer loaded it with viruses. You can't put FreeNX on a windows machine and I'm not sure (if you even can) how to send a windows desktop over ssh. So unless someone could suggest a remote connection other than vnc without a lot of complication for the user that is as secure as ssh, teamviewer seems to me to be my only option.

Sorry for the rant.

---

