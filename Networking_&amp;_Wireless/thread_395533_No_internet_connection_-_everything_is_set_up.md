---
title: "No internet connection - everything is set up"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by Seph2409 on 2007-03-28
Dear Ubuntu Forums,

I have set up my installation of Ubuntu 6.10 to connect to my router and have input the correct settings (Password, the lot) and my signal meter has turned green. However, when I try to use any internet application, it immediately fails to connect. Gaim messenger doesn't even seem to try and connect to the hotmail server and Firefox says "Server not found" to any website.

Any help would be most gratefully received,

Seph

PS:
When I launch the network-admin application through the terminal, I get the following error a lot of times:

```

** (network-admin:5716) : CRITICAL **" gst_xml_element_find_first: assertion 'parent ! = Null' failed

```

---

### Post by Paul41 on 2007-03-28
You can try to blacklist IPv6 to see if that helps.

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)

---

### Post by Seph2409 on 2007-03-28
Thank you for your suggestion. I have tried the technique suggested on the page which you linked to, and another suggestion involving a blacklist elsewhere on the forum. It seems to have worked because when I run "ip a | grep inet6" in the terminal, I don't get any output. It says n "Networking tools" however, that the connection is using IPv6, when it should be trying to connect with IPv4.

There must be something amiss with the Networking as a whole, because there are several issues:

- I can't boot up the laptop with the Wireless card plugged in. It will hang directly after the login screen (a maroon page with just the mouse)

- Doing pretty much anything in "Network settings" takes a very long time. I'm forever waiting for "Activating Interface" or "Changing Location" or some such. These tend to take 30s to a minute. Doing anything with networking causes the computer to crash quite frequently, nothing else seems to have this effect.

- The only time I can plug the wireless card into the laptop is when no "interfaces" file exists at /etc/network/. I have to remove this and reboot each time it crashes to try again. If I plug in the wireless card while the interface file is present, nothing will launch at all. "Starting ***" will appear in the taskbar and then dissappear. I have to hold down the power button to turn it off.

Please can somebody give me a hand with this networking issue? I really have no more ideas.

Thank you,

Seph

---

### Post by Floppyjoe on 2007-03-28
This might be a DNS problem. Can you ping any servers(IP addresses) using System/Administration/Network Tools? If yes can you ping hostnames(eg. ubuntuforums.org)

---

### Post by tstavely on 2007-03-30
I'm having a similar problem with network-admin, with a similar xml-related error message (though on a different line number).  It started after I tried to put in info about different networks I log in to with my wireless.  The process was confusing because each time I created a network connection the tool tried to connect to it, even though that network was miles away.  The result was I eventually aborted the whole process -- plus i'd finished my coffee and needed to leave the coffeeshop.  Now somehow things write to and corrupt my /etc/network/interfaces file, Gnome won't boot (luckily I have two other window managers installed) and now I get network-admin "quits unexpectedly" so I can't get to it and delete the corrupt network designations.  And I don't know where the configuration file is to edit it manually and fix things up.

I think the next step is apt-get remove ubuntu-desktop --purge, or whatever the syntax is.  Get rid of all the bad stuff and reinstall if I'm willing.  Some KDE programs do better than Gnome, some Gnome programs do better.

Tony

---

### Post by Franscisco on 2007-03-30
I have a different question. I am a new Ubuntu user and I am getting DLS for the first time, so I really would like to know what is the process to have my internet service ready. I already have my Verizon packet, so I just need a little extra help.

---

