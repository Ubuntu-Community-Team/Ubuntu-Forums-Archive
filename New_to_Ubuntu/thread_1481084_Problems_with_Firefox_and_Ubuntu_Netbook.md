---
title: "Problems with Firefox and Ubuntu Netbook"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by theonetruelord on 2010-05-12
Hi all, hoping you can help me please.

My brother has just bought himself an Acer Aspire One netbook which came preloaded with Linpus Linux (I don't think he realised it didn't have windows, DOH!) which I have replaced with Ubuntu Network Edition 10.04. All was going well until I installed Wine (Was this a bad move? He needs it to run iTunes for his iPhone) at which point Firefox stopped working! So I tried removing and reinstalling (using the terminal) and halfway through the install everything completely froze, no response at all, so I had to switch it off by holding the power switch. Needless to say, when it was back on, Firefox wasn't properly installed. So the question is, what do I do now?

If I use sudo apt-get remove firefox I see this

```
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following  packages will be REMOVED
  firefox firefox-branding
0  upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
 1 not fully installed or removed.
After this operation,  29.7MB disk space will be freed.
Do you want to continue  [Y/n]? y
(Reading database ... 129142 files and directories  currently installed.)
 Removing firefox-branding ...
Removing firefox ...
dpkg  (subprocess): unable to execute installed pre-removal script: Exec  format error
dpkg: error processing firefox (--remove):
  subprocess installed pre-removal script returned error exit status 2
dpkg  (subprocess): unable to execute installed post-installation script:  Exec format error
dpkg: error while cleaning up:
  subprocess installed post-installation script returned error exit  status 2
Processing triggers for desktop-file-utils ...
Processing  triggers for python-gmenu ...
Rebuilding  /usr/share/applications/desktop.en_GB.utf8.cache...
 Processing triggers for python-support ...
Errors were  encountered while processing:
 firefox
E:  Sub-process /usr/bin/dpkg returned an error code (1)

```And if I try to install it I get

```
Reading package lists... Done
Building dependency tree        
Reading state information... Done
firefox is  already the newest version.
You might want to run 'apt-get -f  install' to correct these:
 The following packages have unmet dependencies.
  firefox:  Depends: firefox-branding or
                     abrowser-branding
E: Unmet dependencies. Try 'apt-get -f  install' with no packages (or specify a solution).

```I also tried -f install but that gives me the message

```
sudo apt-get -f  install
Reading package lists... Done
Building  dependency tree       
Reading state information... Done
0  upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
 1 not fully installed or removed.
After this operation,  0B of additional disk space will be used.
Setting up firefox  (3.6.3+nobinonly-0ubuntu4) ...
dpkg (subprocess): unable to  execute installed post-installation script: Exec format error
 dpkg: error processing firefox (--configure):
 subprocess  installed post-installation script returned error exit status 2
Errors  were encountered while processing:
 firefox
E:  Sub-process /usr/bin/dpkg returned an error code (1)
```
 Please help!

Many thanks,

Nick

---

### Post by blueridgedog on 2010-05-12
Have you tried 

```
sudo apt-get remove --purge firefox
```

Wine will probably not run iTunes...at least not the current one, but you may have success that I have not had.

---

### Post by theonetruelord on 2010-05-13
Thank you, I will try that next time. I just put the original OS back on it, and it doesn't look like iTunes will work anyway, it's slooooooooooow on my big PC and won't recognise iPods either. Not worth the hassle!

Nick

---

### Post by blueridgedog on 2010-05-13
I have an iPhone and use iTunes under Linux to manage it.  To do this I use an installation of WindowsXP running under the Sun VirtualBox software.

---

