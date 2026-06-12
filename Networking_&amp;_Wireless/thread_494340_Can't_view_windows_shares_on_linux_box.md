---
title: "Can't view windows shares on linux box"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by kframe on 2007-07-06
Hi everyone, 
Well, I've finally got 2 out of 3 problems fixed.
I can now print from my Ubuntu machine over the network to the USB printers on my XP machine.
After searching the forums I also got it so I can view the shared folder in the Ubuntu machine from the 3 PC's on my home net.  (2 XP machines and one Vista)

The third problem is stumping me.
From Places>Network I can view my PC's, named XP1, XP2 and Laptop (the Vista machine).
But if I double click on any of them the Ubuntu machine (LX1) thinks and thinks and then an error box opens stating "The folder contents could not be displayed. Sorry, couldn't display all the contents of "Windows Network: xp1"."
And in the backround, no files or folders appeared.

Are my PC's blocking out my Ubuntu machine, or do you think the problem is with the Ubuntu machine?

Please help, any advice will be appreciated!
Thanks, -Kris

---

### Post by kframe on 2007-07-06
Bumptity bump.
Can't anyone help?

Here's more details I found.

I CAN browse and manipulate files in my windows SharedDocs folder by using nautilus from the terminal.
I can also view the shares in the windows machine(s) by typing 
$ smbclient -L XP1 -U owner
or 
$ smbclient -L pc_ip_address -U owner

But still nothing happens except a lot of waiting and an error box if I try to open any of the PCs from Places>Network.

This is the same in root and in my usual user state.  

Arrgh, this is so frustrating!
Why would nautilus work but Network not?

Please help!
-K

---

### Post by drvista on 2007-07-09
me too i ahve the same problem plz help

---

