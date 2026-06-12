---
title: "Bash:-  Getting SSH to work on Ubuntu 14.04 32 bit"
date: 2015-12-20
forum: Networking &amp; Wireless
---

### Post by Tim036 on 2015-12-20
I'm OK with the client side but the server side is my nightmare.  As the computers are on a local network, encryption is not and elaborate passwords are not really needed, but I made a BIG mistake, loaded the openssh onto the client side and the serverside onto a different computer on the network.

After that it asked for a password.  Well before all the computers had the same password but this was not recognised.  Now not even ping works !

So I'm reloading 14.04 on both PCs and going to try again using SSH from Ubumtu Software Centre   Now the question is how do I enable the server side of the SSH I'm about to upload ?

The raspberry Pi, for example has in raspi-config got a switch in its advanced secrion to turn SSH on or off, and is easy to SSH into, its just I have so far not found a way of doing it on Ubuntu 14.04.

I have succeeded in getting very very confused tho....  *LOL*

Any thoughts from anyone are very very welcome!

:  )))

Tim

---

### Post by QIII on 2015-12-20
Many of the answers you get may be as inscrutable to you as they are helpful.  What I would suggest before you try to understand any help you may be given here is that you read through the material [here]("https://help.ubuntu.com/community/SSH"), [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring") and [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys").

I don't expect that you will come away with an epiphany and know exactly where you need to go.  But reading through all that might give you a good overall review that will make better sense when the answers start arriving.  You may just find that you will be able to ask better, more targeted questions, as well.

Feel very welcome to answer this with a whole lot more questions.  We're here to help!

Going back to your comments about local network and passwords (which you should not use -- always use key pairs):  I recommend that you always use good SSH security practices even on your local network.  Don't get in to bad, sloppy habits.  Do it right.

---

### Post by Tim036 on 2015-12-20
Many many thanks for your response !     Its been very frustrating as hour after hour after hour passes but now I have hope of a solution !

I'm a much happier,

:D:D

Tim

---

### Post by The Cog on 2015-12-20
The client is installed by default on Ubuntu, nothing extra needed.
For the server (the PC you are connecting to), all you really need is the command:
```
sudo apt-get install openssh-server
```
after which you should be able to connect to that server from an SSH client. 

When connecting, (let's assume the server's address is 1.2.3.4) the simplest command is as below. It uses your current username that you are logged in as on your client PC, and prompts for a password:
```
ssh 1.2.3.4
```

If you want to log into the server as a different username to the name you are locally logged in as (e.g. as gandalf), you specify the name like this:
```
ssh gandalf@1.2.3.4
```

It is possible to set up password-less logins by exchanging key files, but you should follow the tutorials that QIII posted for that - I won't try to repeat the instructions here.

If after installing you cannot connect, then come back here for more help. Nothing should stop pings working - somehow something unconnected with SSH got broken.

---

