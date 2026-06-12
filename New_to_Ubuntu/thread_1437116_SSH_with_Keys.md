---
title: "SSH with Keys"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by EnigmaticCoder on 2010-03-23
I'm relatively new to SSH, so I followed [this]("http://www.g-loaded.eu/2005/11/10/ssh-with-keys/") guide to set it up to use DSA keys. I followed it step by step until it directed me to test it out. When I tested it out, I couldn't log in, and it eventually said that I had failed to many authorizations. Since I couldn't figure out how to reset the authorizations, I decided to comment out MaxAuthTries. Then, I tried to login over the network. Now it says **"Permission denied (publickey)"**. Any ideas?

(Further info:
- I ran chmod 600 on the files in .svn on client and server
- I ran chmod 700 on the .svn directories
- I tried several different key pairs
- I restarted ssh several times by rebooting and the command /etc/init.d/ssh restart)

---

### Post by bodhi.zazen on 2010-03-23
What ssh command are you running ?

Can you post the output of 

```
ssh -vv user@server
```

You may need to simply specify the ssh key. Where did you put it ? The default location for the key is ~/.ssh

```
ssh -vv user@server -i ~/.ssh/id_dsa
```

---

### Post by EnigmaticCoder on 2010-03-23
I've narrowed down the problem. As per the first tutorial, I had this line in my config: AllowGroups sshusers. When I comment out that line, it works fine. If you still want me to switch back and print out the verbose message, I will.

EDIT: I've decided I don't want to make an extra user for SSH anyway, so I'm marking this thread as solved.

---

