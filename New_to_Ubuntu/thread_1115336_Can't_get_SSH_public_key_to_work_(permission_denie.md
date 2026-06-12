---
title: "Can't get SSH public key to work (permission denied)"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2009-04-03
Hi!  I have pubkeyauthentication set to yes, and the id_dsa.pub concatenated with authorized_keys on the client side, but when I try to connect with SSH, I get:

Permission denied (public key)

What am I doing wrong?

Thanks in advance!

EDIT:  I can connect successfully with password authentication, but after using sftp to get the key I turned it off for security.  I did:

chmod 644 ~/.ssh/authorized_keys

are these the incorrect permissions?

---

### Post by CyberMando on 2009-04-03
The authorized_keys file needs to be on the server side (the host you are connecting to) and yo need to have an agen running client side to which youhave added your key. You should probably investigate keychain for this purpose. You might also find ssh-askpass useful.

---

### Post by pi.boy.travis on 2009-04-03
> **CyberMando said:**
> The authorized_keys file needs to be on the server side (the host you are connecting to) and yo need to have an agen running client side to which youhave added your key. You should probably investigate keychain for this purpose. You might also find ssh-askpass useful.

Thanks for the reply!

I now have ~/.ssh/authorized_keys on the server, with 644 permissions.  What do I do to get the keys working on the client side.

Please excuse my lack of knowledge.  I am a server n00b. . .  :P

---

### Post by pi.boy.travis on 2009-04-03
OK, I tried to use seahorse (Applications>Accessories>Passwords and encryption keys) but it gave the same error (Permission denied (publickey)).  I tried to imoprt the old key but it gave: Unrecognised file type:.pub.  What do I do with the key on the client side?

Thanks in advance!

---

### Post by pi.boy.travis on 2009-04-03
I figured it out.  I had to enable password authentication to create that key, then disable it. . . 

Problem solved!

---

### Post by CyberMando on 2009-04-03
What I do is
sudo aptitude install keychain
that is a utility to get an agent runningand add the envionment variables to nnumerous shells.

I then put this in my .bashrc file
***************************************************
# If keychain is running source the file to take advantage of it
if [ -e ~/.keychain/`uname -n`-sh ] ; then
    . ~/.keychain/`uname -n`-sh;
    else
    if [ -e /usr/bin/keychain ] ; then
        keychain ~/.ssh/id_rsa
        . ~/.keychain/`uname -n`-sh
    fi
fi
*******************************************
That causes each new login shell to get the agent information. Then run 
source ~/.bashrc
and it will ask you for the passphrase you added to the key. After that it should work.

You should install ssh-askpass and then when you login it will ask for you passphrase. Later you will find that when you reboot you end up with a stale key in ~/.keychain.

You can then run keychain -k all, and rm .keychain/*.

Or you can add this to /etc/rc.local
***************************************************
HOST=`hostname -s`
if [ -f /home/username/.keychain/$HOST-sh ]; then
    rm /home/username/.keychain/$HOST*
fi
*********************************************************
replace username with your username and you should be set through reboots.

---

