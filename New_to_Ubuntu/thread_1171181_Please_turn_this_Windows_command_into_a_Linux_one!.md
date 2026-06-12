---
title: "Please turn this Windows command into a Linux one!"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by zcacogp on 2009-05-27
Chaps, 

I work on a client site, and use my own laptop. 

I have installed Ubuntu on my laptop, and am trying to use it in place of the XP install I was using. This means I need to be able to make it do everything on Ubuntu that I could do on XP. 

When on aforementioned client site, I occasionally print to their printers. In order to do this, I run the following command (it's actually wrapped up as a batch file, to which there is a shortcut on my desktop): 

```
net use \\lbb1prnv /user:lbbarnet\<login> <password>
```

... where <login> is my login to the client's network, and <password> is the password I use. This, as I understand it, puts me onto their domain so that I can access their printers. 

I need something similar to run in Ubuntu to enable me to print ... so what should I type in the terminal to have the same effect? (And then I guess I will need to think about installing a suitable driver. That'll be a laugh!) 

All help welcomed ... thanks. 


Oli.

---

### Post by aeiah on 2009-05-27
it depends on whether you're talking about an active directory domain or just an smb (samba) domain. before getting into editing config files and running cli commands, have you tried connecting to the network through the gnome menu?

---

### Post by zcacogp on 2009-05-27
aeiah,

Thanks. 

'tis an Active Directory domain, that I know. 

What do you mean by "connect to the network through the gnome menu"? I am connected to the network (it provides the bandwidth to give me internet access, amongst other things, as well as running a citrix client), but this doesn't mean I am logged into the active directory in question. 

Did this make sense? 


Oli.

---

### Post by Rubicon_82 on 2009-05-27
> **zcacogp said:**
> 
I need something similar to run in Ubuntu to enable me to print ... so what should I type in the terminal to have the same effect? (And then I guess I will need to think about installing a suitable driver. That'll be a laugh!) 


CUPS supports printing to MS print servers assuming you have samba-common installed.  You should be able to add the printers you need using your preferred CUPS interface.  See here for adding a printer on a Windows share (The HowTo is aimed at home networks, but should be applicable to a business-scale network):
[https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter)

Note that many business grade printers will support protocols such as JetDirect, allowing printing directly to the printer's IP address, avoiding the need to use the smb interface.

---

### Post by fatality_uk on 2009-05-27
> **zcacogp said:**
> aeiah,

Thanks. 

'tis an Active Directory domain, that I know. 

What do you mean by "connect to the network through the gnome menu"? I am connected to the network (it provides the bandwidth to give me internet access, amongst other things, as well as running a citrix client), but this doesn't mean I am logged into the active directory in question. 

Did this make sense? 


Oli.


If your network uses ActiveDirectory, privileges etc are set on the sever and when a user logs in, those rights are transfered to that user.

In Ubuntu, if you go into the System->Administration-Printing menu and you are using the network, you should be able to see a view of all the printers in he network. Try this first. It is persistent.

---

### Post by fatality_uk on 2009-05-27
Also just found this.
[http://www.lockergnome.com/it/2005/01/31/control-printers-in-linux-from-the-command-line/](http://www.lockergnome.com/it/2005/01/31/control-printers-in-linux-from-the-command-line/)

---

### Post by zcacogp on 2009-05-27
> **fatality_uk said:**
> In Ubuntu, if you go into the System->Administration-Printing menu and you are using the network, you should be able to see a view of all the printers in he network. Try this first. It is persistent.Crumbs. To my slight surprise, that worked. And very easily as well. Admittedly, I have yet to try rebooting to see what happens then but I don't expect there to be problems. I wouldn't have been that surprised if what I was trying to do was impossible (well, beyond my capabilities, despite having the assistance of this forum). 

Thanks. My respect for Ubuntu grows. That would have been significantly harder in XP. Ubuntu will connect to it (a Windoze network) more easily than an XP machine will ... 


Oli.

---

