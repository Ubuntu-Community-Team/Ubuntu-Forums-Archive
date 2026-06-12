---
title: "pptpconfig gui"
date: 2005-04-23
forum: Networking &amp; Wireless
---

### Post by njwetsu on 2005-04-23
I tried to use the [http://pptpclient.sourceforge.net/howto-debian.phtml](http://pptpclient.sourceforge.net/howto-debian.phtml) info which referes to a site to add to /etc/apt/sources.lis, but the site doesn't seem to exist anymore "http://quozl.netrek.org/pptp/pptpconfig". Does anyone know of a place new place or is having the same problem?  ](*,)

---

### Post by notzac on 2005-04-23
You shouldn't have to add anything to your sources.list -- the pptp-linux package is in the Ubuntu main repository. Just try running 'sudo apt-get install pptp-linux' :)

---

### Post by NewbieNik on 2005-04-25
You are correct about the pptp-linux package, but there isn't the pptpconfig package which I found to be a perfectly written configuration package for us newbies!!
If anyone knows where I can get the source or even an Unbuntu configured package I would be hugely grateful....Well, mildly pleased anyway. No kissing OK!!!

---

### Post by xristos on 2005-05-04
[QUOTE=njwetsu]I tried to use the [http://pptpclient.sourceforge.net/howto-debian.phtml](http://pptpclient.sourceforge.net/howto-debian.phtml) info which referes to a site to add to /etc/apt/sources.lis, but the site doesn't seem to exist anymore "http://quozl.netrek.org/pptp/pptpconfig". Does anyone know of a place new place or is having the same problem?  ](*,)[/QUOTE]
 Try this [http://quozl.us.netrek.org/pptp/php-gtk/](http://quozl.us.netrek.org/pptp/php-gtk/) and manually install th desired packages with dpkg -i .

---

### Post by njwetsu on 2005-05-15
I have tried " Try this [http://quozl.us.netrek.org/pptp/php-gtk/](http://quozl.us.netrek.org/pptp/php-gtk/) and manually install th desired packages with dpkg -i ."  but still can not get to the url to download the packages.  Is there just no pptp-config packages for for Debian (ubuntu/Kubuntu)?  I have tried several different things people have posted about using PPTP manually, but non seem to work for me.  If I use Suse running inside VMWare, I can use pptp-config and it connects me to work just fine.  PLEASE HELP!!!  ](*,)

---

### Post by exile on 2005-05-15
I wrote up a fix for this very problem. I posted it to the forums.

Reposted below.

---- 
add the following to your repository.

deb [http://quozl.netrek.org/pptp/](http://quozl.netrek.org/pptp/) pptpconfig/
deb [http://quozl.netrek.org/pptp/](http://quozl.netrek.org/pptp/) php-gtk/

sudo apt-get update
sudo apt-get install pptpconfig

For kubuntu users you might want to edit
/usr/share/applications/pptpconfig.desktop
and put the category in internet otherwise it will be in lost and found.

---

### Post by njwetsu on 2005-05-15
I just tried your request and I get the following when I run "sudo apt-get update":

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Err [http://quozl.netrek.org](http://quozl.netrek.org) pptpconfig/ Release.gpg
  Temporary failure resolving 'quozl.netrek.org'
Err [http://quozl.netrek.org](http://quozl.netrek.org) php-gtk/ Release.gpg
  Temporary failure resolving 'quozl.netrek.org'
Ign [http://quozl.netrek.org](http://quozl.netrek.org) pptpconfig/ Release
Ign [http://quozl.netrek.org](http://quozl.netrek.org) php-gtk/ Release
Ign [http://quozl.netrek.org](http://quozl.netrek.org) pptpconfig/ Packages

Can you please run from your system and let me know what you get?  I am more then willing to admit it my be something with my ISP or DNS setup, but would like verification from someont who has tried it recently.

Thanks.

---

### Post by NewbieNik on 2005-05-31
OK, Go to [http://quozl.netrek.org/pptp/php-gtk/](http://quozl.netrek.org/pptp/php-gtk/) 
and download the following to your home folder:-
pptpconfig20040809_i386.deb
php-gtk-pcntl_1.0.0-2_i386.deb
php-pcntl_4.3.8-2_i386.deb

Use Synaptic Package Manager to get libglade0 (Allow install of associated packages)

Once done open terminal and then:-
sudo dpkg -i php-gtk-pcntl_1.0.0-2_i386.deb

sudo dpkg -i php-pcntl_4.3.8-2_i386.deb

sudo dpkg -i pptpconfig20040809_i386.deb

et voila!!! PPTP configuration without the terminal commands. Hope that helps

---

### Post by pangloss on 2005-06-20
FWIW: I found that I had to use the following line:
```
deb http://quozl.netrek.org/pptp/pptpconfig ./
```
for this to work.

This is also documented here: [http://pptpclient.sourceforge.net/howto-debian.phtml#install_gui](http://pptpclient.sourceforge.net/howto-debian.phtml#install_gui)

---

### Post by pedroc on 2005-06-29
NewbieNik wrote : 

"OK, Go to [http://quozl.netrek.org/pptp/php-gtk/](http://quozl.netrek.org/pptp/php-gtk/)
and download the following to your home folder:-

pptpconfig20040809_i386.deb
php-gtk-pcntl_1.0.0-2_i386.deb
php-pcntl_4.3.8-2_i386.deb

Use Synaptic Package Manager to get libglade0 (Allow install of associated packages)

Once done open terminal and then:-
sudo dpkg -i php-gtk-pcntl_1.0.0-2_i386.deb

sudo dpkg -i php-pcntl_4.3.8-2_i386.deb

sudo dpkg -i pptpconfig20040809_i386.deb

et voila!!! PPTP configuration without the terminal commands. Hope that helps"

But That URL doesn't exist anymore. 

Go to [http://quozl.netrek.org/pptp/pptpconfig/](http://quozl.netrek.org/pptp/pptpconfig/)  instead and follow the instrucions above.
It worked for me!! thanks NewbieNik.

---

