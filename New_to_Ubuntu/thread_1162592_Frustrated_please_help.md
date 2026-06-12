---
title: "Frustrated please help"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by augie2051 on 2009-05-17
I was using a dual boot for the past six months with vista and Intrepid.  I just recently killed vista from my cpu all together thinking i didn't need anything it had to offer and if i did i could use a virtual machine.  So i sole booted Jaunty and installed virtual box and am now missing some programs that Microsoft ran with ease.  I cant seem to get the VM to recognise my zune, iphone or external HD, basically anything through USB.  I used the OSE virtual box and someone suggested that may be the problem but replaced it with the non free version from Sun's website and still can't seem to get anything to work.  These three programs and shockwave are the only things tempting me back to a dual boot with microsoft but I prefer not to and just run Ubuntu.  If someone could help me get them up and running I would be most grateful.  If you do decide to help please be gentle I am a noob.

---

### Post by hobo14 on 2009-05-17
See here for some ipod/iphone stuff... don't know if that's what you're looking for.
[http://en.wikipedia.org/wiki/Comparison_of_iPod_Managers#Linux]("http://en.wikipedia.org/wiki/Comparison_of_iPod_Managers#Linux")


See here for possible zune solution:
[http://www.zuneboards.com/forums/zune-hacks-mods/2772-zune-linux-progress-2.html]("http://www.zuneboards.com/forums/zune-hacks-mods/2772-zune-linux-progress-2.html")

I suggest you post more details on the external HD problem, and google "ubuntu shockwave" to find out what is and isn't available/possible.

---

### Post by Aaardwark on 2009-05-17
Amarok really is the best way to interact with those devices in linux. I think you can use Rhythm Box as well.

But if you really want to use a vm, I suggest [vmware]("http://www.vmware.com/download/server/"). The version I've linked to is only limited by system resources, it isn't time limited. The limit would be trouble for playing games, but for using simple tools and programs it really hardly matters.

---

### Post by Ocxic on 2009-05-17
you must select the USB devices that you virtual machine can use in the settings for that virtual machine.

---

### Post by gashcr on 2009-05-18
ok, for the guest OS to recognize your USB devices you need to:

1. plug-in the device
2. start Vbox (just that, don't start the guess OS yet)
3. select the guest OS and go to configure, USB 
4. hit the + button to the right and select the device you want to be recognized. repeat this step for every device you need.
5. start the guest OS and there should be the device.

Hope this helps, if that doesn't work, we'll be pleased to help.

---

### Post by hobo14 on 2009-05-18
> **Aaardwark said:**
> Amarok really is the best way to interact with those devices in linux. I think you can use Rhythm Box as well.

But if you really want to use a vm, I suggest [vmware]("http://www.vmware.com/download/server/"). The version I've linked to is only limited by system resources, it isn't time limited. The limit would be trouble for playing games, but for using simple tools and programs it really hardly matters.

To be honest, I don't actually know, but...  
I was under the impression that Amarok doesn't play nice with iphones?

---

### Post by augie2051 on 2009-05-18
I've tried this two suggestions and still having same problems.  Should i try vmware instead of virtualbox?

---

### Post by dark_harmonics on 2009-05-18
Does anything from this thread help you? [http://ubuntuforums.org/archive/index.php/t-512783.html](http://ubuntuforums.org/archive/index.php/t-512783.html)

There is tons of info out there on the subject, the hard part will just be sorting through it till we find you a solution.

---

### Post by tom56 on 2009-05-18
Try installing Guest Additions in Virtualbox. Boot the virtual machine, then click Devices -> Install Guest Additions.

---

### Post by Ms_Angel_D on 2009-05-18
Are you using the correct version of Virtualbox there are two versions the one in the Repositories which is open source doesn't support USB you need to get the one from their website.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by augie2051 on 2009-05-19
I am using the non "OSE" version.  I keep looking through the forums and google and dont seem to find anything that helps.  I hope someone can diagnos the problem

---

