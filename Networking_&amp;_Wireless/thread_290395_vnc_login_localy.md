---
title: "vnc login localy"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by halitus87 on 2006-11-01
hello i want to do something and i duno how

i have been playing with vnc and am liking it alot  but it does have limitations

what i want to do 

when remote desktop is loged out
i want to connect via vnc and login localy then control that session

what i can do is at any time connect and start a new session
or connect and view a local session which has already been loged in  via :1 and :0 respectivly

i would dearly love to be able to start a local session and view it so i can remotly shut down the pc via gui and change things  on the screen remotly


thank you all very much

---

### Post by jsandys on 2006-11-01
> **halitus87 said:**
> ...
what i want to do when remote desktop is loged out i want to connect via vnc and login localy then control that session

what i can do is at any time connect and start a new session
or connect and view a local session which has already been loged in  via :1 and :0 respectivly

How do you connect and start a new session?  With telnet?

My guess is a two step process, connect with telnet and startx, then connect with vnc.  vnc needs an xserver to tap into.

I'm trying to do a similar thing and don't have an answer yet.  
Can you export a display in Linux, in Unix I use the command "xhost +" to export the display to my local terminal.  
When I am using vnc I am able to shutdown the remote computer.

---

### Post by halitus87 on 2006-11-01
i havent been using telnet at all just vnc 
basicaly i want to login to the physical display :0  before the pc has been loged into a session

im trying to get to ubuntu from ubuntu

what im trying to get  is that i can remotly boot it via magicpackets which isnt to hard
then it gets to the gdm login screen  i want to connect to that and then login do my stuff then shut it down if i need to

thanks

---

