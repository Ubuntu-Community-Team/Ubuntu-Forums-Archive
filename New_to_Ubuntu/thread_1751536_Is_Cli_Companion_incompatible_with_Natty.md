---
title: "Is Cli Companion incompatible with Natty?"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by Wheel on 2011-05-06
Hi,

I can not install/enable the repo for Cli Companion since I Clean installed Natty.
I had no problems with this on Maverick or Lucid and have come to rely on it since my Terminal skills are weak.

I have tried to set this up via Terminal:

sudo add-apt-repository ppa:clicompanion-devs/clicompanion-nightlies 
sudo apt-get update
sudo apt-get install clicompanion

And I have tried downloading and installing the deb file:

Clicompanion_1.0-3.1_all.deb

The other 3rd party repositories  I wanted (Dropbox, Medibuntu) installed cleanly--no problems.

Has anyone who is using Natty been able to successfully use Cli Companion?

---

### Post by duanedesign on 2011-05-08
I have not made a PPA yet for Natty. However you can use the following commands to install CLI Companion on Natty.

```
wget http://launchpad.net/clicompanion/1.0/1.0rc2/+download/clicompanion_1.0-3.1_all.deb
```

```
dpkg -i clicompanion_1.0-3.1_all.deb 
```

---

### Post by Wheel on 2011-05-09
> **duanedesign said:**
> I have not made a PPA yet for Natty. However you can use the following commands to install CLI Companion on Natty.

```
wget http://launchpad.net/clicompanion/1.0/1.0rc2/+download/clicompanion_1.0-3.1_all.deb
``````
dpkg -i clicompanion_1.0-3.1_all.deb 
```

When I initially tried installing the repo--which failed--and followed with the install cli companion command, I would get a "not found" error.

So I found the commands to install the deb version.
The same 2 commands you have suggested.
No luck.  I still got a "Not Found" error.
(By the way, I copy & paste commands to avoid typos.)

And for some reason (I don't understand enough about this to do any real problem solving),  both Terminal and Synaptic would no longer open.  That's a pretty critical handicap.  I didn't know what else to do, so I re-installed Natty.

Then I posted my question.

I appreciate your attempt to help, but I'm reticent to repeat those commands for fear of handicapping the system once again.

---

