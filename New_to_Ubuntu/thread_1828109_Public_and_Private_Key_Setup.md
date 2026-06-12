---
title: "Public and Private Key Setup"
date: 2011-08-18
forum: New to Ubuntu
---

### Post by Brad_J on 2011-08-18
So, I have a question and I can't seem to find anything online that will explain it well enough for me to get it working. I have an http web server at home that I've been slowly working on for a while, and, besides a few quirks, I have most things at least functioning. For security and learning reasons, I'd like to learn to set up ssh keys.

I have password protected ssh working, but I'd like to set up private and public keys, and I have no idea how to do that. I've generated the keys and set the permissions of ~/.ssh to 700, but it still is only password protected and I have no idea why. I've searched tutorials for setting up ssh keys a bunch of times, but it always comes to a point where I need to put the public key in the authorized keys folder and since I am usually using ssh through puTTy on my work Windows machine, I don't have that. 

Even if I don't copy the public key over to my Windows machine, it should still have the key activated, so I should be locked out, right? I must be doing something wrong somewhere, but I really don't know where. Help please!

I hope this all makes sense, if you need any more information feel free to ask for clarification or any relevant output. Thanks for your time.

-Brad

---

### Post by matt_symes on 2011-08-18
Hi

I have had a long day so i need to clarify this.

The Linux box is your SSH server and your windows box is your sshSSH client running PuTTY ?

Kind regards

---

### Post by Brad_J on 2011-08-18
That is correct

---

### Post by bodhi.zazen on 2011-08-18
You have to import the openssh keys to putty.

Use Keygen

[http://jason.sharonandjason.com/key_based_putty_logins_mini_how_to.htm](http://jason.sharonandjason.com/key_based_putty_logins_mini_how_to.htm)

---

### Post by Brad_J on 2011-08-18
Thank you for the super fast replies! I have a question, though: where it says "...your public key and should be placed in the ~/.ssh/authorized_keys file for every computer you would like to log in to with this private key." does it mean that I'm saving it to the linux server or the windows machine? If linux server, does that mean that I have to make a new public key for every computer that I want to authorize to access the linux server through ssh? This is the point I get confused at most times, because if it's the Windows machine, which is what I interpret it to mean, where would I save it?

---

### Post by bodhi.zazen on 2011-08-18
When you make a key, there are two files, the public and the private key.

The public key goes on the SERVER in ~/.ssh/authorized_keys

The private key is used on the Windows client. You can use the private key on any client and in fact many people carry putty and a set of keys on a USB.

[http://bodhizazen.net/Tutorials/SSH_keys](http://bodhizazen.net/Tutorials/SSH_keys)

---

### Post by Tamalin on 2011-08-18
Copy the public key (the one that ends in .pub probably), and append it to the ~/.ssh/authorized_keys file on your linux server:
```
cat path_to_public_key_file.pub >> ~/.ssh/authorized_keys
```
You will also need the private key on your Windows computer, with puTTy.

Also, check that you have the correct settings in /etc/ssh/sshd_config:

The "PubkeyAuthentication" setting should be set to yes:
```

...
RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys
...

```

If you change the settings, run
```
sudo service ssh restart
```

---

### Post by Brad_J on 2011-08-19
Awesome! It took me a while to figure out what I was doing wrong, but it turned out to just be me overlooking puttygen as required for my key to work. I seem to always to rush through instructions and miss important things, oh well, works now.

A few more questions if anyone can answer them: is it possible for me to copy files from my server to a Windows machine through putty? I had a lot of trouble with this and ended up just giving up and waiting until I got home to use my flash drive; I really don't understand how to properly use scp and I'm not entirely sure it even works with something like putty. Also, I now have the key working, but I can still log in whenever I feel like with just a password kind of defeating the purpose; how do I make it so my server only allows key-based logins? Thank you to everyone who helped, your replies were super quick and I honestly didn't expect to get it working so soon.

-Brad

---

### Post by bodhi.zazen on 2011-08-19
To transfer files , use winscp

---

### Post by Brad_J on 2011-08-19
> **bodhi.zazen said:**
> To transfer files , use winscp
Cool, I think it works, but my server crashed shortly after connecting through winscp. Hopefully it is unrelated, but I'll have to check again when I get home. Thanks again.

---

