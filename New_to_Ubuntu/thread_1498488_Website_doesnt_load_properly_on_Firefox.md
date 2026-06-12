---
title: "Website doesnt load properly on Firefox"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by Vendettaseve on 2010-05-31
Hey everyone,
The following site does not load correctly on firefox, its all white and menus dont quite fit etc etc. 
[http://www.netstormhq.com/download.php?report.1]("http://www.netstormhq.com/download.php?report.1")

FUnny thing is, it works in Seamonkey -_- also I have verified that my java is up to date and working etc.
[http://sites.google.com/site/easylinuxtipsproject/java]("http://sites.google.com/site/easylinuxtipsproject/java")

Any ideas?

---

### Post by iMisspell on 2010-05-31
Work with: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.3) Gecko/20100401 Firefox/3.6.3

You have any FireFox extensions or addones installed ?
Maybe they are causing the problem.


[EDIT]
Note: That was with, 9.04 Jaunty Jackalope

Maybe this thread will help you
[http://ubuntuforums.org/showthread.php?t=1498475](http://ubuntuforums.org/showthread.php?t=1498475)

_

---

### Post by Vendettaseve on 2010-05-31
looks like im using 3.6.3 I have the following extensions.

Adblock PLus 1.1.3
Ant Video DOwnloader 2.0.1
FIrefusk 1.9(No longer works I believe, must remove)
Illimitux 4.0
Mediaplayerconnectivity 0.9.3
Prism for Firefox 1.0b3(I have no idea what this it)
QUickJava 1.7.2
Ubuntu Firefox Modifications 0,9rc2

---

### Post by Locke_99GS on 2010-05-31
Renders fine for me. Try disabling extensions, as mentioned.

---

### Post by bananas4370 on 2010-05-31
> **Vendettaseve said:**
> Hey everyone,
The following site does not load correctly on firefox, its all white and menus dont quite fit etc etc. 
[http://www.netstormhq.com/download.php?report.1]("http://www.netstormhq.com/download.php?report.1")

FUnny thing is, it works in Seamonkey -_- also I have verified that my java is up to date and working etc.
[http://sites.google.com/site/easylinuxtipsproject/java]("http://sites.google.com/site/easylinuxtipsproject/java")

Any ideas?

Have you tried loading this website using another firefox [profile]("http://kb.mozillazine.org/Profile_Manager")? I'd also try loading firefox in [safe mode]("http://kb.mozillazine.org/Safe_mode") to eliminate any add-ons that could be causing this.

That site loads fine this way using ff 3.6.5pre

---

### Post by Vendettaseve on 2010-05-31
How do I start FF up in safe mode? also im getting alot of errors in the error console like this one 

Warning: Error in parsing value for 'top'.  Declaration dropped.
Source File: [http://www.netstormhq.com/download.php?report.1](http://www.netstormhq.com/download.php?report.1)
Line: 0

AntLog: [http://www.netstormhq.com/e107_files/popup.js](http://www.netstormhq.com/e107_files/popup.js) Rejected => Redirect

---

### Post by bananas4370 on 2010-05-31
> **Vendettaseve said:**
> How do I start FF up in safe mode? also im getting alot of errors in the error console like this one 

Warning: Error in parsing value for 'top'.  Declaration dropped.
Source File: [http://www.netstormhq.com/download.php?report.1](http://www.netstormhq.com/download.php?report.1)
Line: 0

AntLog: [http://www.netstormhq.com/e107_files/popup.js](http://www.netstormhq.com/e107_files/popup.js) Rejected => Redirect

Click here to learn how to start ff in safe mode. [http://kb.mozillazine.org/Safe_mode]("http://kb.mozillazine.org/Safe_mode")

I don't know about those errors in the error console.

---

### Post by Vendettaseve on 2010-05-31
> **bananas4370 said:**
> Click here to learn how to start ff in safe mode. [http://kb.mozillazine.org/Safe_mode]("http://kb.mozillazine.org/Safe_mode")

I don't know about those errors in the error console.

Getting a "no such file or directory" from the instructions on that site.

Also a little googling turned this up, altho Im not sure if its related.
[http://www.litfuel.net/plush/?postid=101]("http://www.litfuel.net/plush/?postid=101")

---

### Post by lovinglinux on 2010-05-31
Don't bother with safe mode. Is not an extension. I did the test here.

It works fine on a clean profile, but not with my default profile, even in safe-mode. So it must be some settings. I still need to investigate tho.

---

### Post by lovinglinux on 2010-05-31
It is something related to image loading. The problem is that the background image is not displayed on your current profile.

---

### Post by lovinglinux on 2010-05-31
Figured it out. The site only displays the background if the preference **[network.http.sendRefererHeader](http://kb.mozillazine.org/Network.http.sendRefererHeader)** has the default value, which is 2. This value allows the browser to send Referer header when clicking on a link or loading an image.

I use 0, so the browser never send information about which site I was previously visiting when I click a link. Is a privacy concern.

---

