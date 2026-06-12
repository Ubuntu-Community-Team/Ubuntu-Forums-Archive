---
title: "[SOLVED] Firefox won't start"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by Ziv Kohav on 2008-12-15
Just installed Ubuntu 8.10. Everything runs fine but when I click on the Firefox icon there is a box on the bottom saying "starting firefox" (or something like this) and the cursor becomes a clock, and then after about 15 seconds this box disappears and firefox doesn't start.
I tried running in terminal "sudo firefox" and it just goes to the next line without anything happening. I figured maybe some extensions hold it from starting, but I hadn't installed any yet.
Can I ask for the magic code that will fix this? 8-[
Thanks,
Ziv

---

### Post by Keen101 on 2008-12-15
I've never experienced that, but here are few old threads that might help.

[http://ubuntuforums.org/showthread.php?t=1001124](http://ubuntuforums.org/showthread.php?t=1001124)
[http://ubuntuforums.org/showthread.php?t=1003636](http://ubuntuforums.org/showthread.php?t=1003636)

sorry i can't be of much help. You could try reinstalling firefox with synaptic or apt-get.

---

### Post by linuxford on 2008-12-15
Did you try to reinstall to fix it?

---

### Post by linuxford on 2008-12-15
You may want to check out this page

[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by Sealbhach on 2008-12-15
Just unistall and reinstall. Usually fixes most issues.

Don't use "sudo" to start it in the terminal. just type "firefox".


.

---

### Post by Michael.Godawski on 2008-12-15
> Just unistall and reinstall. Usually fixes most issues.

Don't use "sudo" to start it in the terminal. just type "firefox".
Correct, 
and if you are want to start a graphical application with sudo rights use
```
gksudo
``` instead.

---

### Post by Ziv Kohav on 2008-12-16
> **Sealbhach said:**
> Just unistall and reinstall. Usually fixes most issues.

Don't use "sudo" to start it in the terminal. just type "firefox".


.

Thanks for all your suggestions. It still doesn't work. Here is what I did:
[LIST=1]
[*]Marked for reinstallation through synaptic. It did it, but when I start Firefox again the box saying "starting firefox" appears and after a few seconds it disappears and nothing happens.
[*]Uninstalled Firefox and its components through synaptic and reinstalled it through "Add/Remove Programs". Same thing.
[*]Installed Opera. This worked great for a day, but then I had all kind of (unrelated) problems with my Samsung printer/scanner and I tried some code someone put in one of the forums to fix it, and then the same thing happens with Opera! It tries to start, but then just nothing happens. Very frustrating.
[*] Uninstalled and reinstalled Opera, and still the problem persists.
[*]I didn't read yet all the links you gave me. Hopefully I'll do it tonight or tomorrow, and hopefully I'll get wiser doing this.
[*]Is there any way to put some diagnostic program or something like this that would give an output which someone can interpret?
[/LIST]

Thanks,
Ziv

---

### Post by Ender41 on 2008-12-16
> **Ziv Kohav said:**
> Thanks for all your suggestions. It still doesn't work. Here is what I did:
[LIST=1]
[*]Marked for reinstallation through synaptic. It did it, but when I start Firefox again the box saying "starting firefox" appears and after a few seconds it disappears and nothing happens.
[*]Uninstalled Firefox and its components through synaptic and reinstalled it through "Add/Remove Programs". Same thing.
[*]Installed Opera. This worked great for a day, but then I had all kind of (unrelated) problems with my Samsung printer/scanner and I tried some code someone put in one of the forums to fix it, and then the same thing happens with Opera! It tries to start, but then just nothing happens. Very frustrating.
[*] Uninstalled and reinstalled Opera, and still the problem persists.
[*]I didn't read yet all the links you gave me. Hopefully I'll do it tonight or tomorrow, and hopefully I'll get wiser doing this.
[*]Is there any way to put some diagnostic program or something like this that would give an output which someone can interpret?
[/LIST]

Thanks,
Ziv


  Open a terminal, navigate to .mozilla/firefox then ls to see what your firefox profile is called, it will be a folder/directory cd to that and rm .parentlock and lock files. cd ~/ and try again

---

### Post by discrat on 2008-12-16
I have had this similar problem with Firefox. And it continues to give me some problems. I will try some of the suggestions here and maybe it can be resolved.
Thanks

---

### Post by maddog46113 on 2008-12-16
This is going to be my second time typing this today but do the following in terminal:

Open Terminal
```

sudo apt-get remove firefox --purge

```

Then type the following:
```
 sudo apt-get install firefox
```
Then to reinstall flash:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Ziv Kohav on 2008-12-16
I'll try it. Thanks.
Ziv

---

### Post by Ziv Kohav on 2008-12-16
Unfortunately none of what you all suggested worked, and I've tried it all exactly according to the code you've given, or the instructions in the links. What I did in the end was a clean install of Ubuntu 8.10. It took some time, but now everything is working fine. Thanks for all your suggestions.

---

### Post by Ophidion on 2010-11-19
> **Ziv Kohav said:**
> Unfortunately none of what you all suggested worked, and I've tried it all exactly according to the code you've given, or the instructions in the links. What I did in the end was a clean install of Ubuntu 8.10. It took some time, but now everything is working fine. Thanks for all your suggestions.
I have the same problem. I guess it is because we installed a kind of plugin like Adobeflash or gnome-do so we can get help each other if u had any of them recently installed before the problem appeared.

---

### Post by lotharmat on 2010-11-19
Try deleting your profile for firefox and then re-opening firefox.

---

