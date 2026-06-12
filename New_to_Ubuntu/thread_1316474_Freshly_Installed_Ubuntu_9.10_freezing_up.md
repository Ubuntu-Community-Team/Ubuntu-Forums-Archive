---
title: "Freshly Installed Ubuntu 9.10 freezing up"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by gribbsy on 2009-11-06
Hello.  I am running a dual boot with Windows XP and Ubuntu 9.10.  I have a Gateway Computer with a 2 GHz processor and 1.25 GB of RAM and a 40GB hard drive.  My video driver is an integrated Intel variety.  

I went to Salimane Adjao Moustapha's web site:

[http://theindexer.wordpress.com/2009/10/25/to-do-list-after-installing-ubuntu-9-10-aka-karmic-koala/](http://theindexer.wordpress.com/2009/10/25/to-do-list-after-installing-ubuntu-9-10-aka-karmic-koala/) 

and copied and pasted all of his post-installation commands into my terminal to run them.  Not sure if this guy knows what he is doing or not.  He seems very intelligent and has a lot of good feedback on the site.  Basically he seems to be upgrading/updating everything and adding apps for Video, Music, Utilities, Antivirus/Firewall, Open Office, GIMP etc...

Somehow my screen freezes up on a regular basis.  I can't mouse click on anything and CTRL+ALT+F2 doesn't bring up an instance of my terminal so I can't kill the offending process.  It also freezes up sometimes when I first power it up.  In any event, my only recourse is to pull the plug on my computer and reboot.

Any suggestions?  I've tried re-installing 3 times already and the problem remains.

---

### Post by SunnyRabbiera on 2009-11-06
Do you know your exact intel vid card model?
I know some intel vid cards dont behave well in linux.

---

### Post by jbrown96 on 2009-11-06
could you post the output of the following commands? Pro tip: install xclip and it will make copying all that data much easier. It allows you to re-direct console output to your clipboard.
```
sudo apt-get install xclip
``` Then post these ```
lspci | xclip -selection clipboard
``` ```
cat /var/log/Xorg.0.log | xclip -selection clipboard
``` and ```
cat /var/log/kernel | xclip -selection clipboard
``` After each command you can paste it with ctrl+v.

---

