---
title: "Wireless problem with cloned computers. Cloning may affect to network connection?"
date: 2018-03-15
forum: Networking &amp; Wireless
---

### Post by planpc on 2018-03-15
Hello, recently cloned about 10 computers, installed and configured Ubuntu 16.04 in one of them, then clone the hard disks y after, configure everyone of them with particular information:

/etc/hostname change the computer name

/etc/samba/samba.conf  (Maybe that is not the real name, cant remember now). Changed workgroup name, and change to yes use WIN server as they are in a Windows scenario.

Anyone knows if is there anything mus be changed/updated after cloning ubuntu? Im having many problems (wireless) and I think after many tests, that could be the only thing to consider.

I appreciate any help, I'm pretty good at windows, which is totally useless in linux ...

---

### Post by TheFu on 2018-03-15
/etc/hosts needs to be changed.
Also, the udev rules need to be cleared for network adapters.  /etc/udev/rules.d/70-persistent-net.rules

Yes, Windows knowledge isn't helpful, and sometimes terrible for understanding how pretty much every other OS in the world works. Every popular OS used in the world that isn't Windows, is based on Unix.

There is a tool for doing these things, btw.   It is named from the MSFT tool for a similar purpose.  I can't remember the name now ... sysprep ... perhaps?  [https://askubuntu.com/questions/428027/how-to-sysprep-ubuntu-to-take-its-image](https://askubuntu.com/questions/428027/how-to-sysprep-ubuntu-to-take-its-image)  - perhaps it is only useful for virtual machines.  The documentation does describe what it does, which would be germane to your needs.

---

### Post by planpc on 2018-03-16
Thank you for your help TheFu.

at the host file, I´d changed computer name, the second part is refered to IPv6 is as it was, I souposed it must or it can keep like it is. No IPv6 configuration is working at this place at this time:
[ATTACH=CONFIG]278966[/ATTACH]

The second part you mention, is somethig I had read before, somewhere in the forum looking for info, but at none of the 10 cloned computers, exists any other file, no one related to network but one related to the Interactive Board (touch screen) present in every computer cloned, as they are in classrooms at school.

Maybe is the 70-persistent-net.rules you say, is what the computers need to run wireless network without problem?

[ATTACH=CONFIG]278965[/ATTACH]
As a point, I may say that cloned computers that are conected to network though cable, have no problem getting a DHCP Ip, nor surfing web or the local network, problem its only wirelessly.


And thank you for share your vision, you also help me to see from another perspective and not only the one I am accustomed to see. Never forget what you said "Every popular OS used in the world that isn't Windows, is based on Unix."





QUOTE=TheFu;13748563]/etc/hosts needs to be changed.
Also, the udev rules need to be cleared for network adapters.  /etc/udev/rules.d/70-persistent-net.rules

Yes, Windows knowledge isn't helpful, and sometimes terrible for understanding how pretty much every other OS in the world works. Every popular OS used in the world that isn't Windows, is based on Unix.

There is a tool for doing these things, btw.   It is named from the MSFT tool for a similar purpose.  I can't remember the name now ... sysprep ... perhaps?  [https://askubuntu.com/questions/428027/how-to-sysprep-ubuntu-to-take-its-image](https://askubuntu.com/questions/428027/how-to-sysprep-ubuntu-to-take-its-image)  - perhaps it is only useful for virtual machines.  The documentation does describe what it does, which would be germane to your needs.[/QUOTE]

---

### Post by TheFu on 2018-03-16
Best to completely disable IPv6 if you aren't ready for it, especially at the router. It can be a huge security hole.  Definitely disable IPv6 on any Windows machines!!!

I don't do images. Sorry.

Wireless - don't have a clue.  I avoid wifi for all computing if there is **any** other choice. Wifi sucks, generally. It is barely good enough for lite browsing and email.  I have lots of wifi experience, professionally.  I use a USB-to-GigE adapter on my chromebook, to avoid wifi.

When there isn't any choice except wifi, I purge network-manager and use wicd-curses to manage the connection.  Network-manager and avahi burned me a few yrs ago, so it is just easier to purge them off the systems. 

I also purge bluetooth-everything.  Got hacked over a bluetooth connection once. Never again.

I purge  lots and lots of default packages that ubuntu includes, even in their minimal installs, though most are just storage eating, not sucking CPU, RAM or causing other issues like NM and avahi can.  The flexibility of Linux lets me have the system **I** want, not what Steve or Bill or Mark or Satya or Tim think I should have.  Today, Ubuntu is the system for least hassles, to me. It has been my choice since 2008-ish.  That can change, though including the amazon buttons on their minimal install in the 18.04 alphas has been less than ideal to me. I generally don't use Ubuntu desktop - too bloated for my likes. Clear Linux, from Intel, has been near the top of all the Linux server benchmark tests I've seen. Most of my Linux systems aren't desktops, so having a fast, lighter, server distro is interesting.  There are trade-offs, of course.

---

