---
title: "Passwordless SSH - did I do it right?"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by Endolith on 2008-07-07
On client machine, open two terminal windows.

**In Terminal 1:**

```
~> ssh *server* -X
*Enter password*
```

(Do it first in case you screw something up and lock yourself out, so you already have an SSH session open that you can fix it with.)

**In Terminal 2 (client):**
```

~/.ssh> ssh-keygen -t dsa
[I]<Enter> for passphrase
<Enter> for passphrase[/I]
...
Your identification has been saved in /home/*clientusername*/.ssh/id_dsa.
Your public key has been saved in /home/*clientusername*/.ssh/id_dsa.pub.
...
~/.ssh> gedit ~/.ssh/id_dsa.pub
```

(Some tutorials say DSA and some say RSA.  I'm assuming that DSA is better because it's newer.)

**Back in Terminal 1 (server):**

```
~> gedit ~/.ssh/authorized_keys
```
Copy and paste the key from one gedit window into the other, at the bottom of the list, if keys are already present.

(I initially tried copying the keys using nano, but it gave me buffer errors because the file wasn't formatted correctly.  This method worked.)

Save and close gedit, then:
```
~> chmod 600 authorized_keys
```

I did this on both machines, and can now ssh from each to the other without a password.

If I ssh from another machine to either of these, I will still need the password, right?  The keys are a machine-to-machine connection, and not a user-based thing.

If I copy the key to another machine, I can log in from that one without a password, but it would be better for security purposes to create a separate key for each machine, so I can cut one off if it gets compromised?

---

### Post by HalPomeranz on 2008-07-07
Generally speaking you did things correctly.  However, you should really be using ssh-agent instead of keys without pass phrases.  ssh-agent is a key storage program that holds onto your keys an makes them available to ssh client programs without you having to type your pass phrase all the time.  The default Ubuntu windowing environments start ssh-agent for you automatically.

You have to use the ssh-add program to stuff your keys into the memory of the ssh-agent program.  ssh-add will prompt you for your pass phrase and then load your key into ssh-agent.  From that point on you'll never have to type your pass phrase (until you log out or reboot your machine).  The advantage is that your private key is still encrypted on disk, just in case somebody gets access to your files or backups.

> **Endolith said:**
> 
If I ssh from another machine to either of these, I will still need the password, right?  The keys are a machine-to-machine connection, and not a user-based thing.


Essentially yes.  These sorts of logins only work if you're connecting from the machine where the private half of the key is stored (~/.ssh/id_{rsa,dsa}).  Some people carry their keys around with them on a USB stick or smart card so that they're not tied to a particular machine, but you have to be careful unlocking your key on an untrusted machine (like a public Internet terminal)-- somebody could have loaded malicious software to steal your key.

Personally, I've almost always got my laptop with me, so I just keep my keys there.

> **Endolith said:**
> 
If I copy the key to another machine, I can log in from that one without a password, but it would be better for security purposes to create a separate key for each machine, so I can cut one off if it gets compromised?

Correct.

---

### Post by Endolith on 2008-07-08
> **HalPomeranz said:**
> From that point on you'll never have to type your pass phrase (until you log out or reboot your machine).

So you'd still have to enter your passphrase once per session?

> The advantage is that your private key is still encrypted on disk, just in case somebody gets access to your files or backups.

If someone gets access to my files, there's really no point in keeping them from getting my key.  The key is supposed to prevent them from accessing the files.  :)

> Personally, I've almost always got my laptop with me, so I just keep my keys there.

Yeah, this is only for my two machines to connect to each other; I'd use passwords for access from other terminals.

Thanks for your help.

---

### Post by HalPomeranz on 2008-07-08
> **Endolith said:**
> So you'd still have to enter your passphrase once per session?

Right.  Once at the beginning of the session when you ssh-add your keys into the ssh-agent keystore.

> **Endolith said:**
> 
If someone gets access to my files, there's really no point in keeping them from getting my key.  The key is supposed to prevent them from accessing the files.  :)


In most cases there's usually a world of difference between getting access to your data and getting access to your login.  This is probably less true on a single-user home-type system, but is a significant distinction for my "enterprise" customers.  Sorry... my IT reflexes are  geared up for bigger environments.  :-)

---

### Post by Endolith on 2008-07-08
> **HalPomeranz said:**
> Right.  Once at the beginning of the session when you ssh-add your keys into the ssh-agent keystore.

You have to run the ssh-add command each time?  Sounds inconvenient.  I thought maybe you just had to log into the system and the desktop would start ssh-agent and take care of everything else for you.

> In most cases there's usually a world of difference between getting access to your data and getting access to your login.  This is probably less true on a single-user home-type system, but is a significant distinction for my "enterprise" customers.  Sorry... my IT reflexes are  geared up for bigger environments.  :-)

Ah, that makes sense.  For my purposes, I think the only way someone would be able to access my files would be if they already had the login.

---

