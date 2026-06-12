---
title: "Error message appearing when upgrading"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by vanhornd on 2009-12-10
Hello all,
 When I execute 'Update Manager', there is a portion at the top that says: "New distribution release '9.10' is available". When I push the 'Upgrade' button, unsurprising windows appear that end in this error: "W:Failed to fetch [http://security.ubuntu.com/ubuntu/di...curity/Release]("http://security.ubuntu.com/ubuntu/dists/karmic-security/Release")  Unable to find expected entry  m/source/Sources  in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

Can you provide some guidance?  As you probably can tell, I'm very new to Ubuntu.

Thank you, Doug

---

### Post by jbrown96 on 2009-12-10
Are you connected to the internet? This is usually caused by a bad connection.

---

### Post by Geoff918 on 2009-12-10
Are you able to connect to that link manually? (In other words, is it being resolved correctly?)

I accessed the link fine, so the server is working. As to whether there are any problems with the MD5SUMS, of that I'm not sure.

Are you having any sort of packets dropped? Are you on a wireless connection that might be losing connection?

Are you behind any kind of firewall, or proxy?

---

### Post by vanhornd on 2009-12-14
Thank you folks for your replies-

My router is a Linksys **WRT610N**. I connected to it with a cable connection through my laptop computer's ethernet port.  Then I disabled the SPI firewall and saved the configuration.  When I accessed the link manually ([http://security.ubuntu.com/ubuntu/di...curity/Release]("http://security.ubuntu.com/ubuntu/dists/karmic-security/Release")), it was fine.  Then I attempted to upgrade again; I got the same error message as I initially received.

This is frustrating for me!  Any thoughts . . .

Thanks again, Doug

---

### Post by lotharmat on 2009-12-14
> **vanhornd said:**
> Hello all,
 When I execute 'Update Manager', there is a portion at the top that says: "New distribution release '9.10' is available". When I push the 'Upgrade' button, unsurprising windows appear that end in this error: "W:Failed to fetch [http://security.ubuntu.com/ubuntu/di...curity/Release]("http://security.ubuntu.com/ubuntu/dists/karmic-security/Release")  Unable to find expected entry  m/source/Sources  in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

Can you provide some guidance?  As you probably can tell, I'm very new to Ubuntu.

Thank you, Doug

What happens when you type 
```
sudo apt-get update
```
and then
```
sudo apt-get dist-upgrade
```

in a terminal

---

### Post by vanhornd on 2009-12-14
In a terminal running:

sudo apt-get update

results in:  

many lines some are hits and some are igns.  An example of ign lines:
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US

In fact I notice that all the Ign's end with the suffixes above (Translation-en_US)

None of the Hit's have that suffix.

At the end is my error message:  'W:  Failed to fetch http:// . . .'

Any clues here?  Thanks Doug

---

### Post by vanhornd on 2009-12-14
Even if I'm doing something stupid here, I would like to know about it so I could stop doing it.

:-)  Doug

---

### Post by vanhornd on 2009-12-16
Hello!  Anybody still interested in solving my problem?  Any ideas, anyone . . . anyone . . .

---

