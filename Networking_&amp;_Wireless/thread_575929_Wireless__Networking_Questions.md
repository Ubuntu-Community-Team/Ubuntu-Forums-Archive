---
title: "Wireless / Networking Questions"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by PartisanEntity on 2007-10-14
Right, I am not sure what I did.

I am using Feisty Fawn on my laptop. I have pam-keyring and installed in order to not have to enter my password every time I want to connect to my home wireless network.

However I now have to connect to a new wireless network with a different password.

So, I can see the wireless network using network manager, but when I click on it, network manager will animate the icon but nothing else happens (no password prompt), I tried to manually enter the data but nothing happened.

I assumed this has something to do with pam-keyring, so I fired up Synaptic and removed it. Still no change. But I also noticed that if I try to issue either iwconfig or ifconfig in the terminal I get this message:

```
The program 'iwconfig' is currently not installed.  You can install it by typing:
sudo apt-get install wireless-tools
bash: iwconfig: command not found
```

I did try to install wireless-tools, but they are already installed. I think Synaptic removed something else while it removed pam-keyring?

Help:)

---

### Post by kevdog on 2007-10-14
When you do:
sudo updatedb
locate iwconfig

Does it come back with a path for the executable???  I think they are supposed to be in /usr/bin by default

---

### Post by PartisanEntity on 2007-10-15
Thanks for the feedback, I'll check it out and post back when I get home.

---

### Post by PartisanEntity on 2007-10-15
Okay, so I updated the db and then ran:

```
locate iwconfig
```

Which gave me:

```
/sbin/iwconfig
/usr/share/man/cs/man8/iwconfig.8.gz
/usr/share/man/fr/man8/iwconfig.8.gz
/usr/share/man/man8/iwconfig.8.gz
```

But as before, when I type 'iwconfig' in the terminal I get:

```
The program 'iwconfig' is currently not installed.  You can install it by typing:
sudo apt-get install wireless-tools
bash: iwconfig: command not found
```

And the issue persists, that I cannot connect the to new router because I get no password prompt.

---

### Post by PartisanEntity on 2007-10-15
Update:

Maybe I am having a dumb moment but if I issue 'sudo' before iwconfig or ifconfig they both work. So I guess these are root applications? For some reason I did not remember them being as such :)

So now the only issue I am having is that I cannot connect to the new wireless router.

---

### Post by PartisanEntity on 2007-10-15
Right, ignore this too, I seem to be having an extremely slow day, I did not apply the changes I made to the router configuration, when I remembered to do that I was able to connect, duh :)

---

