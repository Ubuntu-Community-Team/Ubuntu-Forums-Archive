---
title: "Help with Samba?"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by stevepoppers on 2009-08-23
I've got Ubuntu 9.02 Server Edition connected to my network and the internet. I want to be able to access it like a shared folder from Windows Vista on my laptop. Locally at the very least. Remotely if possible.

I've been trying Samba, but the configuration has me tearing my hair out.

Help?

---

### Post by inobe on 2009-08-23
setting up samba is pretty easy

heres help from community docs.

remember 'USERNAME" is your actual username !

the password to access the shares must be different from login password.

[https://help.ubuntu.com/8.10/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/8.10/serverguide/C/samba-fileserver.html)


may i ask what you have tried and how far you got ?

here's more

[http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)

---

### Post by inobe on 2009-08-23
to add

[http://www.youtube.com/watch?v=d2129OLrY8M&feature=related](http://www.youtube.com/watch?v=d2129OLrY8M&feature=related)

---

### Post by stevepoppers on 2009-08-23
That first link looks like it's going to help a bunch. I'll try it later and let you know how it goes.

The stuff I was finding in google just wasn't clear enough. Guess I should search the documentation better.

Thank you.

---

### Post by stevepoppers on 2009-08-24
Well, after  following just the directions in the first link, it's working. Thanks very much.

Should I go through all the other stuff in the other links too?

It looks like I may have done something wrong, though. Initially, it showed up in windows as my username, instead of the computer name (server1). I commented out the netbios name (probably one of the things enabled before I asked for help here), and now it shows up as both my username and server1, but only server1 works (which is what I want, but why's my username still showing up?).

---

### Post by Thelasko on 2009-08-24
```
sudo apt-get install system-config-samba
```
or if you are like me and don't like the command line, go to the synaptic package manager and install the system-config-samba package.  This will install a nice little GUI you can use to easily administer your Samba shares with.  Once it's installed you can find it under system>administration.

---

### Post by stevepoppers on 2009-08-25
Well, it looks like that won't be necessary as it's no longer showing up as the username, just server1, as it should be. Seems like one of those funky things that just needs time to resolve itself. Thanks, guys.

---

