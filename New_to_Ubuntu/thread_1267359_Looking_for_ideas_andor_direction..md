---
title: "Looking for ideas and/or direction."
date: 2009-09-15
forum: New to Ubuntu
---

### Post by minutest on 2009-09-15
I am new to Ubuntu not a power user by a long shot at this time.

I want to block one of the users on my PC from going to internet site lets call it [www.stop](www.stop) going here.com.

Is there a way that I can block this user with out blocking all of the other users? Also will this require the installation of a firewall?

If a firewall will have to be installed as a last resort any ideas on a simple easy to use firewall as this is all I want to use it for at this time.

Thx for all of your help.

---

### Post by neurostu on 2009-09-15
There is a great firefox plugin called leachblock. You can install it on the users account and then block the user from accessing the plugin. You can even have it load a list of sites to block from the internet.

---

### Post by 73ckn797 on 2009-09-15
> **minutest said:**
> I am new to Ubuntu not a power user by a long shot at this time.

I want to block one of the users on my PC from going to internet site lets call it [www.stop]("http://www.stop") going here.com.

Is there a way that I can block this user with out blocking all of the other users? Also will this require the installation of a firewall?

If a firewall will have to be installed as a last resort any ideas on a simple easy to use firewall as this is all I want to use it for at this time.

Thx for all of your help.


You can try "gufw" from Synaptic. Ubuntu already has "ufw" (Ubuntu FireWall??) installed. gufw is a graphical interface for that.

---

### Post by winotree on 2009-09-15
**U**ncomplicated **F**ire**w**all [http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html](http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html)  ;)

---

### Post by 73ckn797 on 2009-09-15
> **winotree said:**
> **U**ncomplicated **F**ire**w**all [http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html](http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html)  ;)

Thanks. I was not sure so I guessed.

---

### Post by winotree on 2009-09-15
Guesses are good.  :D  But will this application do as you suggest?  If so, how?  Seems I've some reading ahead of me tonight!

EDIT - seems I made a mistake and owe an apology.  Found this in the wiki [https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

---

### Post by LewRockwell on 2009-09-15
> **minutest said:**
> I am new to Ubuntu not a power user by a long shot at this time.

I want to block one of the users on my PC from going to internet site lets call it [www.stop](www.stop) going here.com.

Is there a way that I can block this user with out blocking all of the other users? Also will this require the installation of a firewall?

If a firewall will have to be installed as a last resort any ideas on a simple easy to use firewall as this is all I want to use it for at this time.

Thx for all of your help.

[https://addons.mozilla.org/en-US/firefox/addon/4476](https://addons.mozilla.org/en-US/firefox/addon/4476)

.

---

### Post by Geoff918 on 2009-09-15
Why not edit the hosts file?

Just set the website address to loopback (127.0.0.1) OR if you want to bug him out set it to redirect to a page you've made that says "BIG BROTHER IS WATCHING. YOU'VE BEEN BLOCKED AND LOGGED"

Just some ideas, let me know if you need more direction on changing the hosts file.

---

### Post by neurostu on 2009-09-16
What the OP is trying to do is restrict page views for a specifi user. Installing a firewall or editing the hosts file will affect every user on the system.

A simple firefox addon will allow  the OP to do what they want. A firewall is not what is wanted. 

Firewalls are used to block ports, all unecrypted internet traffic is usually on the same port.

---

