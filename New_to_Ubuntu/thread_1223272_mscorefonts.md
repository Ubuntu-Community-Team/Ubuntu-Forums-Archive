---
title: "mscorefonts"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by stockley on 2009-07-26
I'm new to ubuntu and linux in general, I have been searching for a couple of days now to fix my problem, however all the posts/threads that ive found have not helped.

My problem first occured when I tried to install the flash player plugin for firefox, 
When I entered the code: > ** $ sudo apt-get install flashplugin-nonfree**
My terminal output was:[INDENT]Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11-generic linux-headers-2.6.28-11
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ttf-mscorefonts-installer (2.6) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of msttcorefonts:
 msttcorefonts depends on ttf-mscorefonts-installer; however:
  Package ttf-mscorefonts-installer is not configured yet.
dpkg: error processing msttcorefonts (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 ttf-mscorefonts-installer
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

[/INDENT]I've been through many pages about telling me how to install the mscorefonts package, but nothing has worked and always ends in failure.
The first code I found was this:[INDENT]```
 sudo dpkg --purge msttcorefonts

Once its been purged:
 sudo apt-get install ubuntu-restricted-extras
```[/INDENT]The output is similar to the first one,[INDENT](Reading database ... 125561 files and directories currently installed.)
Removing msttcorefonts ...
pat@Blue:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11-generic linux-headers-2.6.28-11
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ttf-mscorefonts-installer (2.6) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/INDENT]This is really frustrating me and has been doing so for a while now. I have tried much more commands than that of course, but they seem to be the recurring results in all of my searches. Any help would be very much appreciated. :)

(Linux Blue 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 x86_64 GNU/Linux)

---

### Post by XubuRoxMySox on 2009-07-26
I don't know if this will help you or not, but when I had a similar problem in Synaptic it was because I hadn't properly added the Medibunu repository. I left out the word "deb" before the URL.

Have a look [here]("https://help.ubuntu.com/community/Medibuntu") to make sure you have added it correctly.

-Robin

---

### Post by desperado665 on 2009-07-26
You could also use ubuntu-tweak [http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads) 

Add Medibuntu using Applications>Third Party Sources

Then add Ubuntu-restricted-extras under Applications>Add/Remove

Works like a charm for me  :)

---

### Post by stockley on 2009-07-26
Thanks for the help, I've gotten flash player under control, but when installing other packages, a lot of them are still left with the error:
> Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name
andale32.exe: No such file or directory

Its stopping me from installing quite a few applications. Do you know anything about that error? Apparently Synaptics managed to install the ttf-mscorefonts installer package but it still has the error in relation to it... I am really confused :S

Thanks in advance

---

### Post by Liolikas on 2009-07-26
Disable proxy in synaptics configuration.

---

### Post by stockley on 2009-07-26
> **Liolikas said:**
> Disable proxy in synaptics configuration.

It's already set to Direct connection.

After trying to install most applications with synaptic it says > E: ttf-mscorefonts-installer: subprocess post-installation script returned error exit status 1


---

### Post by stockley on 2009-07-26
I figured out something, I ran

```
sudo apt-get remove ttf-mscorefonts-installer
```

and now I can install things, BUT I don't know if I'm ever going to need the mscorefonts...
So what exactly does mscorefonts do? I've read the thread about it and it was really vague, I understand that they are fonts made by Microsoft in an attempt to make things cross-compatible across the internet etc. but are they necessary?

---

### Post by stockley on 2009-07-28
I'm getting a bit anxious to know if mscorefonts is a necessity... So if anyone can tell me I can live happily again :)

---

