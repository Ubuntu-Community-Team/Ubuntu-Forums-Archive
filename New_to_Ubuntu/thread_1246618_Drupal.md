---
title: "Drupal"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by den160593 on 2009-08-21
Hi,

I tried to install drupal6 through Synaptic. However it crashed, so I used XKill to force quit it, then I restarted synaptic. IT told me to do this command through terminal (ended with -a, can't remember exactly, but I think it just did the installation through terminal).

I got to the stage when I was asked what database to use on drupal (I chose default since I'm new) and installation finished up.

Then I went to [http://localhost/drupal](http://localhost/drupal)

However, it says it can't be located. I tried restarting, but it still doesn't work. This is the message I get:
> 
Not Found

The requested URL /drupal was not found on this server.
Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch Server at localhost Port 80

Could someone help me out with how to get it working? I'm on Ubuntu 9.04

Thanks!!

---

### Post by den160593 on 2009-08-22
anyone?

---

### Post by indytim on 2009-08-22
I'm not versed specifically in Drupal.  I'm assuming it is similar to Joomla. If so, why not just download the install compressed file to a folder within your /var/www?   Expand it and access the initial install file to launch the installation.

IndyTim

---

### Post by den160593 on 2009-08-22
The help I got in chat says that I need to install it via the website not through Synaptic.

How could I delete it all, and the assosiated files from the drupal6 installation in Synaptic?

Thanks!
-den

---

### Post by darksideforge on 2009-08-22
> **den160593 said:**
> The help I got in chat says that I need to install it via the website not through Synaptic.

How could I delete it all, and the assosiated files from the drupal6 installation in Synaptic?

Thanks!
-den

If you installed it using Synaptic Package Manager, you should be able to uninstall it the same way. The normal "default" window you see when you open SPM is the "Sections" view. In the lower-left corner you'll see the next option listed as "Status". Once you've clicked on Status, above that you'll see an option for "Installed". Type [drupal] in the search window and then right-click for "Complete Uninstall".

I hope I'm being clear enough with all of this.

---

### Post by tomthumb99 on 2009-10-17
Folks, I found its best to use command line install process.  A few file have to go into the apache/tomcat area. Its all about php, not so clean.

 Also write down all the passwords enterd (3-4 are needed).  You need mysql, apache, java.  I found drual6 is cleaner than drual5 with php integration points.

---

