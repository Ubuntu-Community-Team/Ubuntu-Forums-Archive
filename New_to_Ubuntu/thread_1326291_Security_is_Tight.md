---
title: "Security is Tight"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by JREAM on 2009-11-14
Hey guys i am new to linux but I had a VPS for a month, so 2 days into ubuntu and I like it so far, it's very impressive!

0 -- One thing that bothers me are these security warnings always telling me to check a password, yadda yadda. Im the only one using this computer is there any way to make this system chill out?

1-- i cant edit like an httpd.conf file, I have to go through shell and do sudo gedit /etc/apache2/host.conf -- is there another way to edit this through the file browser?

2 -- Is there a way to assume im always root? I do sudo su, but sometimes the session expires. "Authenticatioin required to install, etc" Im so tired of typing my password in :(

[SOLVED] 3 -- For some reason GIMP wont load for me, I installed and untinstalled, it opens the "Loading" window, but then closes adn does nothing, am i missing somthing..  ** It appears I have something called GIMP SHOP installed thats being funny


Thanks you guys.

---

### Post by Paqman on 2009-11-14
> **JREAM said:**
> 
0 -- One thing that bothers me are these security warnings always telling me to check a password, yadda yadda. Im the only one using this computer is there any way to make this system chill out?


Firstly: lol, maximum geek cred for numbering your bullet points from 0.

Secondly: you'll just have to get used to putting your password in. File permissions are an integral part of Linux, and one of there reasons we have top-notch security. You can end up punching in your password a lot when you're setting things up, install, etc, but in general use it should be pretty infrequent.

Thirdly: you aren't the only user on your computer. If you're connected to the internet there are hundreds of millions of people and machines who have access to your box. Authenticating yourself as the ONE person out of those millions that your machine should trust is crucial.

> 1-- i cant edit like an httpd.conf file, I have to go through shell and do sudo gedit /etc/apache2/host.conf -- is there another way to edit this through the file browser?

Right click > Open with > Gedit. For files owned by root you can install the nautilus-gksu extension, which gives you an "Open as administrator" option in your right-click menu.

> 
2 -- Is there a way to assume im always root? I do sudo su, but sometimes the session expires. "Authenticatioin required to install, etc" Im so tired of typing my password in :(

See above, that's a security feature. You'll spend less time and effort putting in passwords in Linux than you would running malware scans in Windows, and you get peace of mind as an added bonus.

---

### Post by pootan on 2009-11-14
> **JREAM said:**
> 


1-- i cant edit like an httpd.conf file, I have to go through shell and do sudo gedit /etc/apache2/host.conf -- is there another way to edit this through the file browser?


If you install something called Ubuntu Tweak following the instructions here:
[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)

there is a list of right-click Open with.. scripts under the personal section  you can add to Nautilus. One of them lets you open a file with a text editor as root but you will still need to enter your pass to so.

There is also an option in the system section>nautilus to add the administrator function to nautilus as discussed above.

---

### Post by JREAM on 2009-11-14
Haha @ the number list, I got in the habit from PHP :P

Okay this seems all good, Im starting to figure things out slowly.
I will try out that nautilus-gksu thing and the Ubuntu tweak, thats exactly perfect.

Thanks you guys. I like gEdit also, good code editor it looks like

---

