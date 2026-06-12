---
title: "Stuck in recovery mode, ubuntu 9.10 wont boot"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by Damonny27 on 2010-12-18
Hi, there are beginners and then there is me:(
  Am using ubuntu 9.10 on my acer aspire one. During a regular update i got this message " configuration defaults for gnome power manager not installed properly" My acer note book refused to boot and i had a blank screen. After googling the problem i was able to boot my note in failsafe Gnome mode etc.
   Since a few days back it started giving problems again and i used the ctrl+alt+F7 and i used to be able to boot in recovery mode.
 Now since yesterday when i try to do that it starts normally as it would, asks for my user name and password to log me in and then i get this message " 52 packages can be updated. 46 updates are security updates "

  Under that is user@whatever: ~S

  I don't know what to type in there to get out and continue in recovery mode.:confused: I tried Sudo/etc/init.d/gdm start and that just takes me to a blank page where i get the old message " configuration defaults for gnome power manager not installed properly" and i am stuck there with a blank screen.

---

### Post by jtarin on 2010-12-18
Did you try sudo apt-get update?

---

### Post by Damonny27 on 2010-12-18
Yes i have and this is what i get.

W: Failed to fetch [ security.ununtu.com/dists/karmic-security/universe/i18n/Translation-en_US.bz2]("http://security.ununtu.com/dists/karmic-security/universe/i18n/Translation-en_US.bz2") Could not resolve ' security.unbuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.

and then there is 

user@whatever: ~S

 And i am stuck in that place, dont know what command to give after this

---

