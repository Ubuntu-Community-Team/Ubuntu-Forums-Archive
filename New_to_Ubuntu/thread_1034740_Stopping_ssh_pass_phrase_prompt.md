---
title: "Stopping ssh pass phrase prompt"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by expatCM on 2009-01-09
I would like to automate ssh so that it does not prompt for anything at all in connecting to the server.

To begin with ssh worked but before I could use it I got a window asking for the gnome-keyring password. After the password was entered it automatically connected.

I stopped that by opening gconf-editor, apps/gnome-keyring/daemon-components and unchecking ssh.

Fine.  But what happens now is that when I ssh serverIP I am prompted for the pass phrase. This did not appear before.  There is no pass phrase so I press enter and the connection is made.

How do I remove the pass phrase prompt?

---

### Post by hyper_ch on 2009-01-09
do a key-based login on the remote computer.

---

### Post by expatCM on 2009-01-09
Happy to do that.

Would you please tell me what that means or how ........  :)

---

### Post by dmizer on 2009-01-09
Try this: [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

---

### Post by expatCM on 2009-01-11
I took a look at the link ... thank you.  The problem is that it will take me a long time to come up to that level of understanding .... (what I really mean is that if I play around with this and make a mistake I am basically toast with no ssh access at all ....).

---

### Post by hyper_ch on 2009-01-11
it's actually quite simple:

DESKTOP= Computer you work on
SERVER= Computer you wnat to login from your DESKTOP
USER= The username on the SERVER into which you want to login to

On your DESKTOP open a terminal, then run
```

ssh-keygen -t dsa

```

Then run:
```

cat ~/.ssh/id_dsa.pub | ssh -l USER SERVER 'cat >> ~/.ssh/authorized_keys'

```

Once done, you can just login by issuing:

```

ssh USER@SERVER

```

---

### Post by expatCM on 2009-01-11
Thanks for the response.  I cannot do this until the morning but could I just confirm the syntax please.

You say that it should be

> cat ~/.ssh/id_dsa.pub | ssh -l USER SERVER 'cat >> ~/.ssh/authorized_keys'

I was just wondering if it should be 

> cat ~/.ssh/id_dsa.pub | ssh -l USER@SERVER 'cat >> ~/.ssh/authorized_keys'

---

### Post by hyper_ch on 2009-01-11
not sure if the second one works but the one I posted will work ;)

---

### Post by expatCM on 2009-01-11
Yes, it allows login but I am still prompted for the passphrase which is blank ..........

---

### Post by dmizer on 2009-01-11
In the link I posted earlier, it talks about a tool which has simplified my ssh keypair life significantly (which is why I linked the tutorial in the first place).

To add your key to the server, run this command from the client (after creating your keypair):
```
ssh-copy-id -i ~/.ssh/id_rsa.pub username@server
```
The "ssh-copy-id" tool will correctly set permissions, use correct formatting, and takes all the guesswork out of adding keys. In case you don't believe me, testimonial is here: [http://ubuntuforums.org/showthread.php?t=1031033](http://ubuntuforums.org/showthread.php?t=1031033)

---

### Post by expatCM on 2009-01-11
erm ... there appears to be some misunderstanding here ....

Yes I have done all of that including the latest command. I can even ssh from one machine to another ...  no problem.

The issue is that I am always prompted before the connection is completed for the passphrase.  It is a blank field so I only have to press enter.  But this creates one big issue.  I cannot automate any process, for example rsync will not run automatically since I need to press enter....

What I see is as follows 

> Enter passphrase for key '/home/user/.ssh/id_rsa': 

---

### Post by dmizer on 2009-01-12
Do you have more than one id_rsa key in ~/.ssh?

I suggest that you start from scratch. Delete everything from your ~/.ssh directory (make backups if you need to), remake a new key and send it to the server with the tool I suggested earlier.

---

### Post by expatCM on 2009-01-14
All done.  Even works now :)

What I did was rename the .ssh directory and then created new keys.  Works without any prompt at all .... Great ...

Many thanks for your assistance in seeing this through to the happy end :)

---

