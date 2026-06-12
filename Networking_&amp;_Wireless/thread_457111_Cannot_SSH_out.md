---
title: "Cannot SSH out"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by RurouniJ on 2007-05-28
Hello all,

I am having trouble SSH'ing out of my newly (first time) installed Kubuntu installation.

If I try and access another Linux machine using SSH or PuTTY I get the following message after entering my password:

Permission denied (publickey,gssapi-with-mic,password).

I am able to access this machine using PuTTY on a windows machine I have (same hardware) so I am assuming it is an issue with Kubuntu rather than the destination server.

Anyone got any ideas?

Many thanks

RJ

---

### Post by pacanukeha on 2007-05-28
Are you SSHing into a gentoo server per chance?  I have seen weird password issues with them.  I don't know what the cause is, but a possible work-around is to create a key pair and stick the public key on the server via your windows interface.

---

### Post by RurouniJ on 2007-05-28
No I am SSHing into a Fedora Core server. I would like to avoid using public / private keys etc etc. and just want to use a simple PW. I tried looking at the ssh_config on my Kubuntu machine and disabling everything but the password authentication but that didn't seem to work.

---

### Post by RurouniJ on 2007-05-29
> **RurouniJ said:**
> No I am SSHing into a Fedora Core server. I would like to avoid using public / private keys etc etc. and just want to use a simple PW. I tried looking at the ssh_config on my Kubuntu machine and disabling everything but the password authentication but that didn't seem to work.

Have googled about with this and haven't managed to find anything that would help. Does anyone have any ideas as this is a bit of a showstopper with regards to to switching to Kubuntu.

It looks like Kubuntu is trying to use three different authentication mechanisms (publickey, that gssapi one and password) when SSH'ing into the target box, I tried changing ssh_config to only use password authentication but that doesn't seem to have done the trick. 

I am still assuming it is a kubuntu setting since this works fine from an identical machine that is running windows and when using PuTTY it works in win and doesn't in Kubuntu.

[EDIT]

That will teach me to assume, the target machine SSH has GSS and public key enabled (disabled now). I can only assume that windows is ignoring these options? I cannot test this yet as I don't have access to Kubuntu but hopefully this will sort it out....hopefuly

---

### Post by zdude on 2007-05-29
if you are connecting to a port < 1024 (i.e., port 22) then you need to "sudo putty".  Linux putty will then work on some ports like 80 but not others. I tend to use wine with windows putty program, it seems to work correctly. Once again you need to sudo wine putty. Some on here will ask how come you don't use SSH? Well in my case I have window boxes using putty and the keys you make are different then the ones SSH uses and I also have users dual booting. It is a PITA. Hope this helps.

---

### Post by pacanukeha on 2007-06-04
It is strange that you need to sudo for putty < 1024.  sudo to open a local port < 1024 sure , but sudo to connect to a remote port?  Weird, very weird.

---

### Post by kevdog on 2007-06-04
Are you trying to do this from the command line???

Do you get any other errors when at the command line you type (assuming ssh is working through port22):

ssh -p 22 user@host 

Although it seems like it from what you have provided, the server sshd_config files specifically is set up for password authentication??

---

