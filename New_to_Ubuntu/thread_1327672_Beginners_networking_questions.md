---
title: "Beginners networking questions"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by Fidelio on 2009-11-15
Hi All,
I'm running 9.04 on my desktop pc, which is connected via ethernet to a wireless router.
My wife has just bought a laptop on which she's got Linux Mint. This connects wirelessly to the net through the same router. Can anyone point me to some instructions on how to share files between the two? All I could find was instructions for how to designate folders as 'shared'
I've done this but I don't know how to set up the network so that I can find the shared files on one PC from another.
And it would be neat if I could print from the laptop. The only printer is an HP connected to the desktop PC by a USB cable.
I'm sure there is a step by step guide somewhere, but I can't for the life of me find it.
Thanks
Andy

---

### Post by yeats on 2009-11-15
For file sharing, you'll need either samba or nfs (just samba if you are also sharing with Windows computers or will want to later).  Samba is fairly straightforward if it is installed on each computer:

```
sudo apt-get install samba
```

Once samba is installed, each member of the network should be visible when you go to Places -> Network.

Printer sharing is similar.  Once the computers are all visible on the network, you can configure the desktop to share the printer, and the other computers to use the shared printer.

Does that help?

---

### Post by Fidelio on 2009-11-15
double post, sorry

---

### Post by Fidelio on 2009-11-15
Thanks Chris
Samba is installed, although I don't actually need to share with windows machines. When I go to places>network, on either machine I just get a 'Windows Network' icon. If I click on this on the desktop, it says 'Unable to Mount Location' failed to retrieve share list from server.
If I click on the laptop it goes to WORKGROUP then  JULIA-LAPTOP which is the name of the laptop.
I don't have a windows network, so I'm not sure what that icon is there for anyway.
Thanks though.

---

### Post by mprince on 2009-11-15
This won't help with printer sharing, but you could try a small application called "Lanshark".

[http://lanshark.29a.ch/en/About.html](http://lanshark.29a.ch/en/About.html)


Just install it on your machine and also on hers and they should share files.

---

### Post by Fidelio on 2009-11-15
> **mprince said:**
> This won't help with printer sharing, but you could try a small application called "Lanshark".

[http://lanshark.29a.ch/en/About.html](http://lanshark.29a.ch/en/About.html)


Just install it on your machine and also on hers and they should share files.
I guess that's an option. I just thought there would be a straightforward way to do it. Both the computers connect through the same router, so they should be able to see each other, no? Do I need to do something to set up a network name, like you do with windows when they all have to be on MSHOME or whatever?

---

### Post by mprince on 2009-11-15
> **Fidelio said:**
> Do I need to do something to set up a network name, like you do with windows when they all have to be on MSHOME or whatever?

You can change that in the [global] section of your smb.conf file.

```
sudo gedit /etc/samba/smb.conf
```

Make sure you both have the same workgroup name in the [global] section.

```
workgroup = whatever
```

---

### Post by Fidelio on 2009-11-15
Thanks. Both the machines have 'workgroup=WORKGROUP' in the smb.conf file.
Also, I had the firewall turned on on my desktop. Now that I've turned it off I don't get the 'Unable to Mount Location' failed to retrieve share list from server' error.
However, each computer can still only see itself, if you see what I mean. If I go into the laptop WORKGROUP I just see JULIA-LAPTOP and if I go into the desktop it just shows FAMILY-PC.

---

### Post by chriscross93 on 2009-11-15
Once samba is installed you still have to share individual folders.  Samba wont open up your whole machine by default (if at all...)

You could also use ssh.

```
sudo apt-get install ssh
```

Once that is on both machines, goto Connect to Server under places.  Select ssh from the dropdown menu, and put in the other machines IP Address.  Then log in using the usr and pass of the person on that machine.  You will then have full access to the remote filesystem.  A shortcut will show up in Places, not under Network.

To find your IP:
```
ifconfig
```

---

### Post by sandyd on 2009-11-15
> **Fidelio said:**
> Thanks Chris
Samba is installed, although I don't actually need to share with windows machines. When I go to places>network, on either machine I just get a 'Windows Network' icon. If I click on this on the desktop, it says 'Unable to Mount Location' failed to retrieve share list from server.
If I click on the laptop it goes to WORKGROUP then  JULIA-LAPTOP which is the name of the laptop.
I don't have a windows network, so I'm not sure what that icon is there for anyway.
Thanks though.
try this
```

sudo apt-get install system-config-samba
gksudo system-config-samba

```
Then go to Prefrences -> Server Settings

enter in your workgroup (both computers should be on the same workgroup)
the rest of the stuff is self explanatory.

---

### Post by Fidelio on 2009-11-15
I've set a Folder as shared on both machines, in the home folder, but it doesn't show up on the other one. I can access the shared folder on each PC through places>network>windows network> (PC Name) > shared.
I;ll try the ssh thing though. It should work, though, as I'm doing it, right?

---

### Post by mprince on 2009-11-15
*

---

### Post by Fidelio on 2009-11-15
> **carlee said:**
> try this
```

sudo apt-get install system-config-samba
gksudo system-config-samba

```
Then go to Prefrences -> Server Settings

enter in your workgroup (both computers should be on the same workgroup)
the rest of the stuff is self explanatory.
Hi. Thanks. Doesn't that just do the same as checking that they are both on the same workgroup in the smb.conf file?
Actually, I've just done that, and now my the shared folder isn't showing up at all, even on its own machine.

---

### Post by WitchCraft on 2009-11-15
You could use sshfs to share the entire machine, not just a folder.

This is how you do it:
```

apt-get -y install openssh sshfs

ssh-keygen -t rsa -b 4096

```

Then, in the folder ~/.ssh, you have the file id_rsa and id_rsa.pub.

Now e-mail id_rsa.pub to your wife.
Do the same at your wife's laptop, and email her id_rsa.pub to you.


Save id_rsa.pub to the Desktop, open a terminal there, and type: 
```

cat ./id_rsa.pub >> ~/.ssh/authorized_keys

```

Now you can mount your wifes entire filesystem into a folder on your drive:
```

mkdir -p /mnt/sshfs
sshfs username@IP:/ /mnt/sshfs

```
Now open /mnt/sshfs and you see your wifes root drive (and vice-versa if she does the same).
The transmission is 4096 bit RSA encrypted, and you don't even need to enter a password.
You can access your wife's laptop from everywhere, even from work - while she is at home, as long as port 22 is forwared everywhere (if you know her ip-address; see dyndns).

And the best thing: It's relatively secure, because Windows users can't access sshfs filesystems (unless they bought software worth $150, to access a filesystem nobody in the windows world has) ...

PS: I think you have to enably key-based login in the sshd config file, and if your dns doesn't work properly you might have to remove the paranoid line from hosts.deny

---

### Post by westvan23 on 2009-11-18
I certainly thought so.  I installed system-config samba and set all the properties so that sharing should work.  But it still doesn't.

No matter what I do I can see the contents of shared folders in windows but I am always denied access from using them.  What could I be missing here?

More help would be appreciated, thank you.

> **carlee said:**
> try this
```

sudo apt-get install system-config-samba
gksudo system-config-samba

```Then go to Prefrences -> Server Settings

enter in your workgroup (both computers should be on the same workgroup)
the rest of the stuff is self explanatory.

---

### Post by WitchCraft on 2009-11-22
> **westvan23 said:**
> I certainly thought so.  I installed system-config samba and set all the properties so that sharing should work.  But it still doesn't.

No matter what I do I can see the contents of shared folders in windows but I am always denied access from using them.  What could I be missing here?

More help would be appreciated, thank you.

Do you have more permissions on the files than just seeing a file?
For example read/write/execute ?

---

