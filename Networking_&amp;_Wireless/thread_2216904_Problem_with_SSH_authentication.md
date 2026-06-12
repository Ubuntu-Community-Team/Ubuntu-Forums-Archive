---
title: "Problem with SSH authentication"
date: 2014-04-14
forum: Networking &amp; Wireless
---

### Post by gtroyp on 2014-04-14
I am using RSA keys to ssh into my home server form work. I was entering a new port for tunneling, and when prompted for the passphrase for the key, I entered the wrong one. Now, I can tunnel any other port, but not that one.

I am using a command like this: ```
ssh -p [forwarded-port] -L 9005:[host-tunneled-to]:[host-tunnelled-to-port] user@[ssh-host]
```

I am using a VM on the server to serve as the ssh-host computer, and setting up tunnels to the other VM's on the system. The [forwarded-port] is working just fine, since I can also successfully connect to the ssh-host computer using the same user@ssh-host without error.

I can use the command quoted above for <9001:host1:1>, but not for <9002:host2:2>, so I think the keys are fine, stored properly on the ssh-host computer, etc. I am specifically trying to connect to my computer running transmission on port 9091, and when setting up the tunnel for the first time, when prompted for the passphrase for the key, I pasted in the wrong passphrase.

I am connecting from my Mac, using terminal, to my Ubuntu 12.04 server. 

I think that the problem is on the Mac side, with the Mac storing the bad passphrase. But, it could be on the server side.

The error I get is : ```
ssh_exchange_identification: Connection closed by remote host
```

Any help would be most appreciated. All my googling keeps talking about setting up keys, which I have done


UPDATE: I have determined the problem is on the client Mac. It stored the passphrase for the key, somehow, specifically to that tunnel. Now I just have to figure out how to force it to ask me for the right passphrase, or to clear the bad one out (or all of them and just have to reenter for all of them)

---

### Post by Lars Noodén on 2014-04-14
-p is for the target port of the SSH connection itself, if you have it configured to anything other than the normal port 22.  The forwarding is designated with -L instead and seems to be missing above.

*-L 9005:[host-tunneled-to]:[host-tunnelled-to-port] *

---

### Post by gtroyp on 2014-04-14
Lars- You were right. I had left the "-L" out in the code cited. 

I was actually using it properly. I have updated the code above, and updated to show that the problem seems to be on the client.

---

### Post by Lars Noodén on 2014-04-15
If it's looking to use the wrong key, then try setting [IdentitiesOnly](http://manpages.ubuntu.com/manpages/trusty/en/man5/ssh_config.5.html) to "yes" either for that host in ~/.ssh/config  or using -o when you run ssh.

Or you can clear a key from the agent:

```

$ *ssh-add -l*
2048 xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx /home/user/.ssh/key_rsa (RSA)
$ *ssh-add -d /home/user/.ssh/key_rsa*

```

Or just zap them all at once.

```

$ *ssh-add -D*

```

Then reload the key.

```

$ *ssh-add /home/user/.ssh/key_rsa*

```

---

