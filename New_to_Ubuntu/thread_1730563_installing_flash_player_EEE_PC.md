---
title: "installing flash player EEE PC"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by Dommi35 on 2011-04-16
Hi- I would be really grateful if someone would be kind enough to talk me through step by step installing flash player onto my EEE PC netbook. It has a form of Ubuntu I think or Xandros??  from what I understand. I have tried all sorts but not really understood what I am doing. Attempts including using sudo konqueror, commands with funny dollar symbols and all sorts!! I have come up against all types of dead ends. :confused:

To complicate (?) matters I only have 300 mb left of my 4 gig hard drive and since i have owned this machine it keeps asking me to update things. At some point I am going to run out of space. Is there an os I can use to replace the one I have? I only need very simple things...wireless access/watching videos. I really don't need anything fancy.

I am vey good normally with software (windows) and can easily follow instructions if someone is brave enough to talk me through.

I look forward to hearing from you!  ):P

Trisha

---

### Post by Paqman on 2011-04-16
For Flash:

[LIST=1]
[*]Open up Ubuntu Software Centre
[*]Search for Flash
[*]Click on the "install" button for the Adobe Flash plugin
[/LIST]

To clear out some space on your hard drive the quickest thing to do is open a terminal and enter the following two commands (just copy and paste):
```

sudo apt-get autoremove

```
```

sudo apt-get clean

```

This will remove any unneeded packages, then dump the package manager's cache. After that you can start doing things like emptying your trash, uninstalling old kernels (use Synaptic Package Manager, search for "linux-image" and uninstall all except the most recent one). If you want to get even more keen, install BleachBit and you'll be able to clean out all sorts of caches and stuff.

---

### Post by MrEgg on 2011-04-16
When you start up your computer, does it say Ubuntu or Kubuntu?

If Ubuntu, open up Terminal (Applications - Accessories menu).

If Kubuntu, open up Konsole (KMenu - System - Konsole - Terminal).

Once either one is fired up, type in :

If Ubuntu :
```
sudo apt-get install ubuntu-restricted-extras
```

If Kubuntu :
```
sudo apt-get install kubuntu-restricted-extras
```

That should take care of your issue.

Cheers,
MrEgg

---

### Post by TeoBigusGeekus on 2011-04-16
Can you reach a terminal in your netbook?
If so, can you post us the output of the commands
```
lsb-release
```
and
```
df -h
```
?

---

### Post by Dommi35 on 2011-04-16
oh wow! replies already!
will answer one by one..

:KS

---

### Post by 3rdalbum on 2011-04-16
The EEEPCs originally came with Xandros, which is not really related to Ubuntu. At least, not enough for Ubuntu users to really know what to do. It sounds like you're still running Xandros.

If the EEEPC's capacity is 4 GiB you could certainly install Ubuntu. However, it would probably run slowly and you still wouldn't have very much space available; probably with all your documents, less than with Xandros. Not entirely sure though. Ubuntu takes a minimum of 3 GiB of space.

---

### Post by Dommi35 on 2011-04-16
Hi Paqman
dont have

[LIST=1]
[*]Open up Ubuntu Software Centre
[/LIST]
maybe i dont have ubuntu- not sure:confused:

---

### Post by Paqman on 2011-04-16
> **Dommi35 said:**
> 
maybe i dont have ubuntu- not sure:confused:

Sounds like you might still have Xandros :(

Does it look like this:
[IMG]http://www.eee-notebook.info/images/eee-xandros-linux.jpg[/IMG]

---

### Post by Dommi35 on 2011-04-16
Hi Paqman
tried the cleanup but got this message...

E: Invalid operation autoremove

---

### Post by Dommi35 on 2011-04-16
Hi Mr Egg

			 		   		 		 		When you start up your computer, does it say Ubuntu or Kubuntu?

neither...
i think i made an error and maybe have xandros?

---

### Post by Dommi35 on 2011-04-16
Hi TeoBigUs

didn't work...

bash: lsb-release: command not found

---

### Post by MrEgg on 2011-04-16
> **Dommi35 said:**
> 
i think i made an error and maybe have xandros?

Yes, it does sound like it indeed! It looks like you probably should ask your question on the xandros forums :)

Good luck !

---

### Post by Dommi35 on 2011-04-16
Hi third album- its helpful to know about ubuntu needing 3 gig. i dont keep docs on the netbook- all is kept on an external hard drive. I wonder if i can buy a larger hard drive for my netbook- will have to look into it

---

### Post by Dommi35 on 2011-04-16
Hi Mr Egg
thanks- will try the Xandros forum-
thanks everyone!
):P

---

### Post by Paqman on 2011-04-16
> **Dommi35 said:**
> I wonder if i can buy a larger hard drive for my netbook- will have to look into it

Unfortunately the early Eeepc's didn't use a normal hard drive. They had a funny solid state drive that can't just be swapped for a bigger one like normal drives can.

---

