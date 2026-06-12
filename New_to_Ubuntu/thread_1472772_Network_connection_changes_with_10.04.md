---
title: "Network connection changes with 10.04?"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by archkidd on 2010-05-04
I have been using 9.4 and connecting to my network with no problems.  I just installed 10.04 and now, although I can connect to the internet which goes through my router, I cannot see the other computers on my network?  Nothing else changed except the upgrade.  Now the network folder says "Unable to mount location - Failed to retrieve share list from server"  Is there something I have to do with 10.04 that was not required with 9.4?

---

### Post by doas777 on 2010-05-04
well, your problem is with SAMBA rather than your network configuration, so hopefully that will help you find more specific solutions. 

the first thing I woudl check is that i have the correct workgroup set, and that the user account i am useing to connect to the server has been registered with samba (run 'sudo  smbpasswd <username>' and enter your password).

---

### Post by archkidd on 2010-05-04
It came back with "New SMB password"  and then would not let me type anything. Pressing enter produced "Retype new password" and then "failed to find entry for <user>"

I am a complete newbie so no idea what is going on here

---

### Post by doas777 on 2010-05-04
> **archkidd said:**
> It came back with "New SMB password"  and then would not let me type anything. Pressing enter produced "Retype new password" and then "failed to find entry for <user>"

I am a complete newbie so no idea what is going on here
when you put a password in the terminal, it doesn't display '*'s for the keys you hit. it looks like you aren't typing, but it is listening.
the  "failed to find entry for <user>" usually implies that there is no unix user on the server box with that username. jsut to clarify, you did replace <user> with the name of your user, right? traditionally command elements that are in <> indicate that you need to replace the value with a real value, such as a username.

so lets say i have a client user account called 'bob' that needs to access files. I first need to create a linux/unix user account for the user, named 'bob' with teh same password as is used on the client. 
then after setting up the user, I would enter the command:
```
sudo smbpasswd bob
```
and follow the prompts.

---

### Post by archkidd on 2010-05-04
I did enter my  username (as is shown at the top right panel). This time I went through the type new password and retype and then it just went back to the standard terminal prompt.
I did not know what SAMBA was until you mentioned it and so have looked it up since.  Is this different from 9.4?  Is it not installed as standard in 10.04?  I don't understand why it worked so seamlessly before and not now.  Thank you for your patience.

---

### Post by doas777 on 2010-05-04
to he honest, there is a lot of confusion about samba currently, because of a switch between the new and the old paradigms. since you say "seemless" I have to assume that you have been using the new samba-usershare system, as opposed to the older approach that i am most familiar with. in the old paradigm, you just install samba and configure the smb.conf file. 

in this case however i think you want to try this thread:
[http://swiss.ubuntuforums.org/showthread.php?t=1169149&highlight=browseable+smb](http://swiss.ubuntuforums.org/showthread.php?t=1169149&highlight=browseable+smb)
Dmizer is very knowledgable on the topic, as is Iowan, who I imagine will show up before too long.

---

### Post by archkidd on 2010-05-04
Thank you.  I will go there.  However, all I ever did in the past is just what it says in the 'SettingUpSamba' documentation (which I have only now found thanks to your reference), i.e. "Ubuntu and Gnome make it easy to access files on a Windows network  share. Open the **Places**  Menu, then click on **Network**. You will see a **Windows  network** icon. Double-click to open it. The next window shows  all the domains/workgroups found on your network."  That is it! All my files on my windows machine were just there.  The name of my ubuntu machine still shows on my windows computer but will not connect either. No idea that there was a smb.cnf file and certainly did not do anything with it.  Which is why I wonder what is different with 10.04.  thanks

---

### Post by archkidd on 2010-05-04
OK.  So here is my confession. When I added 10.04 I also added the GUFW firewall and guess what, it was doing its job and preventing connections.  Disabling that and lo and behold there are my files on the network.  I can't apologize enough for wasting your time. Reading the thread you referenced reminded me of the issues I have had with firewalls in windows and had not thought about with ubuntu.  Change one thing at a time!!

---

### Post by davec64 on 2010-05-04
> **archkidd said:**
> OK.  So here is my confession. When I added 10.04 I also added the GUFW firewall and guess what, it was doing its job and preventing connections.  Disabling that and lo and behold there are my files on the network.  I can't apologize enough for wasting your time. Reading the thread you referenced reminded me of the issues I have had with firewalls in windows and had not thought about with ubuntu.  Change one thing at a time!!

Archkidd, I had to chuckle! I think everybody has done that at some point! :lolflag:

---

### Post by doas777 on 2010-05-04
no doubt. i am the cause of many of the worst computer problems I've ever had.
I'm glad you got it worked out, and that it was something that could be easily fixed. 
cheers

---

