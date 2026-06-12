---
title: "Dapper Dialup connection problem"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by King Donko on 2007-04-25
I am trying to set up my friend's computer to connect with a USR external serial modem. It seems to work fine, but when I try to connect it fails the login because it tries to enter the username as the password. The log says the following:

...Welcome
Please Sign-on:
--> Looks like a login prompt.
--> Sending: [username]
[username]
Name, password pair incorrect
Please Sign-on:....
....

Any help anyone can give me on this would be greatly appreciated!

---

### Post by mainely_linux on 2007-04-26
What program are you using to make this connection?

---

### Post by King Donko on 2007-04-26
I think it's called Gnome ppp. I tried to configure the settings with pppconfig also, but it didn't seem to have any effect.

---

### Post by mainely_linux on 2007-04-26
Have a look at wvdial.  I find its the easiest to troubleshoot as well as configure.

sudo apt-get install wvdial
sudo wvdialconf
sudo nano /etc/wvdial.conf
sudo wvdial

You can paste any errors here, and I can offer further suggestions.

---

### Post by King Donko on 2007-04-26
Thanks a lot for the tip Mainely. I'll try it as soon as I get home and let you know.

---

### Post by King Donko on 2007-04-26
I followed your directions, but I think I messed something up while entering the info on the wvdial.conf. I entered the phone #, username, and password, but when I try to run wvdial, it says Configuration does not specify valid phone number/login name/password. Do I need to put some character in front of/behind the info?

---

### Post by King Donko on 2007-04-26
I figured out the problem; I had "; " before the Phone, user, and pw. 

I removed those and tried again, but it has the same problem; sending the username as the username as well as the password. 

I've tried changing the echo setting on the modem, but it did the same thing, regardless of the program I use to dial up.

Has anyone seen this problem before?

---

