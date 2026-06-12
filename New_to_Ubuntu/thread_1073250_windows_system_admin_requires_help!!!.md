---
title: "windows system admin requires help!!!"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by leeroyrichardson on 2009-02-18
Hello forum,

I am a windows system admin new to ubuntu and keen to get to grips with the o/s.

I have installed 8.04 successfully on a laptop and have been working with it for a few weeks. However, there are certain issues which may force me to give up my learning curve with ubuntu.

The most important being my unsuccessful attempts to install a vpn client. I administer a windows 2003 domain and its obviously important I have the ability to connect to a cisco vpn concentrator, unfortunately despite numerous attempts I have not been able to get the vpn to work, like I said I am new to ubuntu so its probably me who has made an error.

Can anyone help with a step by step guide as to how I can install a client??

providing I can logon to the workplace I will be able to continue my ubuntu experience.

with thanks

---

### Post by Pollox on 2009-02-18
Check out vpnc.  If you want a gui interface to it, use network-manager-vpnc .  The gui is fairly straightforward, but there's a decent guide to it here: [http://www.alterego7.com/2008/02/vpnc-in-ubuntu.html]("http://www.alterego7.com/2008/02/vpnc-in-ubuntu.html").

---

### Post by Nepherte on 2009-02-18
I suggest you perform a search in the Tutorials & Tips section of this forum. There should be enough information to help you out: [http://ubuntuforums.org/search.php?searchid=55823773](http://ubuntuforums.org/search.php?searchid=55823773)

---

### Post by Metallion on 2009-02-18
I second vpnc. Type this command in a terminal:

```
sudo apt-get install network-manager-vpnc
```

Now you can left click on your network manager applet and go to vpn connections.

---

### Post by beowulffe on 2009-02-18
thanks!

i did that now what to i need to do?

---

