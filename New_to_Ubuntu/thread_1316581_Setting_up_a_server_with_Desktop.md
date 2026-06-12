---
title: "Setting up a server with Desktop"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by RichardCL on 2009-11-06
Hi Forum

So I finally took the plunge. I'm going to move my web, mail CMS and contacts server in house (LAMP for web, Zimbra for mail, VTiger CMS and LDAP for contacts).

I've played with these on an old laptop for a while using a desktop version of Ubuntu as a starting point and can get them to work, I think.

Now I've got dedicated hardware (Atom 330, 4GB Ram, 1TB SATA, GB LAN). I'm tempted to install desktop Ubuntu because I like the speed of Nautilus for moveing files and could use Firefox on the server to download the necessary installations.

Is there a good reason to use "server" Ubuntu instead of "desktop"? I suppose there must be but it isn't obvious.


TIA


Rich

---

### Post by majesticturkey on 2009-11-06
> **RichardCL said:**
> Hi Forum

So I finally took the plunge. I'm going to move my web, mail CMS and contacts server in house (LAMP for web, Zimbra for mail, VTiger CMS and LDAP for contacts).

I've played with these on an old laptop for a while using a desktop version of Ubuntu as a starting point and can get them to work, I think.

Now I've got dedicated hardware (Atom 330, 4GB Ram, 1TB SATA, GB LAN). I'm tempted to install desktop Ubuntu because I like the speed of Nautilus for moveing files and could use Firefox on the server to download the necessary installations.

Is there a good reason to use "server" Ubuntu instead of "desktop"? I suppose there must be but it isn't obvious.


TIA


Rich

I don't work with dedicated servers, I've only rented server space with shell access. But if you think Nautilus is fast, try the mv command. Getting used to a CLI has a ton of benefits, including the ability to move and copy files all over the place so much faster than using a GUI. If you really need a web browser, there are several powerful command-line browsers. Lynx is great.

I think you probably know better than me that using the desktop version of Ubuntu is using resources that could be better suited toward anything else. And really, for most things you get on a desktop environment, you can do it from the command line as well.

---

### Post by nothingspecial on 2009-11-06
You can ssh into your remote server using nautilus on your remote machine using the connect to server option in your places menu.

Download stuff using wget. So browse to a download link on your laptop, right click on the link and choose copy link location. Then ssh into your server and type wget then press Ctrl Shift and V.

---

### Post by jimmy the saint on 2009-11-06
The server addition is designed to make it easy to get a server up and running quickly.  It has quick selections at installation for a lot of server tasks (Lamp for example).  It also has a kernel that is slightly different.  I would go with the server addition and add a light desktop to it if you really feel the need.  

Start with this guide.  Read it first, decide which parts you need and just work on those.  You might consider something like openbox as opposed to gnome as it is far lighter and you can always add a file manager like pcmanFM or even nautilus to it.  pcmanFM doesn't have all the gnome dependencies so it will keep your system running light as a feather.

[http://www.howtoforge.com/perfect-server-ubuntu-9.10-karmic-koala-ispconfig-2](http://www.howtoforge.com/perfect-server-ubuntu-9.10-karmic-koala-ispconfig-2)

---

### Post by RichardCL on 2009-11-06
OK, thanks for the tips. I guess I give it a try with the server edition then. I'm planning to remove the keyboard and monitor anyway when it is up and running It was just a case of making the setup as easy as possible.

I'll look for a way to use remote desktop/ssh to control the server from the more powerful desktop. I've used Putty on Windows so it should be easy enough.

---

### Post by RichardCL on 2009-11-09
Server is up and running without monitor. I'm currently using putty and passwords to access for commands and nautilus for file transfer by SSH. I'm probably going to change to keys instead of passwords soon.

LAMP is running almost out of the box. FTP and printing is next.

Thanks for all the help.

---

