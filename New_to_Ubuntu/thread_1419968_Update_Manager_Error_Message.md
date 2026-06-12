---
title: "Update Manager Error Message"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by drart on 2010-03-02
Using **Ubuntu 8.1** on a **dual boot system** with **WIN-XP Pro**, but both OS are **separate drives**.
When Update Manager is activated 2 ERROR MESSAGES below are generated.

[B]W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid 
Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F7D0E1722382D57E[/B]

**W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0**

I'm new to Ubuntu and I have no idea what the messages mean, where to go to find out, what to do to fix them (if they can be fixed). Can anyone help me.:confused:

---

### Post by Arijit_Kundu on 2010-03-02
run this in terminal, and again with the other number (28A8205077558DD0)

sudo gpg --keyserver hkp://subkeys.pgp.net --recv-keys F7D0E1722382D57E
gpg --export --armor  60D11217247D1CFF | sudo apt-key add -

---

### Post by Paddy Landau on 2010-03-02
The 'key' is a signature, to check that what you're getting is the real thing and not some sneaky messed-up version.

The Update Manager is saying that it doesn't have access to the key for those particular repositories, so it can't check the signature.

Open a terminal and try these commands:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F7D0E1722382D57E
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 28A8205077558DD0
sudo apt-get update
```They should solve the problem. If not, then sorry, someone with more knowledge than I have will have to help.

---

### Post by Arijit_Kundu on 2010-03-02
oh, yes, one line at a time (terminal is in the menu under accessories)

---

### Post by Penguin Guy on 2010-03-02
It means that you don't have the key to the server which gives you the updates. [Open the terminal]("http://www.psychocats.net/ubuntu/terminal") and copy and paste the following into it, then press enter:
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F7D0E1722382D57E
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 28A8205077558DD0
sudo apt-get update

```

> **Arijit_Kundu said:**
> oh, no, not with the same numbers, the third line will have the other number
Ooops - I've fixed it now.

---

### Post by Arijit_Kundu on 2010-03-02
oh, no, not with the same numbers, the third line will have the other number

---

### Post by drart on 2010-03-02
> **Paddy Landau said:**
> The 'key' is a signature, to check that what you're getting is the real thing and not some sneaky messed-up version.

The Update Manager is saying that it doesn't have access to the key for those particular repositories, so it can't check the signature.

Open a terminal and try these commands:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F7D0E1722382D57E
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 28A8205077558DD0
sudo apt-get update
```They should solve the problem. If not, then sorry, someone with more knowledge than I have will have to help.


Thanks for the help. Sorry it took so long to reply, business got in the way. Both error messages GONE. I don't know where they went or why. I have a lot of studying to do with Ubuntu. Don't want to put anyone off but Paddy Landau's solution was broke the barrier. Thanks to all who responded.

---

### Post by Paddy Landau on 2010-03-03
> **drart said:**
> I don't know where they went or why.

[LIST]
[*]'sudo' means run the command as root (i.e. with raised authorisation).
[*]'apt-key ... -recv-keys ...' instructed your computer to go find each key (signature) on the server [keyserver.ubuntu.com]("http://keyserver.ubuntu.com/").
[*]'apt-get update' told the computer to update its repository with the new information (the new signatures).
[/LIST]
If you wish to understand more about how it works, look up [public key cryptology]("http://en.wikipedia.org/wiki/Public-key_cryptography").

---

