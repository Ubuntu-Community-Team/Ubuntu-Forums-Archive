---
title: "SSH Keys Please help"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by theamazingbeat on 2011-01-04
Okay let it be known i have just started using ubuntu, as I am a current Windows/OSX technician, I just started on Thursday.


Anyway what I want out of this is to setup an SSH.

I have already set it up, the only problem I have now is using SSH Keys.

Well I created my keys by entering in 

```
ssh-keygen -t rsa -b 4096
```Anyway so now that I have made that key. I go into: **etc/ssh** and get the 2 rsa key files (public & private).




So now what I have to do (trying to accomplish) is go onto a Windows machine, use puTTY or WinSCP and connect to the server with those keys. Well I realized I cannot do that without a puTTY private key. So i used puTTYgen and imported my private rsa key and made a puTTY private key out of it. And now my dilemma is when i try using that puTTY private key on puTTY or WinSCP it says:

>  Server refused our key I have looked at so many guides asked so many people and I just want people who actually know what they are doing to help me out. At this point I will almost pay for services :P



Also let it be known that I barely know ubuntu command lines so please go into depth.





Please help me guys. I will be available 24/7 for responses.




-Aaron

---

### Post by theamazingbeat on 2011-01-04
Bump

---

### Post by QLee on 2011-01-04
Even though you didn't wait a full day to bump your post as is the convention here, I'll try to give you a useful answer.

[QUOTE=theamazingbeat]...
I have looked at so many guides asked so many people and I just want people who actually know what they are doing to help me out. At this point I will almost pay for services :P[/QUOTE]

Somewhat surprising that someone would post in the Absolute Beginner  Talk forum and put this restriction. I would have thought that a  technician would have found the Networking and Wireless forum or the  Security Discussions forum or even the General Help forum but your  wording is likely to make people shy away from replying to you in a user support forum.

Paid help is a real possibility. And would help to support Canonical who give us this OS for free.
[http://www.canonical.com/consumer-services/support](http://www.canonical.com/consumer-services/support)


[QUOTE=theamazingbeat]Also let it be known that I barely know ubuntu command lines so please go into depth.[/QUOTE]

Many of us will expect a technician to study and learn from documentation. Much more likely to get help if you come with specific questions that also illustrate that you have made an effort. Just stating that you have looked everywhere is often not enough.

See if any of these links helps you:
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

[http://ubuntuswitch.wordpress.com/2007/07/01/securely-remote-control-your-ubuntu-via-putty-from-a-windows-host-vncssh/](http://ubuntuswitch.wordpress.com/2007/07/01/securely-remote-control-your-ubuntu-via-putty-from-a-windows-host-vncssh/)

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

[QUOTE=theamazingbeat]Please help me guys. I will be available 24/7 for responses.[/QUOTE]

Aha, you don't sleep, you must be a coder. W3lc0m3.

---

### Post by blind2314 on 2011-01-04
First, logon to the Ubuntu box as the user you want to connect as, once there, 
```

cd .ssh
vi authorized_keys

```
 
Copy/paste your key from pUTTYGen into this file, and save it. Ensure that the permissions are correct by typing 
```

chmod 644 authorized_keys

```
and then try to connect as that user. This is assuming a lot, but I can help with specific errors/questions as they arise.
 
I forgot one key component! This needs Pageant running on the windows machine (a putty component) and the private key must be imported into Pageant as well.

---

### Post by KIAaze on 2011-01-04
Oh well, writing my post took more than 1 hour now due to multiple real life interruptions... In the meanwhile, answers have already arrived.
But I'm posting my answer anyway. :P

=======
mini off-topic remark:
Bumping is not always the smartest way to get attention, especially if your post has 0 replies. Because some people use "forum tools->unanswered posts" to hunt for unanswered questions. ;)

On the other hand, since you are no longer an unanswered post, I don't have to worry about answering even if my answer may be incomplete. :)
=======

1) Before setting up SSH keys, make sure you can connect remotely to the server with putty (i.e. through SSH with a password).
This simply requires an SSH server to be installed on the server.

2) Once that works, you can set up passwordless SSH access using SSH keys.
The key pair should be generated on the client and the public key placed on the server.
Of course, maybe it also works even if you generate the key pair somewhere else and then place the public one on the server and the private one on the client.

I never set up passwordless SSH with Putty. The only passwordless SSH system I set up with Windows was with git and it was very similar to the standard process between 2 GNU/Linux machines: [http://help.github.com/msysgit-key-setup/](http://help.github.com/msysgit-key-setup/)

It seems that in the case of putty, you can put the private key wherever you want and then just have to specify its location in putty:
[http://www.howtoforge.com/ssh_key_based_logins_putty](http://www.howtoforge.com/ssh_key_based_logins_putty)

Other links:
[http://www.petefreitag.com/item/532.cfm](http://www.petefreitag.com/item/532.cfm)
[http://www.dailyiteration.com/howto-passwordless-ssh-authentication-with-putty/](http://www.dailyiteration.com/howto-passwordless-ssh-authentication-with-putty/)
[http://the.earth.li/~sgtatham/putty/0.53b/htmldoc/Chapter8.html](http://the.earth.li/~sgtatham/putty/0.53b/htmldoc/Chapter8.html)

---

### Post by bodhi.zazen on 2011-01-04
You need to transfer the key to the server.

The best way to do this, IMO, is with ssh-copy-id (it is faster and reduces errors, no need to copy-paste or chmod).

You next need to import the key to putty if you want to use it.

You do this with Puttygen

[http://quark.humbug.org.au/publications/notes/bofh/msg00059.html](http://quark.humbug.org.au/publications/notes/bofh/msg00059.html)

---

### Post by KIAaze on 2011-01-04
> **bodhi.zazen said:**
> 
The best way to do this, IMO, is with ssh-copy-id (it is faster and reduces errors, no need to copy-paste or chmod).


Mmh, interesting. I didn't know about that command. Thanks. :)

---

### Post by bodhi.zazen on 2011-01-04
> **KIAaze said:**
> Mmh, interesting. I didn't know about that command. Thanks. :)

You are most welcome. ssh-copy-id is underutilized =)

---

### Post by theamazingbeat on 2011-01-05
> **blind2314 said:**
> First, logon to the Ubuntu box as the user you want to connect as, once there, 
```

cd .ssh
vi authorized_keys

```
 
Copy/paste your key from pUTTYGen into this file, and save it. Ensure that the permissions are correct by typing 
```

chmod 644 authorized_keys

```
and then try to connect as that user. This is assuming a lot, but I can help with specific errors/questions as they arise.
 
I forgot one key component! This needs Pageant running on the windows machine (a putty component) and the private key must be imported into Pageant as well.


Okay I thank you a lot for this, sorry for actually not getting back to you guys (Busy at work). Anyway I thank you all for the replies I just have one question. What is the difference between the way to copy the key, and ssh-copy-id? IMO the above way to do it is fairly simple. I will try and do it in the morning. Again thanks a lot




P.S: Sorry Qlee I didn't read the rules. That is my fault.

---

### Post by BaffledMollusc on 2011-01-05
Just one more point. Using "vi authorized_keys" will open the file using the text editor vi, which, if you're not used to it, is somewhat akin to repeatedly poking yourself in the eye with a sharp stick. So to ensure you don't have a terrible linux experience, you might want to open the file with the standard text editor instead: "gedit authorized_keys".

In fact, in that vein, I should probably point out that people often post solutions using the command line because it's simple and the instructions are easily followed even if you don't know what they do. I think sometimes this makes people think linux is harder than it needs to be.

You can, of course, do all this stuff with the GUI if you prefer. Open the file via double clicking in the file browser, right click the file to change permissions rather than using chmod etc.

---

### Post by blind2314 on 2011-01-05
You're probably right, but it wasn't my attention to confuse him or make it seem "hard" in any way. I'm very comfortable with vi due to being a sysadmin, and it being a necessity..but it can be very...grumpy :)
 
If you have any issues with the above solution OP, the links posted by other members are great resources, or I can try to help again.

---

### Post by QLee on 2011-01-05
[QUOTE=theamazingbeat]...

P.S: Sorry Qlee I didn't read the rules. That is my fault.[/QUOTE]

You don't need to write that you are sorry to me, I just pointed out something that you did not yet know. 

Just relish all the good answers you received, once your post was noticed. 

And, I repeat, Welcome!

---

### Post by KIAaze on 2011-01-05
> **theamazingbeat said:**
> What is the difference between the way to copy the key, and ssh-copy-id?

Like bodhi.zazen said: It is faster and reduces errors, no need to copy-paste or chmod. :)

Usage example:
```
ssh-copy-id -i  id_rsa.pub terry@host2
```
From [http://www.linuxplanet.com/linuxplanet/tips/6592/1/](http://www.linuxplanet.com/linuxplanet/tips/6592/1/)

That being said, it seems to have some drawbacks (which might have been fixed by now. I never tried it.):
> Three Minor Annoyances of ssh-copy-id

Following are few minor annoyances of the ssh-copy-id.

   1. Default public key: ssh-copy-id uses ~/.ssh/identity.pub as the default public key file (i.e when no value is passed to option -i). Instead, I wish it uses id_dsa.pub, or id_rsa.pub, or identity.pub as default keys. i.e If any one of them exist, it should copy that to the remote-host. If two or three of them exist, it should copy identity.pub as default.
   2. The agent has no identities: When the ssh-agent is running and the ssh-add -L returns &#8220;The agent has no identities&#8221; (i.e no keys are added to the ssh-agent), the ssh-copy-id will still copy the message &#8220;The agent has no identities&#8221; to the remote-host&#8217;s authorized_keys entry.
   3. Duplicate entry in authorized_keys: I wish ssh-copy-id validates duplicate entry on the remote-host&#8217;s authorized_keys. If you execute ssh-copy-id multiple times on the local-host, it will keep appending the same key on the remote-host&#8217;s authorized_keys file without checking for duplicates. Even with duplicate entries everything works as expected. But, I would like to have my authorized_keys file clutter free.

From [http://www.thegeekstuff.com/2008/11/3-steps-to-perform-ssh-login-without-password-using-ssh-keygen-ssh-copy-id/#more-268](http://www.thegeekstuff.com/2008/11/3-steps-to-perform-ssh-login-without-password-using-ssh-keygen-ssh-copy-id/#more-268)

If you do it manually, you at least learn how it works, i.e. by adding a the text contents of the public key file to "~/.ssh/authorized_keys" on the server.
The advantage of ssh-copy-id is that it does everything in one command and ideally securily (log into remote server, append public key, set correct file permissions).

[B]But since ssh-copy-id will most likely not be available on Windows, you will probably have to do it "manually" anyway.
[/B]

---

### Post by theamazingbeat on 2011-01-05
With ssh-copy-id, don't i have to have ssh servers running on both machines to send the key out?

---

### Post by bodhi.zazen on 2011-01-05
> **theamazingbeat said:**
> With ssh-copy-id, don't i have to have ssh servers running on both machines to send the key out?

No, you do not need a ssh server running on both machines.

---

### Post by theamazingbeat on 2011-01-05
I keep trying to ssh-copy-id and it says the Connection Timed out? Are you positive I don't have to have any kind of ftp server setup on my computer?

---

### Post by blind2314 on 2011-01-05
I would try it the manual way I described (and that's been said in other posts). You'll learn how to do it in the future, and it will only help you out as far as experience.

---

### Post by theamazingbeat on 2011-01-05
> **blind2314 said:**
> First, logon to the Ubuntu box as the user you want to connect as, once there, 
```

cd .ssh
vi authorized_keys

```Copy/paste your key from pUTTYGen into this file, and save it. Ensure that the permissions are correct by typing 
```

chmod 644 authorized_keys

```and then try to connect as that user. This is assuming a lot, but I can help with specific errors/questions as they arise.
 
I forgot one key component! This needs Pageant running on the windows machine (a putty component) and the private key must be imported into Pageant as well.


Do I just generate a new key, and copy the key from the big box that PuTTYGen displays the key?

Just making sure I got it right

---

### Post by theamazingbeat on 2011-01-06
Okay I am still getting 

> Disconnected: No supported authentication methods available 


I have tried the manual way and ssh-copy-id (which worked but I believe it worked backwards, basically taking my Windows Machine key and connecting with that, if only I could find the command for Cygwin, I could possibly get this working)

---

### Post by KIAaze on 2011-01-06
Can you connect to the SSH server from another GNU/Linux machine with password?
Can you connect to the SSH server from another GNU/Linux machine with key authentication?
Can you connect to the SSH server from the Windows machine through putty without any key authentication, i.e. by entering a password?

> if only I could find the command for Cygwin
What exactly do you mean?

If you installed the ssh client package in Cygwin, the command will be the same as in GNU/Linux, i.e.: "ssh".
It should also be the same for other common commands like "scp".
I don't know if there is a Cygwin package for "ssh-copy-id".

To use SSH by command-line (Cygwin or under GNU/Linux):
```
ssh USER@HOST
```

Note: Getting key authentication to work in Cygwin might not make it work via putty and vice-versa.

---

### Post by theamazingbeat on 2011-01-07
Okay this is what I did to solve the problem and now I realize how easy it actually is.

Simply I generated a 4096 bit Key (You can just keep it at 1024 bit, but 4096 is more secure) in PuTTYGen. In the box where it  displays the key I copied that and put it into a text document. As well I saved the public and private key file. I put them  on a flash drive.

So I go to my Ubuntu machine, pop in my flash drive, and ran this command.


```
sudo gedit /home/username/.ssh/authorized_keys
```


**(**So if you are like me and your **[COLOR=Black].ssh [/COLOR]**[COLOR=Black]folder does not [/COLOR]exist like mine didn't. Just create that folder manually, by going into** /home/username **and right click, then **Create Folder**. Same thing if there is no **authorized_keys **file just create it. By right clicking, then **Create Document**, then **Empty File.)**

Enter your password for your user account. Then I pasted the key from the text document into that and saved. Then just to be sure that the permissions were set right, I entered the command:


```
chmod 644 authorized_keys
```



Restarted my machine just to be safe...


Then I simply connected via my windows box with that private key file, and SUCCESS!


I personally use WinSCP as my client, way easier to work with then PuTTY.



This is the best way to do it in my mind. So hopefully if there was anyone like me and couldn't figure this out, here ya go, because I messed with this for a long time, lol!

---

