---
title: "Reverse SSH: Permission denied, please try again."
date: 2014-02-03
forum: Networking &amp; Wireless
---

### Post by khurtsiya on 2014-02-03
I have home laptop on 3G - **client**
I have sisters laptop on Wi-Fi router - **target**
I have dedicated server - **middle**

All on Ubuntu

I created tunnel from **target** to **middle**

```
ssh -R 7778:localhost:22 middleuser@middleIP
```

Then I connect to **middle** from **client**

```
ssh middleuser@middleIP
```

And from it to **target**

```
ssh targetuser@localhost -p 7778
```

But here I receive this errror: Permission denied, please try again.

I actually already have success connections today, but then I broke smth...

Please help where to look first?

TIA

---

### Post by The Cog on 2014-02-03
I think only root is allowed to tunnel privileged ports (under 1024). So you may need to ssh in as root@middleIp.

---

### Post by khurtsiya on 2014-02-04
But I've had success logins with this users...

---

### Post by Lars Noodén on 2014-02-04
> **khurtsiya said:**
> I have home laptop on 3G - **client**
I have sisters laptop on Wi-Fi router - **target**
I have dedicated server - **middle**


If you connect from *client* to *target* via *middle* you can do it like this:

```

ssh -L 7778:target:22 middle

```

Then on *client* you can connect to port 7778 on the localhost.  Or are you trying to make it so  *target* can log into *client*?

---

### Post by khurtsiya on 2014-02-04
I've changed the port to 7779 and all works now!

Now I want automate. But tunnel works only if terminal not closed, why?

---

### Post by Lars Noodén on 2014-02-04
Try adding [-fN](http://htmanpages.ubuntu.com/manpages/saucy/en/man1/ssh.1.html) to your options on the client when establishing the port forwarding.  The **-f** drops ssh to the background and the **-N** tells it not to execute a remote command.

---

### Post by khurtsiya on 2014-02-04
when I add -fN and try to run it by clicking and selecting Run - nothing happens and I am not able to connect from middle - Connection refused - so I believe reverse tunnel not created

---

### Post by Lars Noodén on 2014-02-04
What happens when you run it from the terminal?  What is the full line that you enter?

---

### Post by khurtsiya on 2014-02-04
When I run this from terminal I've god prompt: middleuser@middleserver:~$
> sshpass -p password ssh -R 7779:localhost:22 middleuser@middleIP
and after this I can connect from client
but if I type exit followed by Enter key - I've got "logout" and it logs out when I close connection on client side
if i close terminal - connection closes on client side

---

### Post by Lars Noodén on 2014-02-04
Adding -fN like this should allow it to stay running after the terminal is closed:

```

sshpass -p password ssh -fNR 7779:localhost:22 middleuser@middleIP

```

---

### Post by khurtsiya on 2014-02-05
that worked THANKS!!!

---

### Post by Lars Noodén on 2014-02-05
Great.  How about that [sshpass](http://manpages.ubuntu.com/manpages/saucy/en/man1/sshpass.1.html) though?  It looks insecure and the manual page even mentions it.  Can you see the password using [ps](http://manpages.ubuntu.com/manpages/trusty/en/man1/ps.1posix.html)?

```

ps ux | grep ssh

```

If so, you might want to use keys.  You can still automate key use while retaining a strong passphrase if you use the system's ssh agent.

---

### Post by khurtsiya on 2014-02-05
no, i do not see password

but I need sshpass because target script should make tunnel automatically

is it safer to use autossh?

---

### Post by Lars Noodén on 2014-02-05
Keys can provide automatic login and the specific key can be locked down on the server side.  On in the server's *~/.ssh/authorized_keys* file, prepend the particular key with *command=*

```

command="/bin/true" ssh-rsa AAAAB3NzaC1yc2EAAAADAQAB...

```

Then that key can only be used with the -fN option.

---

### Post by khurtsiya on 2014-02-05
but keys also has passwords, don't they?

---

### Post by Lars Noodén on 2014-02-05
Keys have passphrases to decrypt the key, unless you leave them off.  It's recommended to make the keys with passphrases.  If you leave the passphrase off, then locking down the key / account is necessary and the keys should be replaced just like when you change the password.  

You can use an agent to manage the key's passphrase, that gives you automated access but still requires the passphrase.  However, because of the agent, you only have to manually enter the passphrase once when the key is loaded into the agent.  That capability is built into the regular Ubuntu desktop session.  However, it's still doable for a standalone script.  The script just needs to be aware of which socket the agent is using, this is usually passed in a variable.

---

### Post by Lars Noodén on 2014-02-05
Looking at the risks with a single-purpose key, even without a passphrase, if it is stolen it can only be used to create a tunnel.  If the sshpass script's password is captured, then a full SSH session can be made.

---

