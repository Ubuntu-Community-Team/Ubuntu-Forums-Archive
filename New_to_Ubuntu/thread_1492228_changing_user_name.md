---
title: "changing user name"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by Garthhh on 2010-05-24
I've made a mistake & gave 2 computers the same username
how do I fix it & what other things will I mess up?

---

### Post by mbzn on 2010-05-24
Is it your username or the computername that is the same?

---

### Post by Garthhh on 2010-05-24
> **mbzn said:**
> Is it your username or the computername that is the same?
the name of my home folder is the same, which is my username...
I'm trying to share, so I end up with what looks like the same folder on 2 different computers

---

### Post by mbzn on 2010-05-24
This shouldn't be a problem.

---

### Post by roger_1960 on 2010-05-24
Hi

I agree, I have 4 laptops with the same user accounts on each one - not a problem.

---

### Post by Garthhh on 2010-05-24
> **mbzn said:**
> This shouldn't be a problem.
good it's far less confusing for stuff, keeping things consistent
I'm trying to file share across my home network & not quite getting it done
I'm upgrading my ol pentium III pc to 10.04 to see if I can just do it with nautilus...

---

### Post by nothingspecial on 2010-05-24
To access your other computers within your home network


If both your computers are Ubuntu, first install ssh on both machines

Code:

```
sudo apt-get install openssh-server openssh-client
```

Then in your menu go places > connect to server

In the top box select ssh

In the next one type username@ipaddress

This is the username and ip address of the other machine

When you click connect you will have access to the other computers file system.

If you tick (check) the bookmark field, you will have something you can click in your places menu.

---

### Post by Garthhh on 2010-05-24
so I need to have static addresses then?
this laptop is wireless further complicating the issue
I tried sharing through the GUI & all I can manage to see is the files on this computer, when I'm on here & the files on the other when I'm there:confused:

---

### Post by SRST Technologies on 2010-05-24
No, you don't need static IP addresses.  When you obtain the IP lease from the router, generally that IP address will never change even when the IP lease is up and you get a new one.  The router is smart enough to realize that the guy who just gave up X.X.X.X is probably going to want X.X.X.X back just to keep things simple.

Even if you have Wireless, you're probably going to get the same IP address back again.

Since you said you are trying to share a file across the network and wondered if having the same username would cause a problem, I'm assuming you're trying to keep up to date files from one machine to ten or four or however many other machines you have.  If this is the case, there's an even easier way to sync your files.  Look into the rsync and rsync like packages.

---

### Post by Garthhh on 2010-05-24
> **SRST Technologies said:**
> No, you don't need static IP addresses.  When you obtain the IP lease from the router, generally that IP address will never change even when the IP lease is up and you get a new one.  The router is smart enough to realize that the guy who just gave up X.X.X.X is probably going to want X.X.X.X back just to keep things simple.

Even if you have Wireless, you're probably going to get the same IP address back again.

Since you said you are trying to share a file across the network and wondered if having the same username would cause a problem, I'm assuming you're trying to keep up to date files from one machine to ten or four or however many other machines you have.  If this is the case, there's an even easier way to sync your files.  Look into the rsync and rsync like packages.

even more basic, just stuff like sharing a music library & to be able to find & open a document no matter which computer I'm using.  My pc is hooked up to the printer, so I just email files to my self when I need to print.
I haven't done a thing & can see the public files on my wifes vista machine, I don't understand why this is so complicated?

---

### Post by SRST Technologies on 2010-05-24
Ah, I see.  Ok, here's how you can handle this easy.  Open up a terminal and type the following on each computer you want to be able to access over the network.

sudo apt-get install nautilus-share

Or, if you prefer the Synaptic method, just search for the nautilus-share package and install it.

Once installed, you may now right click any folder in Nautilus you want and share it on the network.

If you put the printer on your wife's machine, you would be able to surf your home network from her machine and print directly from the other machines to her printer without having to email anything.

---

### Post by shazbut on 2010-05-24
If you don't want to use the IP address for ssh, hostname.local works (replace hostname with the actual host name) assuming both machines are on the same subnet.

---

### Post by Garthhh on 2010-05-24
> **SRST Technologies said:**
> Ah, I see.  Ok, here's how you can handle this easy.  Open up a terminal and type the following on each computer you want to be able to access over the network.

sudo apt-get install nautilus-share

Or, if you prefer the Synaptic method, just search for the nautilus-share package and install it.

Once installed, you may now right click any folder in Nautilus you want and share it on the network.

If you put the printer on your wife's machine, you would be able to surf your home network from her machine and print directly from the other machines to her printer without having to email anything.

already have it along with samba & Gshare
the printer is connected to a old pentium III running 10.04 [I just upgraded a few hours ago in an effort to make this work

I just tried to share just the documents folder
& get an error
'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. The connection was refused. Maybe smbd is not running.
?

---

