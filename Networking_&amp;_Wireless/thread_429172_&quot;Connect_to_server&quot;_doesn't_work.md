---
title: "&quot;Connect to server&quot; doesn't work"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by d3dtn01 on 2007-05-01
I'm trying to reestablish an SSH connection to another PC on my home network. I went to Places > Connect to server... and filled out the data like I've done before:

Service Type: SSH
Server: [the IP addr of the target PC]
Port:
Folder:
User Name: [my name]
Name to user for connection: compaq

Then I click connect. This places a folder icon on my desktop but does nothing else. So I double clicked on the folder and I get the message:

"Opening compaq.
You can stop this operation by clicking cancel."

But nothing else happens. Can you remind me what to do at this point. I can SSH the PC via the terminal, but I'd like to have a directory view.

---

### Post by d3dtn01 on 2007-05-01
Well, it did it again. After booting anew today, my connection to my other linux box (via the "Connect to server" folder that was created on my desktop) doesn't seem to work. I get that message: 

"Opening compaq.
You can stop this operation by clicking cancel."

but nothing happens after that. It never opens.

Ideas?

---

### Post by wilberfan on 2007-07-17
> **d3dtn01 said:**
> I'm trying to reestablish an SSH connection to another PC on my home network. I went to Places > Connect to server... and filled out the data like I've done before:

Service Type: SSH
Server: [the IP addr of the target PC]
Port:
Folder:
User Name: [my name]
Name to user for connection: compaq

Then I click connect. This places a folder icon on my desktop but does nothing else. So I double clicked on the folder and I get the message:

"Opening compaq.
You can stop this operation by clicking cancel."

But nothing else happens. Can you remind me what to do at this point. I can SSH the PC via the terminal, but I'd like to have a directory view.

I've been having this exact problem for a couple of hours now!!   I'm trying to connect between two Feisty boxes.....    I've gotten SSH to work GREAT before--but I can't remember how, exactly...  (Newbies!)   What could be going on here?!    :confused:

---

### Post by Herman on 2007-07-18
SSH remembers every computer you have connected to and if something has changed, it gets suspicious and won't make the connection.
Maybe your router or ADSL modem has been reset or the IP addresses of your computers have changed since last time you connected.
If you are sure the connection is safe, (on a home LAN it would be), just open your /home/username directory and click 'view'-->'show hidden files.
Look for a file called .ssh and delete it. Then empty you trash to make sure.
Then try the connection again and it should connect as a first time connection without any trouble. A fresh new .ssh directory will be automatically regenerated for you at the same time.
If the same thing keeps happening, maybe try setting  static IP addresses, but that depends on other details about your network that I haven't been told about yet..

Regards, Herman :)

---

