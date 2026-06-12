---
title: "Nm-applet keeps asking keyring"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by PrimaryMaster on 2008-11-08
Hi,

I am new to Ubuntu. I have the latest 8.10. nm-applet pops up at every bootup. I read the solution that included pam-keyring in [this thread]("http://ubuntuforums.org/showthread.php?p=2776815#post2776815"). I fire up xterm and enter sudo apt-get install libpam-keyring. The terminal gives me this message:

[IMG]http://farm4.static.flickr.com/3271/3014719615_8f713e74ef_o.jpg[/IMG]

It looks like it doesn't install, delete or upgrade anything. I understand that this means that i already have libpam-keyring. Right?

Then the solution asks me to input: sudo gedit /etc/pam.d/gdm 

I do that and the page pops up. There are some entries there and i add the following entry as the solution tells me to:

"@include common-pamkeyring"

I save and close the file. 


The solution goes on saying:

"this only works if your keyring pw is the same as your login pw. if it isnt, before doing any of this just delete your keyring -

Quote:
rm $HOME/.gnome2/keyrings/default.keyring
then reboot and connect to your wifi, it will have you reset your keyring, make it the same as your login pw. then do the steps above. now you shouldnt have to enter your keyring each time you connect to a wifi and if you turned on auto-login then you shouldnt have to enter anything at all, just enjoy"


Now my login password for the entire system is let's say JOHN. The keyring i enter to dismiss the nm-applet is also JOHN. So the above requirement is there right? I do all the above, disconnect, reboot and then at bootup nm-applet still asks for my keyring. 

When i upgraded to 8.10 the first time nm-applet popped up at bootup, the window said "nm-applet wants to memorize the keyring blah blah" and i thought "oh well, then this must have been fixed in this version since i will only have to enter once and it will memorize". BUT that wasn't the case.

What else can i do??

---

### Post by PrimaryMaster on 2008-11-09
I added a detailed explanation and maybe someone can now help. Thank you.

---

### Post by Martiini on 2008-11-10
to remove keyring password thing .. read this [http://ubuntuforums.org/showpost.php?p=6069702&postcount=3](http://ubuntuforums.org/showpost.php?p=6069702&postcount=3)

---

### Post by PrimaryMaster on 2008-11-12
Hmmmm... Thank you mate but that suggests to leave the keyring blank and that defeats one of the reasons of using Linux, security. 

Meanwhile i installed 8.04 and everything seems to work perfectly. Though i still need to test the headphone out. In 8.10 headphones and laptop speakers worked simultaneously and i wasn't able to fix it.

---

### Post by mothraman on 2008-11-15
The solution that worked for me may help. See:[http://ubuntuforums.org/showthread.php?t=983508]("http://ubuntuforums.org/showthread.php?t=983508")

---

