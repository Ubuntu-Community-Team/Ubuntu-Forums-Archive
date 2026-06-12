---
title: "openSSH - new keys ?"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by MrEgg on 2008-05-16
Following the recent openSSH update due to security issues, I'd like to create a net set of keys for all the computers on my network. How can I safely remove the existing keys? How can I transfer the newly generated key to the other computers (via a USB key)? Could you recommend an how-to?

TIA,
Egg

---

### Post by SpaceTeddy on 2008-05-16
if you have the updates on the computers, there is no need to create the keys on one computer and carry them around. Acctually, since you just isse the commands and the keys NEVER cross the line, you can even generate them remotely from your computer via the old ssh keys. Even if someone is listening in they cannot see the keys, as they are NEVER send :)
Also, the keys are used to identify the server. They are afaik NOT used for handling the encryption (async encryption is way too slow for a regular transmission protocoll). So you data will still be protected. That is, if i understood the whole concept right. If i am wrong, correct me :)

So, what you need to do is go into the /etc/ssh folder and remove all files that are named ssh_host_*

Option 1.) create the keys manually with these commands
```
sudo ssh-keygen -t dsa -f /etc/ssh/ssh_host_dsa_key
sudo ssh-keygen -b 2048 -t rsa -f /etc/ssh/ssh_host_rsa_key
```

and then restart your openssh-server with
```
sudo /etc/init.d/ssh restart
```

Option 2.)
run this command which will do all the above by itself.
```
sudo dpkg-reconfigure openssh-server
```

voila, there are your new keys. Just make sure you delete the old keys from your own known_hosts, or you won't be able tio log in again.

BTW, while you regenrate and restart the ssh server, the current console stays open **even you restart the ssh server**. So make sure you can login again before you close the last console to the server. If you close that one and cannot log in - happy walking to the server itself :)

hope it helps.

---

### Post by MrEgg on 2008-05-17
Thanks very much, SpaceTeddy. Now, when I first created the keys a while back ago, I add to somehow transfer the public keys from the local ~/.ssh/id_dsa.pub to the remote authorized_keys. I used the command ```
ssh-copy-id -i ~/.ssh/id_dsa.pub remote_server01
```

Let's suppose I can't connect to remote_server01 and that I'm ready to go to it, physically. For my info, how do you manually copy/paste the public key to it? Should I just copy the local ~/.ssh/id_dsa.pub to the server's authorized_keys, using vi/gedit? Or is there a more specific procedure?

Thanks,
Egg

---

### Post by SpaceTeddy on 2008-05-17
take the id_rsa.pub key with you to the remote server. Open the file /home/%user/.ssh/authorized_keys (the %user is the user you want to log into as) and simply copy the one line from your id_rsa.pub into the autorized keys. Just a new line there... tho you might want to remove the old one :)

that's pretty much it. 
btw - the pub is the public key. Anybody can read that as much as they want. So you can transfer that one over an unencrypted line that "bad" people are listening into :)

---

### Post by MrEgg on 2008-05-17
hmmm... I chose Option 1, for the sake of the exercise :) Now, key creation went fine both times, I entered my passphrase and got a fingerprint for each key. My problem is that as I restarted ssh (sudo /etc/init.d/ssh restart), I got the following messages :

Could not load host key: /etc/ssh/ssh_host_dsa_key
Could not load host key: /etc/ssh/ssh_host_rsa_key

I checked /etc/ssh, the keys are there, both with 600 permission. I'm kinda stuck, here :-k ; and, maybe this is due to the process not being completed, but my %h/.ssh/id_dsa.pub hasn't been modified either (well, it still has an old time stamp at least).

Why won't my host keys load as I restart ssh? Any idea?

---

