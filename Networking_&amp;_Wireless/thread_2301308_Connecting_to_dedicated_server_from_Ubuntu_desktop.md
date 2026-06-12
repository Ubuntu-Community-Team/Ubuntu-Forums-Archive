---
title: "Connecting to dedicated server from Ubuntu desktop"
date: 2015-11-01
forum: Networking &amp; Wireless
---

### Post by brian102 on 2015-11-01
Hey everyone,  I recently installed the newest Ubuntu.15 and I also run a company Web site on my dedicated server.  I know there is a easy Way to connect to my dedicated server but for the life of me I can't. Get Ubuntu to ssh into my server.  I keep getting a error saying no pub key and a bunch of letters.  
I also figured nautilus would be able to view. The files on my dedicated server in the connect to network option.  
I have two public keys,  ones m ly server made when iI first got the server.  Well I couldn't figure out where to put the private key on my desktop,  iI read that they go in etc/sshAuth keys file but that didn't work.  Every time I connected via ssh it said no pub key,  
So iI decided to make the ssh keys onUbuntu side and import them into the server.  Well it got the public one imported because I was able to open the public key in etc/ssh and copy and paste the key.  But when I tried to do the private key,  I couldn't. Open the file to see the key.  So im at a stand still.  Was hoping somone could point me in the correct direction. 
I tried to read tuts on this but in them iIalways. Got confused to What file system they refer to the server or my pc.  Anyway thanks in advance.

---

### Post by Lars Noodén on 2015-11-01
Welcome.  

The public key goes on the server.  The private key stays on your desktop machine.  There should be a hidden directory ~/.ssh/ in your home directory.  That's probably the best place to put your SSH keys, but each one in its own separate file.  

The files on the desktop machine *authorized_keys* and *known_hosts* are used for other purposes and should be left alone for now.  On the server, *authorized_keys* should contain your public key(s).

---

### Post by brian102 on 2015-11-01
ok I just did that put the correct keys into the folder and now i get 
Agent admitted failure to sign using the key.
Permission denied (publickey,gssapi-keyex,gssapi-with-mic).

I want to del that key and make a new one but if I make another one put it in the file and double click the key so it says import. Enter PW and it puts the key in. Well I did this for a few other keys when trying to work this out. Will adding a new key over write the old one or will i need to manually del the old key that was imported somewhere.

update. I just found that ssh-add will fix that.. Stay tunned

---

### Post by brian102 on 2015-11-01
and im in, now for the fun, Ok Now that I have a connection arent I able to use nautilus to get a GUI interface?

---

### Post by Lars Noodén on 2015-11-02
You should be able to use Nautilus.  Press ctrl-L to enter the location of the target server.  Then enter the URL:

sftp://someuser@server.example.com/some/path/

---

