---
title: "sudo dpkg --configure -a issues."
date: 2008-12-27
forum: New to Ubuntu
---

### Post by leonhart83 on 2008-12-27
Hi Guys,

My system crashed when updating initially (there were 208 updates). I reboot and when trying to run the updates again I get the message.

[COLOR="Red"]**************************[COLOR="Red"]****************************************
"E: dpkg was interrupted, you must manually run "dpkg --configure -a" to correct the problem.
E:_cache->open()failed, please report"
******************************************************************[/COLOR]

I have tried running the command with sudo at the front and it comes up with.

[COLOR="Red"]******************************************************************
dpkg: parse error, in file '/var/lib/dpkg/updates/0001 near line 23 package 'language-pack-en': EOF after field name '.
*****************************************************************[/COLOR]

Here is what I have tried.

sudo apt-get update
sudo apt-get install
sudo dpkg --configure -a && sudo apt-get -f install

The top two return the first message and the bottom one returns the second message.

I have spent quite a while trying to get this fixed.

---

### Post by bumanie on 2008-12-27
The closest answer I can find to this problem is using the following code in terminal > sudo dpkg --clear-avail && sudo apt-get updateIt apparently works, but i have never had this issue an thus have no first-hand experience with this command. Hope it works.

---

### Post by leonhart83 on 2008-12-27
> **bumanie said:**
> The closest answer I can find to this problem is using the following code in terminal It apparently works, but i have never had this issue an thus have no first-hand experience with this command. Hope it works.

Sorry man, I forgot about that one. I have tried that one aswell. It ends the same.

Everything I have read people are really happy with their simple solutions. I thought I would have this one sorted already.

Micky.

---

### Post by HereInOz on 2008-12-27
I know this will be seen as a cop-out, but from the sound of it, this is a new installation on which you were running the initial upgrade.  If so, I would be tempted, if no-one comes up with an answer in the short term, to put the CD in and do another install.

However, if you have done major system customization prior to the upgrade, then the re-install scenario becomes less palatable.

By the way, did the system crash or did you lose internet connectivity?  If it really was a system crash, perhaps there is a problem somewhere which you need to solve so that it doesn't happen again.

That is a problem which sometimes dogs the Linux community - people have an older machine which is not running well on Windows - crashing, blue screens, etc. so they figure that they will install Linux on it, and that will fix it, because Linux is more stable than Windows, and all that stuff.  

In reality, they are simply trying to install an operating system on hardware which is of dubious reliability, which only causes further heartache.  Please make sure that your hardware is not the root cause of the "crash".

---

### Post by bumanie on 2008-12-27
Can you supply more information such as system specs. Was this a new installation? Which ubuntu version is it? If ubuntu still works could you post the output of > sudo fdisk -lu > df -h / > df -h /homeif you have a separate /home, if not just df -h should be OK.

---

### Post by Partyboi2 on 2008-12-27
> **leonhart83 said:**
> Hi Guys,

My system crashed when updating initially (there were 208 updates). I reboot and when trying to run the updates again I get the message.

[color="Red"]**************************[COLOR=Red]****************************************
"E: dpkg was interrupted, you must manually run "dpkg --configure -a" to correct the problem.
E:_cache->open()failed, please report"
******************************************************************[/COLOR]

I have tried running the command with sudo at the front and it comes up with.

[COLOR=Red]******************************************************************
dpkg: parse error, in file '/var/lib/dpkg/updates/0001 near line 23 package 'language-pack-en': EOF after field name '.
*****************************************************************[/COLOR]

Here is what I have tried.

sudo apt-get update
sudo apt-get install
sudo dpkg --configure -a && sudo apt-get -f install

The top two return the first message and the bottom one returns the second message.

I have spent quite a while trying to get this fixed.
Have you tried moving the file out of the way.
```
sudo mv /var/lib/dpkg/updates/0001 /var/lib/dpkg/updates/0001.old 
```then
```
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```If that does not work can you paste the contents of the file?
```
cat /var/lib/dpkg/updates/0001.old
```

---

### Post by leonhart83 on 2008-12-27
> **Partyboi2 said:**
> Have you tried moving the file out of the way.
```
sudo mv /var/lib/dpkg/updates/0001 /var/lib/dpkg/updates/0001.old 
```then
```
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```If that does not work can you paste the contents of the file?
```
cat /var/lib/dpkg/updates/0001.old
```

I have tried this option aswell. I went with a full reinstall to fix the issue. I am going to avoid doing an update whilst I am studying (unless it is needed) until I get to a point where I am comfortable running the app. I think the vm box is what is causing the system to crash. (although it only happened once, is running fine now).

If it does happen again I will attempt again to fix it. 

I have learnt quite a bit about troubleshooting from this exercise and also found some good articles to read.

Thanks for the help.

Micky.

---

### Post by bemental on 2009-02-13
Thanks bumanie, your suggestion to dpkg clear worked like a charm.  I was having a similar problem where nothing was working.

A shame I had to put off looking for solutions for a week or two because I was too busy to play...

Again, my thanks!

---

