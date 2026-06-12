---
title: "SSH, VNC, Lucid to Leopard - help"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by ChazzR on 2010-06-07
I am fairly new to the entire Ubuntu world (hence the noob area of the board) and I was hoping for some help. After doing a good deal of Google searches and reading I thought I would just ask for help. 

I have built a home server (old Windows desktop with two mounted drives) that runs Lucid and talks to a host of Mac machines. I use a MBP running the latest version of Snow Leopard as the main control point. The server will eventually be headless and kept in closet. 

Current Status: access both mounted drives from all the mac machines, play music in itunes and movies etc that are all stored on the media server. I can also vnc into the server from my mac as well. I have key chained the passwords and have no issue with any of my macs recognizing the drives when they start. 

I have also installed openssh on my main Mac and on the server as well. I can establish and ssh connection with X11. I am a bit confused here once I establish the connection from my MBP to the Server (in command terminal) I'm not sure what I'm supposed to be doing once connected. 

I have also created dsa keys with my MPB but cannot locate the file location that the output provided in command terminal and have no idea why.

Do I need to constantly have an SSH connection running if my server and macs are all connected on the same network? Is SSH only necessary if I am remote (ie not on my home network)? 

Is there a guide (with screen shots) that will walk a noob through the proper steps to set up ssh? I get ssh provides security but I just don't understand how to use the keys (public and private), how to know if it's working etc. 

Once I know how to do it, will the replication be the same for my other computers. On one of my computers I have multiple profiles does this make a difference?

Any help would be greatly appreciated. 

Thanks!

---

### Post by yeats on 2010-06-07
> I have also installed openssh on my main Mac and on the server as well. I can establish and ssh connection with X11. I am a bit confused here once I establish the connection from my MBP to the Server (in command terminal) I'm not sure what I'm supposed to be doing once connected. 


All SSH does is give you a way to log in remotely (i.e., from another computer, not necessarily away from your home network) and have a terminal connection (or X connection if necessary).  If you're going headless, you'll need that to be able to administer your server.

> I have also created dsa keys with my MPB but cannot locate the file location that the output provided in command terminal and have no idea why.

There will be a hidden directory in your /home/*yourusername* directory (where *yourusername* is your actual login name) called ".ssh" (with a dot in front - the dot is what makes it hidden).  Your SSH keys and hosts will be in that directory.

> Do I need to constantly have an SSH connection running if my server and macs are all connected on the same network? Is SSH only necessary if I am remote (ie not on my home network)?

No, you can just log in with SSH whenever you need to.  Unless you set up port forwarding, you won't be able to access the server from outside your network, assuming you are working behind a firewall, which you should be.

> Is there a guide (with screen shots) that will walk a noob through the proper steps to set up ssh? I get ssh provides security but I just don't understand how to use the keys (public and private), how to know if it's working etc. 

If you're able to log in without typing a password, keys are working.  SSH itself does not provide overall security for your server.  What it does is provides you a secure method for accessing your server.  You might benefit from reading the built-in documentation by doing

```
man ssh
```

in the terminal.  There are many guides on the web about it.  An "ssh debian" Google search should get you a lot of useful information.

---

