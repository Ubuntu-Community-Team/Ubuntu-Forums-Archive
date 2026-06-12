---
title: "Server Notifications to Clients?"
date: 2013-10-24
forum: Networking &amp; Wireless
---

### Post by lisanels47 on 2013-10-24
I'm trying to find a program for the Ubuntu Clients that will pop up a message on the Unity screen that can be sent to all clients or specific ones.

For example, when I'm going to restart the server, I'd like to issue a message to all clients on the network that the server will be restarted, and have a message window pop up for all the users.

It would also be nice to be able to open such a window for a specific client.

Thanks,
Lisa

---

### Post by papibe on 2013-10-24
Hi lisanels47.

A few thoughts:
[LIST]
[*]If all clients will have a terminal with a remote session open on the server, you can use something simple like 'wall'.
[*]There's no simple solution for the GUI, but here are a couple of ideas:
[LIST]
[*][*]Since you would need to run a command on a remote machine that will execute code on the clients, you need either a service or grant remote access to them.
[*][*]For a service, I'd take a look at puppet (although this is kind of an elephant killing a fly).
[*][*]You could grant remote access to the client machine using a passwordless ssh key to run a script on the clients.
[*][*]As for the specific tool to display the message, I would recommend notify-send. For instance:
```
 notify-send -i face-devilish "SERVER:" "shuting down in 5min."
```
[/LIST]
[/LIST]
Also, don't forget simple things like:
[LIST]
[*]Send an email, or
[*]a group text message.
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

---

### Post by SeijiSensei on 2013-10-24
This is generally a difficult problem on mixed networks.  We generally either send a warning email or make a announcement over the public address system if one exists.  Oftentimes the internal phone system is your best bet.

---

