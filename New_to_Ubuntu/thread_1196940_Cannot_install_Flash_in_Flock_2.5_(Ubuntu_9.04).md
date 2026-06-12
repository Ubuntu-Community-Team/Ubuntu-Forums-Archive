---
title: "Cannot install Flash in Flock 2.5 (Ubuntu 9.04)"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by Dutch Treat on 2009-06-25
HI !

I am completely new with Ubuntu/Linux and have been using it for 4 days now.

I have some problems which I am not able to solve.

I tried to install Abobe's Flash plugin, but it would not work the normal way.

I did a search and tried several other ways, mostly by using the Terminal window (which for me, as a XP user, is new to me).

Did anybody have the same problem and solved this (Flock v2.5)


Thanks in advance for your help !

---

### Post by oldos2er on 2009-06-25
[http://helpforlinux.blogspot.com/2008/12/get-flash-working-in-flock-browser-in.html](http://helpforlinux.blogspot.com/2008/12/get-flash-working-in-flock-browser-in.html)

---

### Post by Dutch Treat on 2009-06-25
> **oldos2er said:**
> [http://helpforlinux.blogspot.com/2008/12/get-flash-working-in-flock-browser-in.html](http://helpforlinux.blogspot.com/2008/12/get-flash-working-in-flock-browser-in.html)

Error on the first code command ... 

> mega@MSI:~$ sudo nautilus
[sudo] password for mega: 

** (nautilus:7435): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing[FONT=trebuchet ms]**.**[/FONT]

---

### Post by oldos2er on 2009-06-25
Does Nautilus open at all?

Edit: You can forego "sudo nautilus" and run
sudo cp [FONT=&quot]/usr/lib/firefox/plugins/[/FONT]flashplugin-alternative.so /usr/share/flock/plugins

---

### Post by binbash on 2009-06-25
> **Dutch Treat said:**
> Error on the first code command ... 

[FONT=trebuchet ms]**.**[/FONT]

it is just a warning not an error.

---

### Post by Dutch Treat on 2009-06-26
> **binbash said:**
> it is just a warning not an error.

Ok, binbash. 

Now I did the next step: 

> [FONT=Verdana][[IMG]http://twitter.com/favicon.ico[/IMG]]("http://search.twitter.com/search?q=N")[[IMG]http://www.google.com/favicon.ico[/IMG]]("http://www.google.com/search?q=N")[[IMG]http://smarterfox.com/media/wiki-favicon-sharpened.png[/IMG]]("http://smarterfox.com/wikisearch/search?q=N&locale=en-US")[[IMG]http://smarterfox.com/media/popup_bubble/oneriot-favicon.ico[/IMG]]("http://www.oneriot.com/search?p=smarterfox&ssrc=smarterfox_popup_bubble&spid=8493c8f1-0b5b-4116-99fd-f0bcb0a3b602&q=N")avigate to the folder:[/FONT]
[FONT=Verdana]**usr/lib/firefox/plugins** and copy the only file present there 'flashplugin-alternative.so'[/FONT]


There is not only 'flashplugin-alternative.so' there, but also 10 mplayerplug-in.(*)-files there. And onemore: the file 'nppdf.so'.

> [FONT=Verdana]to this folder:[/FONT]
**/usr/share/flock/plugins/**


These folders are not there !

I tried to create them - but it says: 

" Error - the new file cannot be created "

---

### Post by oldos2er on 2009-06-27
How did you install Flock? If you know which directory Flock's in, then copy flashplugin*so to /somewhere/flock/plugins (obviously replace "somewhere" with a proper directory name).

---

### Post by eklem on 2009-07-01
> **Dutch Treat said:**
> HI !

I am completely new with Ubuntu/Linux and have been using it for 4 days now.

I have some problems which I am not able to solve.

I tried to install Abobe's Flash plugin, but it would not work the normal way.

I did a search and tried several other ways, mostly by using the Terminal window (which for me, as a XP user, is new to me).

Did anybody have the same problem and solved this (Flock v2.5)


Thanks in advance for your help !

Yes, had the same problem. I'm using Ubuntu 9.04, 64-bits version, and installed Flock 2.5 from getdeb.net. The issue with that one is that it's not actually a real 64-bits version. [I downloaded the 32-bits version of libflashplayer.so and copied that one to the correct folder]("http://getsatisfaction.com/flock/topics/flock_will_not_take_any_plugins_64bit"). Check fourth reply.

---

### Post by Dutch Treat on 2009-07-01
You Gals & Guys: thanks a lot. It finally worked out !!

I downloaded the 32-bit version of the libflashplayer.so, like Eklem suggested. Mind you: the tar.gz like in the link and *not* the Ubuntu !

I extracted that one to /usr/share/flock/plugins/

Then ran the script in terminal. 

It asked for me to close the browser.

It will then install the correct files in .mozilla.

Et ..... voila !!! 

Af restarting Flock: FLASH !!!! 


Thanks again for all your help.


a starting Ubuntu user, now for 10 days in Linux land, coming form Windows XP ... and asking himself:

why oh why does it take 10 days to install have basic function like Flash to get installed correctly  .... 

= = = 
Link from Eklem that did the final touch:

Flock will not take any plugins (64bit) (1 July 2009)

 [http://getsatisfaction.com/flock/topics/flock_will_not_take_any_plugins_64bit](http://getsatisfaction.com/flock/topics/flock_will_not_take_any_plugins_64bit)
 [http://snipurl.com/lbui9](http://snipurl.com/lbui9)

---

### Post by eklem on 2009-07-02
Good to hear it worked Dutch Treat. I think there's a couple of reasons this is a bit quirky:

1. It's not part of the standard program repository. In Ubuntu/Debian-world where you have the beauty of apt-get/synaptic everything from that repository just works. New software is added all the time, and some software packages are taken out. Not sure why Flock isn't in the repository, but since it isn't it's not taken care of by Ubuntu in the same graceful way.

2. Flash is proprietary code, and has just recently been added to the 3rd party part of the repository. Big proprietary software vendors are starting to understand that they have to support Linux as well, but these things takes time.

---

