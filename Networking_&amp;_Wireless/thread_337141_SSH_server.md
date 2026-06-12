---
title: "SSH server"
date: 2007-01-12
forum: Networking &amp; Wireless
---

### Post by band-aid on 2007-01-12
I want to set up a SSH server on my desktop. I already have a ubuntu desktop install on one of my hard drives but seeing as I sometimes use this for box for gaming I have not gotten rid of winblows yet. What I hope to accomplish is to be able to access this computer via ssh from my laptop wherever I happen to be. I'd like for everything to start up automatically that way when I'm done doing any games I can simply restart the computer and be confident that the timer in grub will automatically boot the server OS log me in and start everything automatically that way I don't have to babysit it through the startup process. I will have files that I want to be able to copy back and forth between my desktop and laptop on both my partitions (both windows and ubuntu). Should I use the server distribution? My reservation is that I don't want a web server or anything like that. I want just a ssh. Thanks for the help.

Band-aid


If anything in this post is impossible or blatantly wrong please feel free to let me know.

---

### Post by blackened on 2007-01-12
You don't need the server version. Just apt-get install openssh-server on the desktop, then apt-get install openssh-client on the laptop. I would suggest checking into related security issues behind this approach just to be safe.

---

### Post by band-aid on 2007-01-12
Ok I have the server up and have it set to allow me to log in with my username and password. I also have it set to a nonstandard port. I would really like to have my login based on a key that I could store along with putty on a thumbdrive for when I am using a computer other than the one I own. I would also like to be able to use the keybased method to log in from my ubuntu laptop. How would I go about doing this. I have done ssh-keygen or whatever the command is to generate the keys in ~/.ssh/ but I do not know how to make use of these keys. Thanks for the help.

Band-aid

---

