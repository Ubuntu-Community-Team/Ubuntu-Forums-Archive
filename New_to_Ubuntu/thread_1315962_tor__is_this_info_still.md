---
title: "tor:  is this info still"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by shadowlands on 2009-11-05
good to use?

[https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ?action=newaccount](https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ?action=newaccount)

---

### Post by shadowlands on 2009-11-05
bash: /etc/polipo/config: Permission denied

 why do I get this message I followed the directions on the web page.

---

### Post by Dude-PWB- on 2009-11-05
I used this setup here: [http://www.torproject.org/docs/tor-doc-unix.html.en](http://www.torproject.org/docs/tor-doc-unix.html.en)

And, it worked fine, I just used the configs they had.

Make sure you use the 'sudo' command to get around the permission denied issue.

---

### Post by shadowlands on 2009-11-05
Still not work following error message occurred: 
sudo /etc/polipo/config
sudo: /etc/polipo/config: command not found
> **Dude-PWB- said:**
> I used this setup here: [http://www.torproject.org/docs/tor-doc-unix.html.en](http://www.torproject.org/docs/tor-doc-unix.html.en)

And, it worked fine, I just used the configs they had.

Make sure you use the 'sudo' command to get around the permission denied issue.

---

### Post by Dude-PWB- on 2009-11-05
To edit the config file you need to use: sudo gedit /etc/polipo/config

But, the way I did it, was simply type: sudo nautilus

Then browse to the config file, and rename it to config.bak, then create a new file called config, and paste the contents of the config file into the new file.

Then 'sudo /etc/init.d/polipo restart'

Do the same with the tor config as well.

---

### Post by shadowlands on 2009-11-05
Thank you much!!!!And you found these directions where? do they have a step- by-step guide?:KS   > **Dude-PWB- said:**
> To edit the config file you need to use: sudo gedit /etc/polipo/config

But, the way I did it, was simply type: sudo nautilus

Then browse to the config file, and rename it to config.bak, then create a new file called config, and paste the contents of the config file into the new file.

Then 'sudo /etc/init.d/polipo restart'

Do the same with the tor config as well.

---

### Post by Dude-PWB- on 2009-11-05
It's all about making a mess of everything and learning how to fix it, and I've done that many times. :)

Sudo is the command to use when acting as a 'super user' or admin powers, it helps your system stay more secure from the stupid things you might accidently do as a regular user. ;)

gedit is the text editor most people use to edit config files, but in order to edit config files that affect how your system or the programs you are using affect your system, you need to be a super user, or 'sudo'.

Hope you have it working correctly, and glad I could help.

---

### Post by shadowlands on 2009-11-05
I used the config on the website for tor, step two but have trouble figuring out how to config tor.as you suggested.  Any dummy tips?

I tried using sudo nautilus

and I think something is wrong because of the statment that showed up in the terminal:


nautilus:2249): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:2249): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2249): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2249): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:2249): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
Segmentation fault

---

### Post by Dude-PWB- on 2009-11-05
You shouldn't have to configure tor, it should be configured already, just configure polipo, my mistake.

Once you have changed the config for polipo do these commands.

```
sudo /etc/init.d/tor restart
```

then 

```
sudo /etc/init.d/polipo restart
```

Then you should be able to set your browser, or whatever application you want to run on the tor network to use the proxy at: 127.0.0.1 port 9050.

Then go to a website like [http://www.ip-adress.com](http://www.ip-adress.com) and check that it is working properly

---

### Post by shadowlands on 2009-11-06
Thanks!!  :KS> **Dude-PWB- said:**
> You shouldn't have to configure tor, it should be configured already, just configure polipo, my mistake.

Once you have changed the config for polipo do these commands.

```
sudo /etc/init.d/tor restart
```

then 

```
sudo /etc/init.d/polipo restart
```

Then you should be able to set your browser, or whatever application you want to run on the tor network to use the proxy at: 127.0.0.1 port 9050.

Then go to a website like [http://www.ip-adress.com](http://www.ip-adress.com) and check that it is working properly

---

