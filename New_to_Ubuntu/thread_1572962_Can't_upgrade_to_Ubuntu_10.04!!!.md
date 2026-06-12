---
title: "Can't upgrade to Ubuntu 10.04!!!"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by Suzanne42 on 2010-09-12
I currently hve Ubuntu 9.10 but I am unable to upgrade to 10.04 via Update Manager nor command line. I dunno what to do. In Update Manager, the process gets stuck in the second upgrade option while in the terminal, comp doesn't recognise the new Ubuntu release.

---

### Post by abs_kkk on 2010-09-12
try the alternate cd method....[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

---

### Post by Suzanne42 on 2010-09-12
M not sure which option to select in the list u provided, mine is an ACER comp with Ubuntu version 9.10. Anyways m downloading one alternate CD option now, will see if it works.Thanx

---

### Post by wilee-nilee on 2010-09-12
> **Suzanne42 said:**
> M not sure which option to select in the list u provided, mine is an ACER comp with Ubuntu version 9.10. Anyways m downloading one alternate CD option now, will see if it works.Thanx

The alternative cd does offer a upgrade I believe that will not just be a overwrite like the live cd. I have never done it though so I will look for information, hopefully somebody who knows will see the thread, if this is not something your aware of.

---

### Post by Suzanne42 on 2010-09-12
Actually, I stopped downloading it, not sure if its the correct one. Is there any simpler method to resolve this issue?

---

### Post by abs_kkk on 2010-09-12
checkout this link it'll help

[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

and also be careful which file u r selecting if weather its 64bit version or 32 bit version

---

### Post by jeight on 2010-09-12
Check Synaptic Package Manager and see if you have any broken packages. Even if you don't try reloading and clicking apply changes. Sometimes broken or none upgraded packages will cause Lucid to fail.

---

### Post by wilee-nilee on 2010-09-12
Are you seeing the upgrade in the update manager?

Here is what you generally do to get it to show if not, press Alt+F2 and type in update-manager -d to start the update manager.

---

### Post by Suzanne42 on 2010-09-12
I can't reload via Synaptic, I get this error
E: Internal Error, Could not perform immediate configuration (2) on mountall
I used to have the upgrade option in Update Mananger, now it has disappeared, I have partial upgrade but that hangs once executed. Nothing works, I still can't fix broken packages.

---

### Post by jeight on 2010-09-12
Awe damn I forgot about that. Good catch. I dropped the ball on that last post haha.

---

### Post by Suzanne42 on 2010-09-12
abs_kkk I have seen that link before, its of no help.

---

### Post by wilee-nilee on 2010-09-12
There are two commands that may get things cleared up.

```
sudo dpkg --configure -a
```
```
sudo apt-get install -f 
```     

As the other posts have suggested after these commands you may have access to synaptic to look for other broken stuff.

So I am assuming that you don't have a partial upgrade you're trying to fix.

---

### Post by Suzanne42 on 2010-09-12
I m doing a partial update for the nth time now, should I stop it? The time keeps wavering, I dun see the pt of doing it bcose in the end the update manager jus hangs.

---

### Post by abs_kkk on 2010-09-12
there is another way to upgrade from terminal that is

> sudo apt-get upgrade

EDIT : follow [wilee-nilee]("http://ubuntuforums.org/member.php?u=906928")'s way i think he is more experienced in this stuff :P

---

### Post by Suzanne42 on 2010-09-12
abs-kkk I have tried that before, I get the message "Waiting for header 0%" then the terminal hangs, right now m waiting for partial manager to finish, if it hangs again then I will cancel it.

---

### Post by wilee-nilee on 2010-09-12
> **Suzanne42 said:**
> I m doing a partial update for the nth time now, should I stop it? The time keeps wavering, I dun see the pt of doing it bcose in the end the update manager jus hangs.

So partial updates are not a good idea. So run the two commands and then let the terminal do the rest look for it to ask you for confirmations. Then go to synaptic look in the broken package section for dependencies by right clicking on the broken package.

It may be that the commands clear some of this up. What you have to understand with a Ubuntu update is if it hangs or is shut down in the middle without finishing this can cause problems with updating again and other problems, the commands are for hopefully remedying that.

---

### Post by Suzanne42 on 2010-09-12
I stopped partial update, ran the commands earlier specified in the terminal then went to Synaptic->Custom Filters->Broken, I see nothing there.Under Edit I again selected "fix broken packages", I see no diff, what do I do?No packages have been specified as broken even when I ran the commands in the terminal.

---

### Post by jtarin on 2010-09-12
How do you connect to the internet? Are you using a router for internet connection?

[http://korel.com.au/linux/apt-get-waiting-for-headers/](http://korel.com.au/linux/apt-get-waiting-for-headers/)

---

### Post by mörgæs on 2010-09-12
The safe, fast and hassle-free method is a clean install using the alternate installer with wired internet access. This thread is a good example of the problems of upgrading.

---

### Post by Suzanne42 on 2010-09-12
jtarin, I presume so. Anyways I have restarted the partial upgrade & left it to take its own sweet time. M fed up with trying to upgrade.

---

### Post by Suzanne42 on 2010-09-12
M stuck with the partial upgrade again, the progress bar is moving but the fetching file command doesn't go beyond 1316 of 1331, its been almost 45 mins.

---

### Post by slakkie on 2010-09-12
Hi, you could have a look here:

[https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)


Best of luck!

---

### Post by jtarin on 2010-09-12
> **Suzanne42 said:**
> M stuck with the partial upgrade again, the progress bar is moving but the fetching file command doesn't go beyond 1316 of 1331, its been almost 45 mins.
Find another mirror to download from.

---

### Post by Suzanne42 on 2010-09-12
Btw jtarin, I saw the link u gave 4 "Waiting for Headers" but I dunno where to make the change. If u cud tell me where, then I will go back to upgrading via terminal. Update Manager is practically crawling, if it continues like this then most likely Ubuntu 10.04 will finish installing only tmr. What other options r there?Not many plus my synaptic is giving the error I specified b4 so I dunno how to resolve that also,unless I resolve that can't do normal Ubuntu 9.10 updates.

---

