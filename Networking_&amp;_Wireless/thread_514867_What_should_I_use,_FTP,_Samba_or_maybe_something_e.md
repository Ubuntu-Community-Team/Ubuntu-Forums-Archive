---
title: "What should I use, FTP, Samba or maybe something else...."
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by Leonin on 2007-08-01
Hello. 
I have made a couple of posts about my troubles in the world of FTP and since I havent got my server (wich is the same computer as I use in my everyday work) working I might as well let go of the idea of having a FTP server. 
So what now.....
I work as a musician and most of the time I work at home, meaning that I have to transfer large files back and forth over the internet. I guess I will transfer files mostly to computers with windows as OS.
So my question to all of you wizards out there, what type of way should I use to transfer files?
Thank you!

Edit: I dont need a super secure way. As long as it works im happy. :)

---

### Post by kevdog on 2007-08-01
Although there is no real answer to this question, since there are many ways, you might want to provide more answers, such as "who on the other end is doing the transferring"??  Is is you, or someone you know, or is the person on the other end anonymous, or do they know anything about downloading files? Im only asking, since I probably would prefer ssh with the WinSCP (its free) client for the Windows machines, however this method requires you to know in advance who is going to download from you.  Anonymous downloading would probably be better served with ftp, or even http (web server).  The cost however anonymity however is decreased security.  SSH very secure, FTP/HTTP less so.

---

### Post by Leonin on 2007-08-01
Thank you for your reply Kevdog!
I have phonecontact with all the people that I will trasnfer files too/from, so I guess you could say I know them. 
I have been thinking of SSH too. But I havent found a guide wich explains what and how to do it and most importantly WHY I should do it. Any suggestions on links would be great.

---

### Post by kevdog on 2007-08-01
Let me try to find  how guide, but here are a few caveats

Each ssh user has to have an account on the server with a "private key/public key" or password.  Each user could in theory have their own account or you could just have one general account.  Although not difficult (not in the least), to some novice users the setup of using the key could be problematic (you just have to set it up once on the client -- basically tell WinSCP where the file private.key -- for example).  Some users get confused doing this.  I guess you could in theory default to password based authentication instead of using public/private keys if this is a problem, however again, each user/general user needs an account on the server.

SSH is probably the most secure way of doing file transfer -- all transfer is encrypted -- however it needs some form of authentication (as explained above).  Hence the server in theory needs to know about the client apriori.  With FTP this isnt a requirement, however it is far less secure -- no data encryption.  

As I was trying to suggest in the first post, it depends both on what you want to offer, and what you think your clients can work with.  SSH requires a little work to set up on the part of a client.  FTP a little less.

---

### Post by frodon on 2007-08-01
Basic FTP server setup isn't really difficult, look here if you are interested, i wrote a small FTP server guide :
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

---

### Post by Leonin on 2007-08-01
Ive tried that one and I got it to work the first time, but when I reeinstalled ubuntu and had to do it all over again it didnt work. For some reason when I try the FTP I get "connection refused", the GUI is really nice though. :)

---

### Post by frodon on 2007-08-01
Then maybe try the manual configuration, it is rock solid :)

---

### Post by Leonin on 2007-08-01
I will try to set it up again when I come home from work and post my problems in [http://ubuntuforums.org/showthread.php?t=79588]("http://ubuntuforums.org/showthread.php?t=79588").  Hopefully will there be none. 
While im at it I might as well ask what a shell is (Example: /bin/false). When I make a new user I can choose lots of different shells and I have no idea what the difference are between them.

---

### Post by frodon on 2007-08-01
The difference is just different syntax for scripting, the point with the FTP user is that he don't even need a terminal setup so this is why i set a shell which don't exist ;)

---

### Post by Leonin on 2007-08-01
Oh, thank you. 
Hmm this is starting to feel like a doublepost, but maybe you wont be to angry with me when I ask you this in this thread instead of yours. ;-)
Lets say that I want to set up accounts for three friends on my FTP. How do I do that.

---

### Post by frodon on 2007-08-01
heyhey, the usual question :P

I would say that if they access the same directories just make some different aliases for your ftpuser or maybe just use one account (duifferent users can acess the FTP server with the same usernqme qnd password and you can set that exactly to what you want thanks to a dedicated parameter).
So the short answer is use only one account if all users access the same directories it will be really easier to handle for you.

---

### Post by Leonin on 2007-08-01
Ok, thank you, :)

---

