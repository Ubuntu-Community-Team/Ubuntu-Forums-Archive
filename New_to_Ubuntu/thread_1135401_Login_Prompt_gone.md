---
title: "Login Prompt gone"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by ad5os on 2009-04-24
Hi... Just did an upgrade and it asked if I wanted to upgrade from 8.10 to 9.04 and I said sure.

The thing downloaded all night and I woke up to a question about replacing gwm I believe.  I said sure.... 

Then it said only a partial install could take place and that the upgrade didn't quite go all the way... No big deal I think it is because I have some 3rd party repositories and latest versions of like firefox and opera and skype stuff.  

So now when x starts all I get is my pretty "busy" mouse with no control and no login window.  I can log in fine on a terminal but not in x... 

I am sure it is just a line of script somewhere that I need to edit..

Any help?

---

### Post by LowSky on 2009-04-24
in terminal run

sudo apt-get update

then 

sudo apt-get upgrade

---

### Post by ad5os on 2009-04-24
yea I already tried that.... it doesnt upgrade 300 some odd packages... I guess I shouldnt have hit that upgrade button now! :P 

I think it is something to do just with xserver....  the cursor loads up but I get no response.. it is just hanging there.. no background nothing.  cant restart the xserver either... just switch to a text term.  

could it be something with the GWM?

---

### Post by Peter09 on 2009-04-24
No disk activity?

---

### Post by ad5os on 2009-04-24
when I do an update on apt-get I think all my other repositories are screwing it up.... when I do an upgrade it says 0 upgraded 0 newly installed and 321 not upgraded.  

looks like it wont upgrade any of the xorg stuff.

Can I roll back some of the upgrades.... or would a REINSTALL really mess things up?  I dont know if thats all that much different than upgrade.

---

### Post by ad5os on 2009-04-24
also when I apt-get update I get a lot of failed to  fetch and GPG errors  I think it is cause I used all those 3rd party repositories with Ubuntu Tweak.  can I degrade back to 8.10?

---

### Post by Peter09 on 2009-04-24
Can you not comment out your additional repositories on a temporary basis.

Edit /etc/apt/sources.list

---

### Post by ad5os on 2009-04-24
alright I did that  I am doing a apt-get dist-install  So thats gonig to take a while.. let you know if it worked or not..

---

### Post by ad5os on 2009-04-24
FIXED:

after doing the sudo apt-get dist-install  I booted in recovery mode and ran fix packages or something like that.... SO  now its working and all my settings are still there AND it is fully 9.04  thanks guys

---

