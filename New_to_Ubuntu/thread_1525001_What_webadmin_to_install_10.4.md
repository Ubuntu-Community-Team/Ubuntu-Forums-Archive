---
title: "What webadmin to install 10.4"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by ozstar on 2010-07-06
Hi,

I am a newby..

I have 10.4 and have the ubuntu server working sort as a test web server but not out to the internet but now I want to install webadmin.

I looked in desktop Get Software packages and it shows Kolab administraion for kolab-webadmin and also znc-webadmin.

Is one of these the webadmin I need and if so do I inmstall it from here?

Thanks


oz

---

### Post by cj13579 on 2010-07-06
For my server admin I use Webmin. You can download it from - [http://www.webmin.com/](http://www.webmin.com/).

It has a really simple .deb install, intuitive user interface and allows you to fully manage your server from any browser.

---

### Post by ozstar on 2010-07-06
Hey thanks..

oz  :-)

---

### Post by ozstar on 2010-07-08
Well I did install it and wow it is very comprehensive and would be excellent for those who understood all it does.  

Me ? well I'm a caveman with Linux so am looking at the very basics to start with.

Where is the best place to start and stop php, mySQL, apache etc when I make changes and need to refresh?

Thanks


oz

---

### Post by cj13579 on 2010-07-08
Easy! On the left hand side menu under "Severs" You will find sections for Apache and MySQL. For Apache the stop start button is in the top right hand corner. For MySQL the stop start button is at the bottom of the screen.

For PHP - from the left hand menu under "Others" you should find the PHP Configuration section. You can either edit the .ini file with the GUI or manually if you wish.

Hope this helps.

---

### Post by Randy Wells on 2010-10-06
I'm not using the GUI.  How do I add or change users, etc.  I can't get to Webmin from my Windows desktops.  I looked in the "miniserv.users" file and the only user there is root.  "root: x:0" to be exact.  Is there another file to peek in?
Also, how do I make sure that port 10000 is open on the server?

Randy

---

### Post by CharlesA on 2010-10-06
Stick to one thread please.

You can access the webmin interface from any user that can use sudo.

---

