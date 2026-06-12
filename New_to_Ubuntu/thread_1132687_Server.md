---
title: "Server"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by Drenriza on 2009-04-22
Im intersted in setting up a ubuntu server, that can show my webpage on the web.

But how do you get started ,) i have downloaded the ubuntu server edition and installed it on a comp. But the server has no User interface, so is there a place with a guide to setting up the DNS, lamp and so on.

Is their a place where you can see a list with the driffent commands and what they do.

---

### Post by Kobalt on 2009-04-22
Here is everything you're looking for : [https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

---

### Post by Drenriza on 2009-04-22
I have readed a little. And as far as i can tell i need to install Joomla. But do you just install a ubuntu desktop comp, and then install this program on the disktop? or do you need to use the Ubuntu Server instead of the Desktop Model?

---

### Post by Penguin Guy on 2009-04-22
> **Drenriza said:**
> I have readed a little. And as far as i can tell i need to install Joomla. But do you just install a ubuntu desktop comp, and then install this program on the disktop? or do you need to use the Ubuntu Server instead of the Desktop Model?
If the computer is going to be used as a server, and only a server, then use Ubuntu server addition. Otherwise use desktop addition.

---

### Post by bodhi.zazen on 2009-04-22
You can install server software on a desktop.

typically people move to a dedicated server or a server in KVM / Virtualbox, but you may not be ready for that yet.

---

### Post by JK3mp on 2009-04-22
> **bodhi.zazen said:**
> You can install server software on a desktop.

typically people move to a dedicated server or a server in KVM / Virtualbox, but you may not be ready for that yet.

I second this. It would be much easier to just use desktop edition. Then later on as you get more traffic and more experience you may wanna get a box dedicated as a server only then worry about it. (Also check your ISP's Terms of Use, not all of them allow you to host a server since they can use alot of bandwidth and resources)

---

### Post by MN Noob on 2009-04-22
What are you trying to *show*? More than likely, all you will need is apache installed. (especially if you just want to use the server for html only and for non-commercial purposes) If I remember correctly, apache was pretty simple to do a basic configuration from the CLI. Otherwise, I recommend using webmin to do the configuring. From there, you can add whatever language you may use, php etc as well as any databases mysql...
But if you are having trouble, I would also recommend messing around with the desktop version. For me, I was forced to use CLI as my wife didn't want the computer lying around taking up space, so I had to put it somewhere inconvenient and disconnect the monitor.

---

### Post by nandemonai on 2009-04-22
Use a GUI until you're 100% comfortable with a command line only interface.

Best advice I can offer.

When doing the things you need to do with your server in the GUI think to yourself.. 'How can I achieve this with only terminal?'

Once you can answer that or find out by other means how to achieve what you need to do then you are ready for a headless CLI server.

---

### Post by Iowan on 2009-04-22
Since links are what I seem to do best, I'll offer a few...
[ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")
[ServerGUI]("https://help.ubuntu.com/community/ServerGUI")
[howtoforge.com]("http://www.howtoforge.com/howtos/linux/ubuntu")

---

### Post by Drenriza on 2009-04-23
Thanks for all the applies & advice. Im familiar with the command line interface(Windows), and i acctualy feel more "comfortable" in a command line then actual user-interface.

It's all down to the commands their is in the ubuntu server edition. I have switched to ubuntu for not so long ago, so it's "lerning by doing" so far.

So far i thanks for all the answers, links, advises.
And i will take it all into consideration.:KS

---

### Post by Drenriza on 2009-04-24
I have 1 question tho, if you install the ubuntu server edition and don't click to install addtional DNS, lampserver MySQL and so on. 

Can you then install them later on by the command line interface? or is this something you MUST do from the beginning.

Kind Regards
Dren

---

### Post by MN Noob on 2009-04-24
The only thing I install additionally is SSH. I have read on here to do it that way. I cannot remember the exact reason though.
Once Ubuntu is install, just ssh into the server and install the rest.

---

### Post by ephmanjmm on 2009-04-24
You don't have to install everything at the beginning.  You can use  tasksel for a convenient way to add features to your machine or sudo apt-get install <package>.

---

### Post by Drenriza on 2009-04-24
Thanks for the quick answers.

---

### Post by bodhi.zazen on 2009-04-24
If you are just starting, the server edition will offer you the opportunity to install LAMP.

I would go with that option.

As you get more experience you may wish to simply install a minimal installation and then install only what you wish. This tends to be a lighter , more custom install.

---

