---
title: "Help needed to edit    /etc/icecast2/icecast.xml"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by Peterfc on 2011-05-22
I am trying to edit /etc/icecast2/icecast.xml so i can setup an online radio station. 

I am using a site and i have enclosed a link below. The text below is where i need help with. When i go to /icecast.xml and right click then permission i get a message. You are not the owner, so you can not change these permissions.

Thanks for reading my request for help.

Configure icecast2

The icecast2 config file is located at /etc/icecast2/icecast.xml. The default configuration is very usable, so we'll only change the passwords. Take your favorite text editor and open /etc/icecast2/icecast.xml. Change the default passwords for source, relay and admin. The source password is used by ezstream to feed mp3's to icecast2. The admin password is used for the admin web interface. An example file is attached at the end of this post.


[http://koorenneef.nl/content/run-your-own-online-radio-station-icecast2-and-ezstream-howto](http://koorenneef.nl/content/run-your-own-online-radio-station-icecast2-and-ezstream-howto)

---

### Post by Lateralis on 2011-05-22
To edit files outside of your home (and I think /opt) directory you need root privileges.  If you would like to edit this particular file using gedit as root, type

```

gksudo gedit /etc/icecast2/icecast.xml

```

into a terminal.  You will be asked to type in your password in a GUI box, after which you will be able to edit and save the file.  

I don't see anywhere on that page instructions on changing the permissions of the file, but if you do need to do that (think carefully before you make such changes) then see the [manual page]("http://ss64.com/bash/chmod.html") and [this tutorial]("http://catcode.com/teachmod/chmod_cmd.html") on the chmod program.

---

